# Practice Session 07: Empirical degree distributions

:construction: THIS IS UNDER CONSTRUCTION

In this session we will process some existing networks using [NetworkX](https://networkx.github.io/), a Python package.

# 0. Reading and drawing in NetworkX

TO-DO:

* Add instructions to read hero-network.csv
* Study 3 networks: hero, internet, astro
* For each network, extract degree distribution, fit manually and using Hill, plot degree-degree correlation, conclude something

Imports:

```python
import networkx as nx
import matplotlib.pyplot as plt
```

For reading a GML file, you use the `read_gml` method and indicate what is the name of the attribute that you want to use as a label for the nodes.

```python
gkar = nx.read_gml(path="data/karate.gml", label="id")
print("Karate Club: |V|=%d, |E|=%d" % (gkar.order(), gkar.size()))
nx.draw_spring(gkar, with_labels=True)
plt.show()

gmis = nx.read_gml(path="data/lesmiserables.gml", label="label")
print("Les Misèrables: |V|=%d, |E|=%d" % (gmis.order(), gmis.size()))
nx.draw_spring(gmis, with_labels=True)
plt.show()
```

The number of nodes in a graph can be obtained with `g.order()` and the number of edges with `g.size()`.

Simple CSV files of the form `source,target` can also be loaded using the `read_edgelist` function:

```python
g = nx.read_edgelist(path="data/holidays-bcn-network.csv", delimiter=",")
```

More complex CSV files are better parsed with the `csv` module; a graph can then be created programmatically.

```python
import io
import csv
import re

import networkx as nx
import matplotlib.pyplot as plt

DISORDER_FILE="data/disease-genes.csv"
DISORDER_CLASS="Respiratory"

# Create an empty graph
g = nx.Graph()

with io.open(DISORDER_FILE) as file:
    reader = csv.DictReader(file, delimiter=',', quotechar='"')
    for row in reader:
        disorder_class = row["Class"]

        # Select a specific class of disorder
        if disorder_class == DISORDER_CLASS:

            # Parse name and gene list
            disorder_name = row["Name"]
            disorder_genes = list(map(str.strip, row["Genes"].split(",")))
            for gene in disorder_genes:

                # Shorten the disorder name
                disorder_name = re.sub(",.*$", "", disorder_name)

                # Add the edge to the graph and report to screen
                g.add_edge(disorder_name, gene)
                print("%s - %s" % (disorder_name, gene))

print("Respiratory diseases/genes: |V|=%d, |E|=%d" % (g.order(), g.size()))
# Draw the graph
nx.draw_spring(g, with_labels=True)
plt.show()
```

The purpose of NetworkX is not really to draw graphs, for that there is Cytoscape and other tools. Instead, its purpose is to run algorithms on graphs.

# 1. Compute centrality

You can calculate various centrality metrics using NetworkX:

```python
# This should take a couple of minutes
eig_cen = nx.eigenvector_centrality(g)
# k is the number of pivots; larger k means more precision
bet_cen = nx.betweenness_centrality(g, k=50)
```

# 2. ACTIVITY TBA

:construction: To be available

# DELIVER (individually)

Deliver a zip file containing your Python notebook (remove unnecessary elements, add comments when needed), and a PDF file containing, for a network (:construction: **WHICH NETWORK**):

* The 3 nodes with the larger degree.
* The 3 nodes with the larger betweenness centrality.
* The 3 nodes with the larger eigenvector centrality (PageRank).
* ... :construction:

## Extra points available

For extra points, add a section "Extra points" to your document, and include a scatter plot containing the top nodes by degree (say, top 100). In the x axis place the degree of the node, and in the y axis the betweenness centrality of the node.

Indicate the names of the node that deviates significantly from the diagonal, i.e., has a much larger betweenness centrality considering its degree. Which kind of node may have this characteristic in this specific graph, in which an edge connect two characters that appear together in a comic?

To plot the names in a scatterplot, you can use this code. You just need to fill in the arrays x_values, y_values, and labels.

```python
plt.loglog(x_values, y_values, '.')
plt.xlabel("Degree")
plt.ylabel("Betweenness Centrality")
for i in range(len(x_values)):
    plt.text(x_values[i], y_values[i], labels[i])
plt.show()
```

# References

* [Complex Network Analysis in Python](https://www.amazon.com/gp/product/1680502697/) (2018) by Dmitry Zinoviev. Also [available as an e-book](https://upfinder.upf.edu/iii/encore/record/C__Rb1557007?lang=cat) for UPF students.
* [Social network analysis with NetworkX](https://blog.dominodatalab.com/social-network-analysis-with-networkx/) by Manojit Nandi
* [NetworkX: Network analysis with Python](https://www.cl.cam.ac.uk/~cm542/teaching/2010/stna-pdfs/stna-lecture8.pdf) by Salvatore Scellato
* [NetworkX documentation](https://networkx.github.io/)
* [Zipf, Power-laws, and Pareto - a ranking tutorial](http://www.labs.hp.com/research/idl/papers/ranking/ranking.html) by Lada Adamic (2002)
