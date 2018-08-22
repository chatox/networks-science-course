# Practice Session 08: Communities in NetworkX

In this session we will use [NetworkX](https://networkx.github.io/) for implementing graph clustering algorithms.

# 0. Materials

You will need Zachary's Karate Club (`karate.gml`), and a file describing which student went to which group after the club splitted (`karate-factions.csv`). The latter will serve as ground truth for our community detection methods.

# 1. Load the two ground-truth communities in Zachary's Karate Club

Load the graph `karate.gml` using NetworkX.

```python
gkar = nx.read_gml(path="data/karate.gml", label="id")
print("Karate Club: |V|=%d, |E|=%d" % (gkar.order(), gkar.size()))
```

Load the file `karate-factions.csv` using a `csv.DictReader` into a dictionary `node2faction`. The output of `print(node2faction)` should be:

```python
{1: 'A', 2: 'A', ..., 22: 'A', 10: 'B', 15: 'B', ..., 34: 'B'}
```

Now, "invert" this dictionary so that it has only two keys (one for every faction name, "A" or "B") and each value is a list of nodes. The result should be a new dictionary `factions`, which should look like this when printed:

```python
{'B': [10, 15, ..., 34], 'A': [1, 2, ..., 22]}
```

**Important**: Note that the node ids must be numbers, not strings. You can convert strings to numbers using the `int()` function.

# 2. Visualize these communities

We will now visualize these two communities. For this we will use the fact that the function `networkx.spring_layout()` can return the positions of all the elements in the display of a network: nodes, edges, and labels. Then, we can use these positions to draw each element separately. This allows us to associate different colors to different nodes, in this example.

```python
pos = nx.spring_layout(gkar)

plt.figure(figsize=(12,8))
plt.axis('off')
nx.draw_networkx_edges(gkar, pos=pos)
faction2color = {'A': 'red', 'B': 'blue'}

for (faction_name, faction_members) in factions.items():
    color = faction2color[faction_name]
    nx.draw_networkx_nodes(gkar, pos=pos, nodelist=faction_members, node_color=color, node_size=640)

nx.draw_networkx_labels(gkar, pos=pos, font_color='white')
plt.show()
```

Note that each run will generate a different graph. Execute this cell a few times until you like the resulting layout.

# 3. Evaluate these communities

We will use the [modularity](https://en.wikipedia.org/wiki/Modularity_%28networks%29) measure. For this we need two quantities:

* The probability that an edge is completely inside community `i`: `prob_internal[i]`
* The probability that an edge has one end in community `i`: `prob_has_one_end_in[i]`

The modularity is expressed as the sum of `prob_internal[i] - prob_has_one_end_in[i]^2`. In Python:

```python
def compute_modularity(g, communities):
    num_internal_edges = {}
    num_edges_one_end_in = {}
    for edge in g.edges():
        (src, dest) = edge
        src_community = communities[src]
        dest_community = communities[dest]

        if src_community == dest_community:
            if src_community in num_internal_edges:
                num_internal_edges[src_community] += 1
            else:
                num_internal_edges[src_community] = 1

        if src_community in num_edges_one_end_in:
            num_edges_one_end_in[src_community] += 1
        else:
            num_edges_one_end_in[src_community] = 1

        if dest_community in num_edges_one_end_in:
            num_edges_one_end_in[dest_community] += 1
        else:
            num_edges_one_end_in[dest_community] = 1

    num_edges = len(g.edges())
    modularity = 0
    for faction_name in num_internal_edges.keys():
        modularity += num_internal_edges[faction_name]/num_edges - (num_edges_one_end_in[faction_name]/(2.0*num_edges))**2.0

    return(modularity)
```

You should obtain a value of 0.3582 for the division of the Karate Club into the communities defined in `node2faction`.

# 3. Implement betweenness-based clustering algorithm

Next we will implement a simple betwenness-based algorithm named after Girvan and Newman. Basically we remove the edge with the largest edge betweenness until the graph is disconnected.

**Note: this algorithm is already implemented in the references, although in a different way. If you copy-paste the algorithm from the reference, you will get a zero grade in this session. Instead, implement it following the steps here.**

```python
def partition_by_edge_betweenness(g):
    gcopy = g.copy()

    while nx.number_connected_components(gcopy) == 1:
        edge_to_remove = edge_with_largest_betweenness(gcopy)
        gcopy.remove_edge(edge_to_remove[0], edge_to_remove[1])

    return(gcopy)
```

Implement the function `edge_with_largest_betwenness(g)` that returns the edge with the largest betweenness. Use the function `nx.edge_betweenness_centrality()` to obtain a map of edge to betweenness centrality.

If you run your method, you should see the resulting graph has two connected components:

```python
gkar_partitioned = partition_by_edge_betweenness(gkar)
nx.draw_spring(gkar_partitioned)
```

# 4. Evaluate the betweenness-based method

Now you need to create a new variable `node2faction_alt` containing this new division of nodes into factions.

Each faction is a connected component, use `nx.connected_components` to obtain the sets of nodes in each connected component. Then, iterate through the components.

To ease your development, name the new factions using numbers: 1 and 2.

If you print `node2faction_alt` the result should look similar to this:

```python
{1: 1, 2: 1, 4: 1, ..., 30: 2, 31: 2}
```

Compute the modularity of this partition.

# 5. Visualize the removed edges

Use the following code to divide the edges into those that were removed and those that were kept:

```python
removed_edges = []
surviving_edges = []

for edge in gkar.edges():
    if edge in gkar_partitioned.edges():
        surviving_edges.append(edge)
    else:
        removed_edges.append(edge)
```

Now, draw the network again; use the same code as above but replace the line where we draw the edges by these two lines:

```python
nx.draw_networkx_edges(gkar, pos=pos, edgelist=surviving_edges)
nx.draw_networkx_edges(gkar, pos=pos, edgelist=removed_edges, style='dashed', edge_color='gray', width=3)
```

Repeat the spring layout as many times as needed until you clearly see the cut, i.e., until you can draw an imaginary straight line cutting only removed (dashed) edges.

# DELIVER (individually)

At the end of the session, deliver a zip file containing your Python notebook (remove unnecessary elements, add comments when needed). Include also a PDF file containing:

* The original Karate Club with the ground-truth factions
* The modularity obtained using the ground-truth and the Girvan-Newman algorithm, and your 1-2 lines commentary on those modularity values.
* The plot with the visualization of the removed edges
* A table with the nodes indicating what is their ground-truth component, and their component in the Girvan-Newman algorithm (you will need to manually determine whether resulting component 0 is original component A and 1 is B, or viceversa). Highlight the nodes that moved to a different component: they should be a small minority.

# Extra points

For extra points, add a section "Extra points" to your document, and process `polblogs.gml` and `polblogs-leaning.csv`. These are left (*liberal*) and right (*conservative*) leaning blogs in the US in 2004 collected in a seminal paper by Lada Adamic and Natalie Glance.

First, visualize this graph using Cytoscape, painting blue/red the two leanings.

Next, process this using NetworkX. You need to select its largest connected component. Assumming you loaded it in variable `gpol`, this is done by doing:

```python
gpol_largest = max(nx.connected_component_subgraphs(gpol), key=len)
```

Include the following in your "Extra points" section:
* Your visualization in Cytoscape of the entire graph with colors for the two leanings.
* The ground-truth modularity using the given leaning, considering only the largest connected component.
* The number of nodes in each component after applying the Girvan-Newman algorithm.

You will notice that the results might be very insatisfactory and the graph is divided into a component having almost all the nodes and a component having almost none. Why do you think this happens? Indicate this in your report.

# References

* [Barabási's Python Notebook for community detection](https://www.dropbox.com/s/8cz75z3rbsbcem3/communities.ipynb?dl=0)
* [Adamic and Glance 2005](https://doi.org/10.1145/1134271.1134277)
* [NetworkX documentation](https://networkx.github.io/)
