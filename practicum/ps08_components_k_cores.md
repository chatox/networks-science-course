# Practice Session 08: Connected components and k-core decomposition

In this session we will use [NetworkX](https://networkx.github.io/) for implementing two simple algorithms.

# 0. Materials

Imports:

```python
import io
import csv
import networkx as nx
import matplotlib.pyplot as plt
```

We will use the `email-eu-core.txt` network, which is a list of space-delimited edges.

```python
INPUT_FILE = "data/email-eu-core.txt"
h = nx.Graph()

with io.open(INPUT_FILE) as file:
    reader = csv.reader(file, delimiter=' ', quotechar='"')
    for row in reader:
        p1 = row[0]
        p2 = row[1]
        h.add_edge(p1, p2)

g = h.to_undirected()

print("E-mails: |V|=%d, |E|=%d" % (g.order(), g.size()))
```

:warning: Note we are loading the graph as an undirected graph.

You can take a quick look at this graph (it may take a minute):

```python
nx.draw_spring(g, with_labels=True)
plt.show()
```

# 1. Determining the number of (weakly) connected components

For this we are going to proceed in steps:

## 1a. Create a function to recursively assign nodes

Create a function `assign_recursive` that receives the following arguments:

1. A graph: *g*
2. A dictionary: *dict*
3. A node: *starting_node*
4. A number: *identifier*

The function should do the following:

First, assign the starting node to the identifier in the dictionary. To assign a value *v* to key *k* in dictionary *d* one does `d[k] = v`.

Second, for each neighbor, if that neighbor is not assigned, call the function `assign_recursive`. For this you need the following:

* To iterate through the neighbors of a node, you do `for neighbor in nx.all_neighbors(g, starting_node):` or `for neighbor in g.neighbors(starting_node):`. Note that *neighbor* will be a string containing the id of the node.
* To check if a string *str* is a key in the dictionary *dict*, ask `if str in dict`

## 1b. Iterate through all nodes

Now we should call the function `assign_recursive` for all the nodes in the graph that are not assigned. Here is some (**wrong**) code to do this, which you have to fix.

```python
node_to_component = {}
next_component_id = 1
for node in g.nodes():
    assign_component(g, node_to_component, node, next_component_id)
    next_component_id += 1
```

## 1c. Determine the size of the largest connected component

Now you can see the assignment that was created:

```python
print(node_to_component)
```

The next step is to determine the size of each component. For this, we will use the function `dict.values()` which returns all the values of a dictionary. For instance if the dictionary `dict = {"a":1, "b":2, "c":1}` then `dict.values()` will return `[1, 2, 1]`.

1. Create an empty dictionary `component_size` for the component sizes
2. Iterate through the values of the `node_to_component` dictionary; if a component is already in component_size, increase its value by one; if it is not, then set its value to one.

# 2. Now we will perform a k-core decomposition on the graph

# 2a. Auxiliary functions

We will use these auxiliary functions which are self explanatory. Complete the missing code in the second function. You can use `g.degree(n)` to obtain the degree of node *n* in graph *g*.

```python
def get_max_degree(graph):
    ''' Gets the maximum degree of a graph
    '''
    degree_sequence = [x[1] for x in graph.degree()]
    return(max(degree_sequence))


def nodes_with_degree_less_or_equal_than(graph, degree):
    ''' Gets a list of nodes in the graph with degree <= degree
    '''
    nodes = []
    # TO-DO: implement this function
    return nodes
```

# 2b. Main function for kcore decomposition

Complete the missing code. You can use `g.remove_node(n)` to remove node *n* from graph *g*.

```python
def kcore_decomposition(graph):
    ''' Perform a k-core decomposition of the given graph
    '''
    g = graph.copy()
    max_degree = get_max_degree(g)

    node_to_level = {}
    for level in range(1, max_degree + 1):

        while True:
            # Obtain the list of nodes with degree <= level
            nodes_in_level = nodes_with_degree_less_or_equal_than(g, level)

            # Check if this list is empty
            if len(nodes_in_level) == 0:
                # TO-DO: implement (one line)

            # If the list is not empty, assign the nodes to the
            # corresponding level and remove the node
            for node in nodes_in_level:
                # TO-DO: implement this (two lines)

    return(node_to_level)
```

To call this function, you do:

```python
node_to_kcore = kcore_decomposition(g)
```

Note that if the function is correct, `g.order()` and `len(node_to_kcore.keys())` should give the same result. You must verify this.

# 2c. Compute k-core component sizes

Then, adapt the code above in which we generated the `component_size` dictionary to generate a `kcore_size` dictionary.

You can now plot them using these commands:

```python
plt.bar(kcore_size.keys(), kcore_size.values())
plt.title("Distribution of k-core sizes")
plt.xlabel("Level")
plt.ylabel("Number of nodes")
plt.show()
```

# 2d. Save k-core levels

Save the sizes of the k-cores to disk:

```python
OUTPUT_FILE = "data/email-eu-core-kcore.csv"
with io.open(OUTPUT_FILE, "w") as file:
    writer = csv.writer(file, delimiter=",", quotechar='"')
    writer.writerow(["Node", "Level"])
    for node in node_to_kcore:
        writer.writerow([node, node_to_kcore[node]])
```

# 2e. Visualize this in Cytoscape

:bulb: In Cytoscape you can load the graph as directed or undirected, it does not matter.

To create this visualization, you must import two files (A) and (B) into the same network collection, given that the table (B) has properties that apply to the graph (A).

(A) Import the `email-eu-core.txt` graph into Cytoscape:

1. Use the import network function
2. In the advanced options, select *space* as a separator an **un-tick** *Use first line as column names*
3. *Column 1* should be source node, *Column 2* should be target node.

(B) Import the `email-eu-core-kcore.csv` file into Cytoscape:

1. Use the import table function
2. In the advanced options, select *comma* as a separator and **tick** *Use first line as column names*
3. *Node* should be the key, *Level* an attribute.

Now in the *Node Table* you should see that each node has associated a level. Use the column *Level* for fill color with a continuous mapping. Change the default colors of the mapping to something that makes sense (in general, darker for more deep levels) and is not the default.

# DELIVER (individually)

Deliver a zip file containing your Python notebook (remove unnecessary elements, add comments when needed; please deliver your code in a single .ipynb file with multiple cells), and a PDF file containing:

* A description of the connected component sizes of the email graph.
 * Is there a giant connected component, if yes, what is its size as a percentage of the total number of nodes?
 * Are there singleton components, if yes, how many?
 * Are there non-giant non-singleton components, if yes, how many?
* A bar plot of the k-core sizes per level
* A graph with colors for each k-core component, generated by Cytoscape.

# References

* [Complex Network Analysis in Python](https://www.amazon.com/gp/product/1680502697/) (2018) by Dmitry Zinoviev. Also [available as an e-book](https://upfinder.upf.edu/iii/encore/record/C__Rb1557007?lang=cat) for UPF students.
* [NetworkX documentation](https://networkx.github.io/)
