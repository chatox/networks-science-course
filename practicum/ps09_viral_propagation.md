
Load labels from `stocks_62_names.txt` into a variable `id2name`, which should be a dictionary. Load edges from `stocks_62_pearson.net` into a variable `edges` which should be a list of 3-element lists.

Then use these to create a graph:

```python
g = nx.Graph()
for edge in edges:
    g.add_edge(edge[0], edge[1], weight=float(edge[2]))
g = nx.relabel_nodes(g, id2name)
    
print("Stocks network: |V|=%d, |E|=%d" % (g.order(), g.size()))
print("E.g., weight from %s to %s: %.3f" % ("ORCL", "AIG", g.get_edge_data("ORCL", "AIG")["weight"]))
```

Draw this graph:

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

Now simulate independent cascades. The following code shows how to walk this graph:

```python
def dump_weighted_graph(graph, weight_attr_name):
    for node in graph.nodes():
        for neighbor in graph.neighbors(node):
            weight = graph.get_edge_data(node, neighbor)[weight_attr_name]
            print("Link from %s to %s with weight %.3f" % (node, neighbor, weight))
            
#dump_weighted_graph(g, weight_attr_name='weight')
```

The algorithm should be: 

EXPLAIN

Your code should look like:

```python
def simulate_independent_cascade(graph, starting_node, weight_attr_name, weight_multiplier):
    infected = dict([(node, False) for node in graph.nodes()])
    #... (should use auxiliary function which is recursive) ...
    return infected
```


```python
infected = simulate_independent_cascade(g, starting_node='NSC', weight_attr_name='weight', weight_multiplier=0.1)
infected_count = sum([1 for is_infected in infected.values() if is_infected])
print("Infected nodes: %d" % infected_count)

pos = draw_weighted_graph(g, pos=pos, weight_attr_name='weight', node_colors=[('red' if infected[u] else 'green') for u in g.nodes()], label_color='white')
```

def perform_simulation(graph, starting_node, weight_attr_name, weight_multiplier, num_trials):
    count_infected_per_trial = []
    ....
    return count_infected_per_trial
```


```python
count_infected_per_trial = perform_simulation(g, starting_node='S', weight_attr_name='weight', weight_multiplier=0.1, num_trials=1000)
plt.hist(count_infected_per_trial, density=True)
plt.title("Infection started from node 'S'")
plt.xlabel("Number infected")
plt.ylabel("Probability")
print("Average infected: %.3f" % (sum(count_infected_per_trial)/len(count_infected_per_trial)))
```

Do a simulation from each node:

    Node: AA Average infected: 40.780
    Node: AEP Average infected: 39.220
  ...
    Node: XRX Average infected: 42.290

List nodes from the one that's most viral to least viral, draw 3 infection graphs for the top and the bottom of the list.

```python
# EXTRA POINTS: draw in red the infectious edges
```

