# Practice Session 01: Cytoscape Basics

## Materials for this session

:warning: Do not simply right-click on the file names below, or you will download an HTML file that will not be readable by Cytoscape. See [how to download](data/README.md) in the README of the data/ directory. 

* [Cytoscape](http://www.cytoscape.org/download.php) *version 3.6.1*
* File "[karate.gml](data/karate.gml)"
* File "[lesmiserables.gml](data/lesmiserables.gml)"
* File "[us_companies_ownership.csv](data/us_companies_ownership.csv)"

## Contents of this session

0. About Cytoscape
1. Importing a network
2. Editing nodes and edge styles
3. Creating layouts
4. Performing basic network analysis
5. Using a Cytoscape app

# 0. About Cytoscape

[Cytoscape](http://www.cytoscape.org/) is an open source software platform for visualizing complex networks and integrating these with any type of attribute data. These are two recommended tutorials on Cytoscape:

* [Cytoscape tutorial](https://github.com/cytoscape/cytoscape-tutorials/wiki)
* [Emma Towlson's slides](https://www.dropbox.com/s/37zleq3ynw6e0n6/Cytoscape_2017.pdf?dl=0)

For test datasets, see [data/](data/README.md)

# 1. Importing a network

## 1.1. Import "Zachary's Karate Club"

Let's start with a simple case: [Zachary's Karate Club](https://en.wikipedia.org/wiki/Zachary%27s_karate_club). This was a Karate Club with a sensei (#1) and a club president (#34) that split into two: some people remained with the sensei, and the others created a new club with the club president.

* File > Import > Network > File
* Select `karate.gml`
* Layout > Compound Spring Embedder
* Look at the graph and try to figure out if there is anything special about nodes 1 and 34.
* [**REPORT**] Include in your report this graph plus and a brief paragraph indicating whether nodes 1 and 34 have visually anything special.

## 1.2. Import "Les Misérables"

Open a graph shown co-occurrences of characters in Victor Hugo's "Les Misérables" (same procedure as above)

* File `lesmiserables.gml`
* Find Valjean
* Find Cosette and Marius
* [**REPORT**] Include in your report this graph. Indicate where Valjean, Cosette, and Marius are by including arrows in your report.

Note: you can also look at this [other visualization of the same data](https://bost.ocks.org/mike/miserables/).

## 1.3. Import US companies co-ownership

Open a graph representing company co-ownership in the US:

* File > Import > Network > File
* Select `us_companies_ownership.csv`
* Click OK (accept default import)
* It might take a couple of minutes to open
* Layout > Compound Spring Embedder (might take ~10 minutes in some PCs)
* [**REPORT**] Include in your report this graph.

Note: you can zoom in and zoom out with the scroll wheel

# 2. How to edit node and edge styles

Go to the "Style" panel (top-left, between "Network" and "Select")

## 2.1. How to change the style of the entire network

To style the entire networks in different ways:

* Play with predefined styles, e.g. "Metallic" or others

## 2.2. How to name nodes

To include in each node its name:

* Create a "Passthrough mapping" for "name" in the label property

To remove these names:

* Remove the mapping (trash can icon)

## 2.3. How to change the shape of node

To change the shape of nodes:

* Click on the rectangle left of "Shape" and choose another shape

## 2.4. How to change edge width

To change the width of edges:

* Click on "Edge" on bottom left (between "Node" and "Network")
* Mapping Type = Continuous Mapping
* Column = Value (this will work in *Les Misérables* which has a value column)
* Change the "Current Mapping" by double clicking. You should see a window "Continuous Mapping Editor ..."
* Create a mapping that gives a clear visual separation between thin and thick edges, by editing the mapping so that it has a broader range of values

## 2.5. How to add arrows

To add arrows, you need a directed graph such as the company ownership dataset.

* Change the setting of "Target Arrow Shape".

## 2.6. How to change the entire layout

Try some layouts ("Layout" menu)

* Degree Sorted Circle Layout > All nodes
* Edge Weighted Spring Embedded Layout
 * Try this with the Karate Club, look for nodes 1 and 34.
* Prefuse Force Directed Layout

# 3. Basic network analysis

## 3.1. Analyze network

Perform basic network analysis. Tools > Network Analyzer > Network Analysis > Analyze network ; then choose "undirected"

* Start with the Karate Club network
* The analysis adds some node attributes
* Look at these node attributes (e.g., find the node with the largest betweenness centrality)
* [**REPORT**] Indicate the number of the node with largest betweenness centrality in the Karate Club
* Try the same with Les Misèrables
* [**REPORT**] Indicate the name of the node with largest betweenness centrality in Les Misèrables

## 3.2. Plot different distributions

Look at the results from the network analysis (you will need to go to "View > Show results panel" -- if it does not show up, try hiding and showing the results panel)

* [**REPORT**] Include two plots with degree distributions in Karate Club and Les Misèrables
* [**REPORT**] Include two plots with the distribution of shortest path lengths in Karate Club and Les Misèrables

## 3.3. Style the network using analysis results

Use these to style the network

* Use continuous mapping for "size" and "fill color". Note that size can only be changed if height and width are locked as properties.
* Use "degree" for size
* Use "betweenness centrality" for color
 * Try creating a mapping where small=blue, large=red (continuous mapping)
* Tip: delete the mapping with the trash bin to start over

Include in your report:

* [**REPORT**] Include an image of the network from Les Misérables, styled in any way you want.
* [**REPORT**] Include an image of the network from US Companies, styled in any way you want.

# 4. Use a Cytoscape App (ModuLand 2.0)

Cytoscape has "apps" that can be installed and used.

## 4.1. Install ModuLand

Install ModuLand 2.0 (Apps > App Manager or in the "apps" option in the menu bar).

## 4.2. Use ModuLand

Use ModuLand 2.0 (Apps > ModuLand 2.0 > Run ...) on Les Misèrables

* Select any temporary folder if prompted
* ModuLand requires an attribute for the weight: use the "value" attribute (in *Les Misérables*)
* Once you run it, a new network will be created AND the old network will have a new attribute in the nodes
* Use the new attribute in the nodes for "Fill color" using a "Discrete mapping" on "Module color." You might have to pick the color for each group

## 6.3. Apply to Karate Club

Use ModuLand 2.0 on the Karate Club

* Here you MUST run the network analyzer first so you can have "Edge betweenness" as an attribute in edges
* Use "Edge betweenness" as the attribute for the weight
* Run the module, you should get two groups, led by #1 and #34 . Are they close to the [real partition displayed here](http://historicaldataninjas.com/karate-club-network/)?

[**REPORT**] Include in your report an image of the Karate Club network with nodes painted according to clusters.

# DELIVER (INDIVIDUALLY)

Deliver a report in PDF containing everything marked [**REPORT**] above. Maximum 4 pages.

Remember to use File > Export as image, and then insert the images in your document.


