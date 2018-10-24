# Practice Session 07: Degree distribution and degree correlations

In this session we will process some existing networks using [NetworkX](https://networkx.github.io/), a Python package.

# 0. Preliminaries

## 0.1 Datasets

You will need the following files:

* the hero network (`hero-network.csv`),
* a network of Internet autonomous systems (`internet-as-20060622.gml`, label attribute `label`), and
* a network of collaborations between astrophysicists (`astro-ph.gml`, label attribute `label`).

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

CSV files can be parsed with the `csv` module, creating the graph programmatically. In the example below, we read a file that has a header with `Source` and `Target`.

```python
# Create an empty graph
g = nx.Graph()

with io.open(INPUT_FILE) as file:
    reader = csv.DictReader(file, delimiter='\t', quotechar='"')

    # Read lines
    for row in reader:
        hero1 = row["Source"]
        hero2 = row["Target"]
        g.add_edge(hero1, hero2)

print("|V|=%d, |E|=%d" % (g.order(), g.size()))
```

# 1. Analyze the hero network graph

## 1.1. Obtain the sub-graph of high-degree nodes

The purpose of NetworkX is not really to draw graphs, for that there is Cytoscape and other tools. Instead, its purpose is to run algorithms on graphs. It can, however, be used to visualize small graphs or sub-graphs.

Use the following code to extract the sub-graph of high-degree nodes and draw it. Choose a `THRESHOLD` value that allows you to plot around 100-200 nodes maximum.

```python
# Build a list of nodes
all_nodes = g.nodes()
high_degree_nodes = []
for node in all_nodes:
    if g.degree(node) > THRESHOLD:
        high_degree_nodes.append(node)

# Extract the sub-graph of those nodes
subgraph = g.subgraph(high_degree_nodes)
print("Extracted a subgraph of %d nodes" % len(subgraph))

# Draw the sub-graph (tip: place this code in another cell)
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

NetworkX includes a method named `degree()` for Graph objects that returns a dictionary of the degree of nodes:

```python
print("Degre dictionary:")
print(g.degree())

print("Degree sequence:")
degrees = [ x[1] for x in g.degree() ]
print(degrees)
```

To plot the degree distribution, use the following code:

```python
# Obtain a histogram; this requires two additional bins
# to the left and right (hence the +2)
prob, bin_edges = np.histogram(degrees, bins=range(1,np.max(degrees)+2), normed=True)

# Plot in log-log the degree distribution with crosses
plt.loglog(bin_edges[:-1], prob, '.', marker='x')

# Add an approximation line
plt.loglog(bin_edges[:-1], [C*x**-gamma for x in bin_edges[:-1]], '-')

# Include tile and axis labels
plt.title("Probability density function")
plt.ylabel("probability")
plt.xlabel("degree")
plt.show()
```

First set the values of *C* and *gamma* by trial and error, until you have a line that passes through the center of the right portion of the degree distribution.

To obtain a better approximation of *gamma*, use [Hill's estimator](https://en.wikipedia.org/wiki/Power_law#Maximum_likelihood). This estimator is computed as *gamma = 1 + n / sum(log(xi/xmin))*. In this equation:

* *xmin* is the minimum value from which the power-law should be expected. Obtain it by looking at the point in the degree distribution plot in which the probability starts to decrease.
* *xi* are all the values of the degree larger or equal to *xmin*.
* *n* is the number of nodes having degree larger or equal to *xmin*.

Write code to compute Hill's estimator and use this value of *gamma* in your plot.

## 1.4. Plot the degree-degree correlation plot

Now we will create a plot in which in the x axis we have the degree of nodes, and in the y axis the average degree of their neighbors. This will allow us to say if the network is assortative or disassortative.

First, create a dictionary from degrees to lists of nodes having that degree:

```python
degree_to_nodes = {}
for node in g.nodes():
    degree = g.degree(node)
    # If the degree of this node has not been seen,
    # initialize degree_to_nodes[degree] = []
    # Then, append this node to degree_to_nodes[degree]
```

Second, create arrays *x* and *y*. Array *x* should contain all degrees for which there are nodes that have at least one neighbor. Array *y* should contain the macro-average of the degree of the neighbors of those nodes.

```python
x = []
y = []
for degree in degree_to_nodes.keys():
    sum_degree_neighbors = 0
    count_neighbors = 0

    for node in degree_to_nodes[degree]:
        for neighbor in g.neighbors(node):
            # YOUR CODE HERE

    if count_neighbors > 0:            
        average_degree_neighbors = sum_degree_neighbors / count_neighbors
        # YOUR CODE HERE
```

Third, create a scatterplot and conclude from it if the network is assortative or disassortative:

```python
plt.loglog(x, y, '.')
plt.title("Degree Correlation")
plt.ylabel("degre of node")
plt.xlabel("average degree of neighbors")
plt.show()
```

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
