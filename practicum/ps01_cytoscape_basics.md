# Practice Session 01: Cytoscape Basics

## Materials for this session

(See [how to download](data/README.md) in the README of the data/ directory)

* [Cytoscape](http://www.cytoscape.org/download.php) *version 3.6.1*
* File "[karate.gml](data/karate.gml)" 
* File "[lesmiserables.gml](data/lesmiserables.gml)" 
* File "[us_companies_ownership.csv](data/us_companies_ownership.csv)"

## Contents of this session

1. About Cytoscape
1. Importing a network
1. Editing nodes and edge styles
1. Creating layouts
1. Performing basic network analysis
1. Using a Cytoscape app

## 1. About Cytoscape

[Cytoscape](http://www.cytoscape.org/) is an open source software platform for visualizing complex networks and integrating these with any type of attribute data. These are two recommended tutorials on Cytoscape:

* [Cytoscape tutorial](https://github.com/cytoscape/cytoscape-tutorials/wiki)
* [Emma Towlson's slides](https://www.dropbox.com/s/37zleq3ynw6e0n6/Cytoscape_2017.pdf?dl=0)

For test datasets, see [data/](data/README.md)

# 2. Importing a network

## 2.1. Import "Zachary's Karate Club"

Let's start with a simple case: [Zachary's Karate Club](https://en.wikipedia.org/wiki/Zachary%27s_karate_club). This was a Karate Club with a sensei (#1) and a club president (#34) that split into two: some people remained with the sensei, and the others created a new club with the club president.

* File > Import > Network > File
* Select `karate.gml`
* Layout > Compound Spring Embedder
* Look at the graph and try to figure out if there's anything special about nodes 1 and 34.

## 2.2. Import "Les Misérables"

Open a graph shown co-occurrences of characters in Victor Hugo's "Les Misérables" (same procedure as above)

* File `lesmiserables.gml`
* Find Valjean
* Find Cosette and Marius
* Look at this [other visualization of the same data](https://bost.ocks.org/mike/miserables/)

## 2.3. Import US companies co-ownership

Open a graph representing company co-ownership in the US:

* File > Import > Network > File
* Select `us_companies_ownership.csv`
* Click OK (accept default import)
* It might take a couple of minutes to open
* Layout > Compound Spring Embedder (might take ~10 minutes in some PCs)
* Zoom in, Zoom out with the scroll wheel

# 3. Editing node and edge styles

Go to the "Style" panel (top-left, between "Network" and "Select")

## 3.1. Predefined styles

* Play with predefined styles, e.g. "Metallic" or others

## 3.2. Name nodes

* Create a "Passthrough mapping" for "name" in the label property
* Remove the mapping (trash can icon)

## 3.3. Change shape of node

* Here we don't need a mapping. Just click on the rectangle left of "Shape" and choose another shape

## 3.4. Change edge width

* Click on "Edge" on bottom left (between "Node" and "Network")
* Mapping Type = Continuous Mapping
* Column = Value
* Change the "Current Mapping" by double clicking. You should see a window "Continuous Mapping Editor ..."
* Create a mapping that gives a clear visual separation between thin and thick edges, by editing the mapping so that it has a broader range of values

## 3.5. Add arrows (company ownership dataset)

Look for "Target Arrow Shape".

# 4. Create Layouts

Try some layouts ("Layout" menu)

* Degree Sorted Circle Layout > All nodes
* Edge Weighted Spring Embedded Layout
 * Try this with the Karate Club, look for nodes 1 and 34.
* Prefuse Force Directed Layout

# 5. Basic network analysis

## 5.1. Analyze network

Perform basic network analysis. Tools > Network Analyzer > Network Analysis > Analyze network ; then choose "undirected"

* Start with the Karate Club network
* The analysis adds some node attributes
* Look at these node attributes (e.g., find the node with the largest betweenness centrality)
* Try the same with Les Misèrables

## 5.2. Look at analysis results

Look at the results from the network analysis (you will need to go to "View > Show results panel" -- if it does not show up, try hiding and showing the results panel)

* Look at distributes of node degrees between Karate Club and Les Misèrables
* Look at distributions of shortest path lengths between Karate Club and Les Misèrables

## 5.3. Style the network using analysis results

Use these to style the network

* Use continuous mapping for "size" and "fill color". Note that size can only be changed if height and width are locked as properties.
* Use "degree" for size
* Use "betweenness centrality" for color
 * Try creating a mapping where small=blue, large=red (continuous mapping)
* Tip: delete the mapping with the trash bin to start over

# 6. Use a Cytoscape App (ModuLand 2.0)

Cytoscape has "apps" that can be installed and used.

## 6.1. Install ModuLand

Install ModuLand 2.0 (Tools > App Manager or in the "apps" option in the menu bar).

## 6.2. Use ModuLand

Use ModuLand 2.0 (Tools > ModuLand 2.0 > Run ...) on Les Misèrables

* Select any temporary folder if prompted
* Use the "value" attribute (ModuLand requires an attribute for the weight)
* Once you run it, a new network will be created AND the old network will have a new attribute in the nodes
* Use the new attribute in the nodes for "Fill color" using a "Discrete mapping" on "Module color." You might have to pick the color for each group

## 6.3. Apply to Karate Club

Use ModuLand 2.0 on the Karate Club

* Here you MUST run the network analyzer first so you can have "Edge betweenness" as an attribute in edges
* Use "Edge betweenness" as the attribute
* Run the module, you should get two groups, led by #1 and #34 . Are they close to the [real partition displayed here](http://historicaldataninjas.com/karate-club-network/)?

# DELIVER (INDIVIDUALLY)

At the end of the session, deliver a report in PDF containing three images:

* an image of the network from Les Misérables, styled in any way you want,
* an image of the network from US Companies, styled in any way you want, and
* an image of the Karate Club network with nodes painted according to clusters.

Use File > Export as image, and then insert the images in your document.
