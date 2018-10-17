# Practice Session 06: Graph generation and degree computation

:construction: **NOTE: THIS PRACTICE IS BEING EDITED/REVIEWED**

In this session we will learn to use [NetworkX](https://networkx.github.io/), a Python package.

# 0. Imports

Imports:

```python
import networkx as nx
import matplotlib.pyplot as plt
```

# 1. Generate a small graph

:construction: To be available

Draw the graph:

```python
nx.draw_spring(g, with_labels=True)
plt.show()
```

# 2. Generate an ER graph

:construction: To be available

# 3. Generate a BA graph

:construction: To be available

# 4. Degree sequence and histogram for a small graph

Load the graph from *Zachary's Karate Club* in variable `g`:

```python
g = nx.read_gml(path="data/karate.gml", label="id")
```

We will now plot its degree sequence.

```python
# Obtain degree sequence
degree_dict = dict(g.degree())
print(degree_dict)
degree_sequence = sorted(degree_dict.values(), reverse=True)
print(degree_sequence)

plt.loglog(degree_sequence,'b-',marker='o')
plt.title("Degree rank plot")
plt.ylabel("degree")
plt.xlabel("rank")
plt.show()
```

Next, we will plot its degree histogram. For this, we will use a function in `numpy` named `histogram`. Add this to the first cell of your notebook and run it:

```python
import numpy as np
```

Now you can use the following code to create the histogram. Normally the `numpy.histogram` function uses its own bins for histograms, but we are giving our own. We are also ensuring all degrees have their own bin, remember the `range` function excludes the last element of the range, plus the bins are the upper limit of each bucket, this is why we use *+2*.

We also have to remove the last bin in the end to make both lists (bins and frequencies) the same size.

```python
freq, bin_edges = np.histogram(degree_sequence, bins=range(1, np.max(degree_sequence)+2))
print(degree_sequence)
print(freq)

print(bin_edges)
bin_edges_minus_last = bin_edges[:-1]
print(bin_edges_minus_last)

plt.bar(bin_edges_minus_last, freq)
plt.title("Degree histogram")
plt.ylabel("Number of nodes")
plt.xlabel("Degree")
plt.xticks(bin_edges_minus_last)
plt.show()
```

# 5. Degree distribution for a large graph

Now let's load a larger network: `hero-network.csv`:

```python
INPUT_FILE = "data/hero-network.csv"
g = nx.Graph()

with io.open(INPUT_FILE) as file:
    reader = csv.reader(file, delimiter='\t', quotechar='"')
    for row in reader:
        hero1 = row[0]
        hero2 = row[1]
        g.add_edge(hero1, hero2)

print("Hero network: |V|=%d, |E|=%d" % (g.order(), g.size()))
```

To obtain its degree sequence, we will use an ordered dictionary, which also allows us to see the hero that is associated to each value. Add `from collections import OrderedDict` to the first cell in your notebook, and then do:

```python
degree_dict = dict(g.degree())
degree_ordered = OrderedDict(sorted(degree_dict.items(), key=lambda x: x[1], reverse=True))
print(degree_ordered)
degree_sequence = list(degree_ordered.values())
print(degree_sequence)
```

Now, plot its degree rank plot using the code we have seen above.

To plot its degree distribution, we will use the following:

```python
prob, bin_edges = np.histogram(degree_sequence, bins=range(1,np.max(degree_sequence)+2), density=True)
plt.loglog(bin_edges[:-1], prob, '.', marker='x')
plt.title("Probability density function")
plt.xlabel("Degree")
plt.ylabel("Probability")
plt.show()
```

Observe two things in this plot. First, for smaller degrees we do not observe a power law. Second, for larger degrees the distribution is a bit *messy* because of the sparse observations. This is a fairly typical situation, so following [Adamic 2002](http://www.labs.hp.com/research/idl/papers/ranking/ranking.html), we will use the inverse cumulative distribution function (inverse CDF) instead of the probability density function (PDF).

```python
cdf_x = sorted(degree_sequence)
cdf_y = np.array(range(len(degree_sequence)))/len(degree_sequence)

plt.loglog(cdf_x, 1-cdf_y, 'b-')
plt.title("Inverse cumulative distribution function")
plt.xlabel("x")
plt.ylabel("P(degree >= x)")
plt.show()
```

Next, we will select the central portion of this plot, by discarding degrees that are too low: we want to obtain a power law for the middle part of the distribution. In this case, we will discard values smaller than 30:

```python
degree_sequence_central = [d for d in degree_sequence if d >= 30]
```

Now we will fit a line to the inverse CDF plot. To ensure we obtain a line, we will first transform the data using `log()`, and then use `numpy.polyfit` to fit a polynomial of degree 1 (i.e., a line) to the data:

```python
cdf_x = sorted(degree_sequence_central)
cdf_y = np.array(range(len(degree_sequence_central)))/len(degree_sequence_central)

x_values = np.log(cdf_x)
y_values = np.log(1-cdf_y)
linmodel = np.polyfit(x_values, y_values, deg=1)
print(linmodel)
pred_y_values = list(map(lambda x: linmodel[0]*x + linmodel[1], x_values))

plt.plot(x_values, pred_y_values, 'r-')
plt.plot(x_values, y_values, 'b-')
plt.legend(['Line with slope %.1f' % linmodel[0], 'Observed'])
plt.title("Inverse cumulative distribution function (log-transformed)")
plt.xlabel("log(x)")
plt.ylabel("log(P(degree >= x))")
plt.show()
```

Now, we can return to the original data:

```python
cdf_x = sorted(degree_sequence)
cdf_y = np.array(range(len(degree_sequence)))/len(degree_sequence)
plt.loglog(cdf_x, 1-cdf_y, 'b-')
plt.loglog(cdf_x, list(map(lambda x: x**linmodel[0] * np.exp(linmodel[1]), cdf_x)))
plt.title("Inverse cumulative distribution function")
plt.xlabel("x")density
plt.ylabel("P(degree >= x)")
plt.legend(['Cx^(%.1f)' % linmodel[0], 'Observed'])
plt.show()
```

Note that if *log(y) = a log(x) + b*, then *y = x^a e^b*, and that the displacement along the y axis of the fitted line is because the last plot includes the entire degree sequence and not just the selected values. In any case, what we care about is the slope.

# DELIVER (individually)

Deliver a zip file containing your Python notebook (remove unnecessary elements, add comments when needed), and a PDF file containing, for the ER and BA networks you have created:

* A probability density function (PDF) plot
* An inverse cumulative density function (CDF) of degree with a fitted line
* Your commentary on these

# References

* [Complex Network Analysis in Python](https://www.amazon.com/gp/product/1680502697/) (2018) by Dmitry Zinoviev. Also [available as an e-book](https://upfinder.upf.edu/iii/encore/record/C__Rb1557007?lang=cat) for UPF students.
* [Social network analysis with NetworkX](https://blog.dominodatalab.com/social-network-analysis-with-networkx/) by Manojit Nandi
* [NetworkX: Network analysis with Python](https://www.cl.cam.ac.uk/~cm542/teaching/2010/stna-pdfs/stna-lecture8.pdf) by Salvatore Scellato
* [NetworkX documentation](https://networkx.github.io/)
* [Zipf, Power-laws, and Pareto - a ranking tutorial](http://www.labs.hp.com/research/idl/papers/ranking/ranking.html) by Lada Adamic (2002)
