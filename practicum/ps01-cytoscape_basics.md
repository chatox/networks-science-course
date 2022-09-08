# Practice Session 01: Cytoscape Basics

## Materials for this session

:warning: Do not simply right-click on the file names below, or you will download an HTML file that will not be readable by Cytoscape. See [how to download](data/README.md) in the README of the data/ directory.

* File "[karate.gml](data/karate.gml)"
* File "[starwars.graphml](data/starwars.graphml)"
* File "[us_companies_ownership.csv](data/us_companies_ownership.csv)"

## Contents of this session

0. About Cytoscape
1. Importing a network
2. Editing nodes and edge styles
3. Performing basic network analysis
4. Using a Cytoscape app

# 0. About Cytoscape

[Cytoscape](http://www.cytoscape.org/) is an open source software platform for visualizing complex networks and integrating these with any type of attribute data.

# 1. Importing a network

## 1.1. Import Zachary's karate club

Let's start with a simple case: [Zachary's Karate Club](https://en.wikipedia.org/wiki/Zachary%27s_karate_club), which captures 34 members of a karate club at a university, with links representing interactions between members outside the club.

* `File > Import > Network from File ...`
* Select `karate.gml`
* `Layout > Compound Spring Embedder`
* Determine which are the two nodes with the largest degree.
   * *Tip: use `Tools > Analyze network` and look at the `Node table` displayed under the graph*
* [**REPORT**] Include in your report this graph plus and a brief paragraph indicating what are the top two highest degree nodes.
* [**REPORT**] The Compound Spring Embedder is an algorithm derived from force-directed graph layour algorithms. Read the Wikipedia page on [force-directed graph drawing](https://en.wikipedia.org/wiki/Force-directed_graph_drawing) and explain in one paragraph, in your own words, how this works.

**Do not use screenshots**; use `File > Export as image`

## 1.2. Import the Star Wars characters network

Open a graph showing characters that appear or are mentioned in the same scene of a Star Wars movie.

* `File > Import > Network from File ...`
* Select `starwars.graphml`
* If asked, select *shared name* for the node identifier column. This will transform node identifiers into a column named "shared name" internally.
* `Layout > Prefuse Force Directed Layout > scenes`
* Find a node with degree larger than *D=100*
* [**REPORT**] Include in your report this graph. Indicate which character has degree larger than *D* (right click in any blank space, then select Add > Text annotation ...)
* [**REPORT**] Include a brief commentary of what kinds of characters are represented by nodes with degree larger than *D*

**Remember: do not use screenshots**; use `File > Export as image`

## 1.3. Import US companies co-ownership

Open a graph representing company co-ownership in the US:

* `File > Import > Network from File ...`
* Select `us_companies_ownership.csv`
* Click `OK` (accept default import)
* It might take a couple of minutes to open and layout
* [**REPORT**] Include in your report two images with the *second and third largest connected components* of this graph
* [**REPORT**] Do you see any connected component that is a *cycle*? If not, indicate this; if yes, include its image in the report
* [**REPORT**] Do you see any connected component that is a *star*? If not, indicate this; if yes, include its image in the report
* [**REPORT**] Look for any large company in the technology sector, include an image centered around that company and displaying its neighbors; add a one-paragraph commentary about what you see in this image

Note: you can zoom in and zoom out with the mouse scroll wheel, you can also use the panel on the bottom-right of the screen to navigate the graph.

**Final reminder: do not use screenshots**; use `File > Export as image`

# 2. How to edit node and edge styles

*You do not need to include anything from this part (part 2) in your report.*

Reload the Karate Club dataset (`karate.gml`).

Now you can play with the "Style" panel (top-left, between "Network" and "Filter"). Here are some ideas.

## 2.1. How to change the style of the entire network

To style the entire networks in different ways:

* Play with predefined styles available in the pull-down menu under `Styles`, e.g. "Rippled", "Curved", or others.

## 2.2. How to name nodes

To include in each node its name:

* In the label property,
* create a "Passthrough mapping"
* for attribute "name"

To remove these names:

* Remove the mapping (trash can icon)

*Note that node names might not be visible in large graphs until you zoom in. This is controlled by the setting under `View > Always Show Graphics Details`.*

## 2.3. How to change the shape of node

To change the shape of nodes:

* Click on the drawing to the left of "Shape" and choose another shape

## 2.4. How to change edge width

To change the width of edges:

* Click on "Edge" on bottom left (between "Node" and "Network")
* Click on "Width" property
* Mapping Type = Continuous Mapping
* Column = scenes (this will work in the *Star Wars* graph, which has a column with the number of scenes in common)
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

*You do not need to include anything from this part (part 2) in your report.*

# 3. Basic network analysis

## 3.1. Closeness and betweenness in the Karate Club

Perform basic network analysis. ``Tools > Analyze network``. Consider the network is not directed.

* Load the Karate Club network
* The analysis adds some node attributes
* [**REPORT**] Indicate which are the three nodes with the largest closeness centrality
* [**REPORT**] Indicate which are the three nodes with largest betweenness centrality
* Change the fill color of nodes to be red for nodes with larger *closeness  centrality*, white for node with smaller *closeness centrality* (you will need a continuous mapping for this)
* Change the size of the nodes (alternatively, their width) to be proportional to *betweenness centrality*
* Make sure all node labels are readable, you may need to play with the *label color* and/or *label font size* properties
* [**REPORT**] Include this image in your report

## 3.2. Plot degree distributions

Look at the results from the network analysis (you will need to go to ``View > Show results panel`` -- if it does not show up, try hiding and showing the results panel)

* [**REPORT**] Include a plot with the degree distributions in all three graphs (Karate, US Companies, StarWars). In the case of US companies, which is a directed graph, plot the out-degree.

*Tip: the user interface of Cytoscape is a bit confusing, as the bottom panel needs to be showing `Node Table` for the `Node Degree Distribution` button to work properly.*

## 3.3. Style the network

* Load the Star Wars network
* Make the size of the node larger either for nodes with high degree or nodes with high betweenness
* Change the width and color of edges so it depends o the "scenes" attribute of the network (number of scenes in common). More scenes should mean thicker and darker edges.
* [**REPORT**] Include an image of the network from *Star Wars*, styled as indicated above

# 4. Use a Cytoscape App (ClusterMaker2)

Cytoscape has "apps" that can be installed and used.

## 4.1. Install ClusterMaker2

Install ClusterMaker2 (``Apps > App Manager``). You may need to download a jar file from the [releases](https://apps.cytoscape.org/apps/clustermaker2) directory of clustermaker2, and then ``Install from file ...`` in the App Manager.

## 4.2. Use ClusterMaker2

Run the [affinity propagation](https://en.wikipedia.org/wiki/Affinity_propagation) clustering algorithm in ClusterMaker2 (``Apps > ClusterMaker2 > Affinity Propagation ...``) on the *Star Wars* network.

* Select any temporary folder if prompted
* ClusterMaker2 requires an attribute for the weight: use ``Array source = scenes`` in *Star Wars*
* Once you run it, the network will have a new attribute in the nodes (in the node table you will see an attribute named ``_APCluster``)
* Use the new attribute in the nodes for "Fill color" using a "Discrete mapping" on ``_APCluster.`` Note that with the right button you can generate a mapping out of a set of pre-defined ones.
[**REPORT**] Include in your report an image of the Star Wars network with colors representing clusters.
[**REPORT**] Include a brief commentary on what do you see in these clusters, what do you think they represent and why.

## 4.3. Apply to Karate Club

Use ClusterMaker2 on the Karate Club

* Try with two different cluster algorithms in the `ClusterMaker2` plug-in. Not all the methods work: try two that do.
   * You can find a description of the algorithms used in the [ClusterMaker2 homepage](http://www.rbvi.ucsf.edu/cytoscape/clusterMaker2/)
* If you can choose an attribute in the clustering algorithm, choose "Edge betweenness"
   * You MUST run the network analyzer first, so you can have "Edge betweenness" as an attribute in edges
* Compare both obtained clusters with the actual one

![Karate Club](karate-true-communities.png)

[**REPORT**] Include in your report an image of the Karate Club network with nodes painted according to clusters using the two methods you selected.

[**REPORT**] Include a brief commentary on what do you see in these clusters, and whether they have some relationship with the way in which the Karate Club actually splitted

# DELIVER (INDIVIDUALLY)

:warning: First of all, read [delivering your report](../upf/upf-evaluation.md) on the evaluation guidelines, and check your report against those guidelines before submitting.

Deliver a brief report of at most 4 pages (it can be less!), in PDF format. Organize your report as follows:

* Section 1 should briefly describe the three networks, including a table with the number of nodes and edges in each one; do not include visualizations in this section
* Sections 2, 3, 4 should include basically the parts marked "[**REPORT**]" above:
   * Section 2 should be everything you were asked to do with the *Karate Club* graph
   * Section 3 should be everything you were asked to do with the *Star Wars* graph
   * Section 4 should be everything you were asked to do with the *US Companies* graph

**Please be brief,** you do not need to write too much; your report can be less than four pages. A "brief commentary" means one or two paragraphs.

Your report should end with the following text:

**I hereby declare that all of the text, tables, and figures in this report were produced by myself.**
