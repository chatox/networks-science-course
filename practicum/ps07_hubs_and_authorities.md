# Practice Session 07: Hubs and authorities

In this session we will compute Hubs and Authorities using [NetworkX](https://networkx.github.io/), a Python package. This analysis is inspired by a paper on international trade ([Deguchi et al. 2014](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0100338)).

# 0. Preliminaries

## 0.1 Dataset

You will need the file `country-exports-2018.csv` from the datasets of this course.
The file contains exports between all OECD countries from 1 January 2018 to 1 January 2019, and figures are expressed in millions of dollars.

## 0.2 Imports

```python
import io
import csv
import networkx as nx
import matplotlib.pyplot as plt
import numpy as np
```

## 0.3 Reading the exports data

The exports data is a tab-separated file of the following form:

```
         [Tab] CountryA    [Tab] CountryB ...
CountryA [Tab] (empty)     [Tab] Exports A-B ...
CountryB [Tab] Exports B-A [Tab] (empty) ...
...
```


To read this file, you can use the following code:

```python
with io.open(INPUT_FILE) as file:
    reader = csv.DictReader(file, delimiter='\t', quotechar='"')

    # Read lines
    for row in reader:
        exporter = None
        for key, value in row.items():
            if key == '' and exporter == None:
                importer = None
                exporter = value
            else:
                importer = key
                amount = float(value) if len(value) > 0 else 0

            if exporter and importer and amount > 0:
                print("%s -> %s (%f)" % (exporter, importer, amount))
```

# 1. Read the file

Create an empty graph using

```python
g = nx.DiGraph()
```

Then read the file and add weighted edges to `g`. To add a weighted edge from node *u* to node *v* with weight *w*, use `g.add_edge(u, v, weight=w)`.

# 2. Draw this graph

The following code can draw this graph.

```python
plt.figure(figsize=(20,10))

pos = nx.spring_layout(g, iterations=50)
nx.draw_networkx_nodes(g, pos)
nx.draw_networkx_labels(g, pos)

edgewidth = []
for u, v, d in g.edges(data=True):
    weight = d['weight']
    edgewidth.append(1)

_ = nx.draw_networkx_edges(g, pos, width=edgewidth,)
```

In this code, all edges have width 1.

Modify this code so that edges of different weights have different widths. An acceptable range of widths is 0.05 to 4.

[**REPORT**] Include a drawing of this graph in your report.

# 3. Compute total imports and total exports

Compute total imports and total exports per country. Store total imports in a dictionary indexed by country name `total_imports` and total exports in `total_exports`.

Then print these dictionaries, it should look like this:

```
Total imports:
{'Australia': 107994.09350800002, 'Austria': 163062.14995200007, ... 'United States': 1483708.502665}

Total exports:
{'Australia': 91793.28902100003, 'Austria': 157292.941279, ... 'United States': 1109455.3172300002}
```

[**REPORT**] Include a well-formatted table of top-10 importers and top-10 exporters in your report.

Tip: here is some suggested code for sorting a dictionary by descending values and then printing per-line, formatting the numbers without decimals but with thousand separators.

```python
sorted_exports = sorted( [(exports, country) for (country, exports) in total_exports.items()], reverse=True)[:10]
for value, country in sorted_exports:
    print("%s %s" % (format(int(value), ',d'), country))
```

# 4. Compute hubs and authorities

Implement the iterative algorithm seen in class for hubs and authorities. Instead of vectors, we will use two dictionaries having country names as keys. Dictionary `h` should contain the hub scores, while dictionary `a` should contain the authority scores.

Start from normalized hub scores: the hub score should be *1/N* for each country, where *N* is the number of countries.

Then, perform 50 iterations of the following:

1. Compute authority scores from hub scores, remember to divide the exports in each edge by the total exports of the originating (hub) country.
1. Normalize the authority scores.
1. Compute hub scores from authority scores, remember to divide the exports in each edge by the total imports of the destination (authority) country.
1. Normalize the hub scores.

[**REPORT**] Include in your report the top-10 countries by hub score and the top-10 countries by authority score.

Tip: here is some suggested code for sorting a dictionary by descending values and then printing per-line, formatting the numbers with 4 decimals.

```python
sorted_h = sorted( [(value, country) for (country, value) in h.items()], reverse=True)[:10]
for value, country in sorted_h:
    print("%.4f %s" % (value, country))
```

# 5. Compare values

Here is some basic code for plotting hubs and authority scores in a scatter plot in log scale:

```python
plt.figure(figsize=(20,10))
plt.loglog()
plt.scatter([h[country] for country in g.nodes()], [a[country] for country in g.nodes()])
for country in g.nodes():
    plt.text(h[country], a[country], country)
```

[**REPORT**] Include two plots in your report: one with hubs vs authority scores, the other one with exports vs imports. You need to include the following in each plot:

1. A label for the x axis
1. A label for the y axis
1. A title for the plot
1. A diagonal line using `plt.plot([x1,y1], [x2,y2])`

Tip: the maximum value in a dictionary can be obtained with `np.max(list(dict.values()))`.

[**REPORT**] Include a one-paragraph commentary on your observations regarding the comparison of hubs/authorities vs exports/imports. Compare also the top-10 countries in each case. Provide a possible explanation for the differences.

# DELIVER (individually)

Deliver a zip file including your report and code.

The report should be in PDF and can have up to 2 pages, containing each of the elements marked [**REPORT**] above. For each of those elements:

* Include the section number where each element is requested.
* Include a descriptive title, remembering to indicate from which network each element comes.
* For images and plots, include a brief commentary.

The code should be your `.ipynb` file:

* Remove all unnecessary elements
* Add comments when needed
* Use a single file with multiple cells.

# References

* Deguchi T, Takahashi K, Takayasu H, Takayasu M (2014) [Hubs and Authorities in the World Trade Network Using a Weighted HITS Algorithm](https://doi.org/10.1371/journal.pone.0100338). PLoS ONE 9(7): e100338.
* [NetworkX documentation](https://networkx.github.io/).
