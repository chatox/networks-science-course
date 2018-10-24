# Practice Session 07: Empirical degree distributions

:construction: THIS IS UNDER CONSTRUCTION

In this session we will process some existing networks using [NetworkX](https://networkx.github.io/), a Python package.

# 0. Preliminaries

## 0.1 Datasets

You will need the hero network (`hero-network.csv`), a network of Internet autonomous systems (`internet-as-20060622.gml`, label attribute `label`), and a network of collaborations between astrophysicists (`astro-ph.gml`, label attribute `label`).

## 0.2 Imports

```python
import networkx as nx
import matplotlib.pyplot as plt
import io
import csv
import numpy as np
```

## 0.3 Reading a GML file

For reading a GML file, you use the `read_gml` method and indicate what is the name of the attribute that you want to use as a label for the nodes.

```python
g = nx.read_gml(path=INPUT_FILE, label=LABEL_NAME)
print("|V|=%d, |E|=%d" % (g.order(), g.size()))
```

The number of nodes in a graph is obtained with `g.order()` and the number of edges with `g.size()`.

## 0.4 Reading a CSV file

CSV files can be parsed with the `csv` module, creating the graph programmatically.

```python
# Create an empty graph
g = nx.Graph()

# Open and read a CSV file
with io.open(INPUT_FILE) as file:
    reader = csv.reader(file, delimiter='\t', quotechar='"')

    # Skip header
    header = next(reader)
    assert(header[0] == 'Source')
    assert(header[1] == 'Target')

    # Read lines
    for row in reader:
        hero1 = row[0]
        hero2 = row[1]
        g.add_edge(hero1, hero2)
```

# 1. Analyze the hero network graph

## 1.1. Obtain the sub-graph of high-degree nodes

The purpose of NetworkX is not really to draw graphs, for that there is Cytoscape and other tools. Instead, its purpose is to run algorithms on graphs. It can, however, be used to visualize small graphs or sub-graphs.

Use the following code to extract the sub-graph of high-degree nodes and plot it. Choose a `THRESHOLD` value that allows you to plot around 100-200 nodes maximum.

```python
all_nodes = g.nodes()
high_degree_nodes = [node for node in all_nodes if g.degree(node) > THRESHOLD]
subgraph = g.subgraph(high_degree_nodes)
print("Extracted a subgraph of %d nodes" % len(subgraph))

plt.figure(figsize=(10,10))
plt.axis('off')
pos = nx.spring_layout(subgraph)
nx.draw_networkx(subgraph, pos, with_labels=True, node_size=10, edge_color='gray', linewidths=0.1)
```

## 1.2. Obtain the ego network of a node

Next, obtain the ego-network of a node *u*, which is a sub-graph containing the node *u*, all its neighbors, and all the links between the *u* and its neighbors and between the neighbors themselves.

To do this, do the following. Start with a list of nodes containing only the *ego* node (in this case, one character in the hero network):

```python
ego = 'SCARLET WITCH/WANDA'
ego_neighbors = [ego]
```

Now, iterate through all the neighbors of the *ego* node using `for neighbor in g.neighbors(ego)` and append them to *ego_neighbors* if their degree is larger than 1000.

Then, obtain the sub-graph of those nodes using `g.subgraph()` as above and draw this sub-graph.

## 1.3. Plot degree distribution and estimate slope

:construction:

## 1.4. Plot the degree-degree correlation plot

:construction:

# 2. Analyze the Internet graph

Perform the following operations with the Internet graph:

1. Extract the degree distribution
1. Fit a power-law distribution using Hill's estimator
1. Draw the degree-degree correlation plot

# 3. Analyze the astrophysicists collaboration graph

Perform the same operations as with the Internet graph with the astrophysicists collaboration graph.

# DELIVER (individually)

Deliver a zip file containing your Python notebook (remove unnecessary elements, add comments when needed), and a PDF file containing:

* For the hero network:
  * A drawing of the two subgraphs you extracted
  * The degree distribution graph with a fitted line
  * The exponent gamma
  * The degree-degree correlation plot
  * A brief comment on your interpretation of these
* For the Internet network:
  * The degree distribution graph with a fitted line
  * The exponent gamma
  * The degree-degree correlation plot
  * A brief comment on your interpretation of these
* For the astrophysicists collaborations:
  * The degree distribution graph with a fitted line
  * The exponent gamma
  * The degree-degree correlation plot
  * A brief comment on your interpretation of these

# References

* [Complex Network Analysis in Python](https://www.amazon.com/gp/product/1680502697/) (2018) by Dmitry Zinoviev. Also [available as an e-book](https://upfinder.upf.edu/iii/encore/record/C__Rb1557007?lang=cat) for UPF students.
* [Zipf, Power-laws, and Pareto - a ranking tutorial](http://www.labs.hp.com/research/idl/papers/ranking/ranking.html) by Lada Adamic (2002)
* [NetworkX documentation](https://networkx.github.io/)
