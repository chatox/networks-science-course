# Practice Session 09: Viral Propagation

In this session we will use [NetworkX](https://networkx.github.io/) for simulating propagations through a network.

We will simulate a toy version of a "market crash" caused by the collapse of the stock price of a company. Given that stock prices are interdependent, we will assume that if one company's stock value collapses, then there is a chance that the stock value of other companies may also collapse. The higher the interdependence between two companies, the higher the chances of this happening.

# 0. Materials

We will use a network that describes correlations between the stock prices of 62 public companies in the US. The nodes are in the file `stocks_62_names.txt`, and the correlations in `stocks_62_pearson.net`.

You will need Zachary's Karate Club (`karate.gml`), and a file describing which student went to which group after the club splitted (`karate-factions.csv`). The latter will serve as ground truth for our community detection methods.

# 1. Load node labels and edges

Load the names of the companies from the file `stocks_62_names.txt` using a CSV reader. You can examine the file with a text editor to see its file format. Then, load it into a variable `id2name`, which should be a dictionary:

```python
{'0': 'AA', '1': 'AEP', '2':, ..., '61': 'XRX'}
```

Load the edges from `stocks_62_pearson.net` into a variable `edges`. This variable should be a list of lists. Each sub-list should contain exactly three elements: the id of one stock, the id of another stock, and the Pearson correlation between the prices of these stocks, which we will interpret as their interdependence. The variable `edges` should look like this:

```python
[['0', '1', '0.211...'], ['0', '2', '0.306...'], ..., ['60', '61', '0.331...']]
```

# 2. Create and visualize this graph

Use the variables `id2name` and `edges` to create a graph using the following code:

```python
g = nx.Graph()
for edge in edges:
    g.add_edge(edge[0], edge[1], weight=float(edge[2]))
g = nx.relabel_nodes(g, id2name)

print("Stocks network: |V|=%d, |E|=%d" % (g.order(), g.size()))
print("E.g., weight from %s to %s: %.3f" % ("ORCL", "AIG", g.get_edge_data("ORCL", "AIG")["weight"]))
```

This should print:

```
Stocks network: |V|=62, |E|=1891
E.g., weight from ORCL to AIG: 0.428
```

Visualize the graph in NetworkX using the function `draw_weighted_graph` below. It takes as input the graph, the name of the edge attribute containing the weight (in our case, `weight`), a list of node colors, and the color to be used for the labels. Optionally, this function also takes a pre-computed `pos` variable containing the position of the nodes; otherwise it computes the node positions using a spring layout.

```python
def draw_weighted_graph(graph, weight_attr_name, node_colors, label_color, pos=False):
    node_shape = 's' # Square (see https://matplotlib.org/api/markers_api.html)
    if not pos:
        pos = nx.spring_layout(graph, weight=weight_attr_name)
    plt.figure(figsize=(12,12))
    plt.axis('off')
    nx.draw_networkx_nodes(graph, pos=pos, node_shape='s', node_size=1000, node_color=node_colors)
    nx.draw_networkx_labels(graph, pos=pos, font_color=label_color)
    nx.draw_networkx_edges(graph, pos=pos, width=[graph[u][v][weight_attr_name] for u,v in graph.edges()])
    plt.show()
    return(pos)

pos = draw_weighted_graph(g, weight_attr_name='weight', node_colors=['green' for u in g.nodes()], label_color='white')
```

The following code shows how to iterate through nodes and neighboring edges:

```python
def dump_weighted_graph(graph, weight_attr_name):
    for node in graph.nodes():
        for neighbor in graph.neighbors(node):
            weight = graph.get_edge_data(node, neighbor)[weight_attr_name]
            print("Link from %s to %s with weight %.3f" % (node, neighbor, weight))

dump_weighted_graph(g, weight_attr_name='weight')
```

# 3. Simulate one propagation using the independent cascade model

This is the main part of this session. Write code to simulate independent cascades. Your algorithm should do the following:

1. Initialize an `infected` dictionary with every node having value `False`
1. Mark a starting node *u* as infected with value `True`
1. For each neighbor *v* of this node:
  * If the neighbor *v* is not infected:
    * Generate a random r number in [0, 1]
    * If r is smaller than the probability of transmission of edge *(u,v)*:
      * Infect node *v*
1. Return the `infected` dictionary

Your code should look like this:

```python
def simulate_independent_cascade(graph, starting_node, weight_attr_name, weight_multiplier):
    infected = dict([(node, False) for node in graph.nodes()])
    # YOUR CODE HERE
    return infected
```

The *weight_multiplier* is a way of interpreting the weights as probabilities. For instance, if an edge weight is 0.8 and the weight multiplier is 0.5, the transmission probability for this edge will be 0.4.

**Tip**: Use an auxiliary function which should be recursive: `simulate_independent_cascade_aux(graph, node, infected, weight_attr_name, weight_multiplier)`.

To use your code, you provide the starting node for the infection. In this case, we start from node `NSC`:

```python
infected = simulate_independent_cascade(g, starting_node='NSC', weight_attr_name='weight', weight_multiplier=0.1)
infected_count = sum([1 for is_infected in infected.values() if is_infected])
print("Infected nodes: %d" % infected_count)
```

To visualize the result of the infection, use this code:

```python
pos = draw_weighted_graph(g, pos=pos, weight_attr_name='weight', node_colors=[('red' if infected[u] else 'green') for u in g.nodes()], label_color='white')
```

Note that we are passing the `pos` variable that was generated above, so that the visualization always has the nodes in the same position, which allows us to compare better between different runs of the algorithm.

# 4. Compute the average size of the infection starting from a node

Complete the following code to perform a series of trials (`num_trials`) and return a list of the number of nodes that were infected in each trial:

```python
def perform_simulation(graph, starting_node, weight_attr_name, weight_multiplier, num_trials):
    count_infected_per_trial = []
    # YOUR CODE HERE
    return count_infected_per_trial
```

Now, use this function to perform a simulation with 1,000 (or better, 10,000) trials:

```python
count_infected_per_trial = perform_simulation(g, starting_node='S', weight_attr_name='weight', weight_multiplier=0.1, num_trials=1000)
plt.hist(count_infected_per_trial, density=True)
plt.title("Infection started from node 'S'")
plt.xlabel("Number infected")
plt.ylabel("Probability")
print("Average infected: %.3f" % (sum(count_infected_per_trial)/len(count_infected_per_trial)))
```

Perform the simulation from each of the nodes. The output of this should look like this:

```
Node: AA Average infected: 40.780
Node: AEP Average infected: 39.220
...
Node: XRX Average infected: 42.290
```


# DELIVER (individually)

Deliver a zip file containing your Python notebook (remove unnecessary elements, add comments when needed). Include also a PDF file containing:

* A table with the nodes sorted from the most viral (largest average cascade size) to the least viral (smallest average cascade size), including the name of the stock and its average cascade size.
* 3 infection graphs (showing in red the companies that "collapsed" and in green the companies that "survived") for the most viral starting point, and 3 infection graph for the least viral.

# Extra points

For extra points, modify the code so that the edges that effectively transmitted the infection are drawn in red. You will need to keep track of these edges and return them along with the `infected` dictionary in the `simulate_independent_cascade` function. You will also need to modify the function that draws the graph to receive the list of active edges.

If you go for the extra points, add a section "Extra points" to your report and include one infection graph starting from the most viral stock and one infection graph starting from the least viral.

# References

* [NetworkX documentation](https://networkx.github.io/)
