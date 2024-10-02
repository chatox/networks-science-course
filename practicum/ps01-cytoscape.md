# Practice Session 01: Cytoscape Basics and Advanced

## Materials for this session

:warning: Do not simply right-click on the file names below, or you will download an HTML file that will not be readable by Cytoscape. See [how to download](data/README.md) in the README of the data/ directory.

* File "[karate.gml](data/karate-club/karate.gml)"
* File "[reptilia-tortoise.graphml](data/reptilia-tortoise/reptilia-tortoise.graphml)"
* Marvel Universe Social Graph: [marvel-hero.csv](data/marvel-hero.csv)
* Game of Thrones Characters: [got-characters.csv](data/game-of-thrones/got-characters.csv) and [got-relationships.csv](data/game-of-thrones/got-relationships.csv)

## What you should deliver

What you should deliver is explained at the end of each practice handout. In short, it is a 9-pages report.

## Contents of this session

Basic concepts:

0. About Cytoscape
1. Importing a network
2. Editing nodes and edge styles
3. Performing basic network analysis

Advanced concepts:

4. Working with large network (Importing, creating subgraphs)
5. Creating new networks (from a file, in a csv file)

# 0. About Cytoscape

[Cytoscape](http://www.cytoscape.org/) is an open source software platform for visualizing complex networks and integrating these with any type of attribute data.

# 1. Importing a network

## 1.1. Import Zachary's karate club

Let's start with a simple case: [Zachary's Karate Club](https://en.wikipedia.org/wiki/Zachary%27s_karate_club), which captures 34 members of a karate club at a university, with links representing interactions between members outside the club.

* `File > Import > Network from File ...`
* Select `karate.gml`
* `Layout > Compound Spring Embedder`
* Determine which are the two nodes with the largest degree.
   * *Tip: use `Tools > Analyze network` (do not check "directed") and look at the `Node table` displayed under the graph*
* [**REPORT**] Include in your report this graph plus and a brief paragraph indicating what are the top two nodes having the larger *Degree*. Why are they so connected?
* [**REPORT**] Indicate one person that has degree larger than *D=9* (right click in any blank space, then select Add > Text annotation ...). Put the text in red so that we can see.
* [**REPORT**] The Compound Spring Embedder is an algorithm derived from force-directed graph layout algorithms. Read the Wikipedia page on [force-directed graph drawing](https://en.wikipedia.org/wiki/Force-directed_graph_drawing) and explain in one paragraph, in your own words, how this works.

**Do not use screenshots**; use `File > Export as image`


## 1.2. Import network of tortoises

Open a graph representing tortoises who shared a burrow in the Nevada desert. It is interesting because desert tortoises are assumed to be solitary animals, and this study based on radio tags showed the extent to which they can sometimes be social. The graph we use is a projection of a bipartite graph of tortoises and burrows.

* `File > Import > Network from File ...`
* Select `reptilia-tortoise.graphml`
* Indicate this goes to a new *Network Collection* to keep it separate from the Karate graph.
* `Layout > Prefuse Force Directed Layout`
* To extract a sub-graph, select some nodes and use `File > New Network > From selected nodes, all edges`
* [**REPORT**] Extract the *second and third largest connected components* of this graph, breaking ties arbitrarily if there are components with the same size, and include this in your report.
Laia: you can do the table analysis and the  find the edges.
* [**REPORT**] Extract the largest connected component that is a *clique*, include it in your report and indicate how many nodes it has.
Laia: how can we find cliques using cytoscapes?
* [**REPORT**] Extract the largest connected component that is a *line graph*, include it in your report and indicate how many nodes it has.
Laia: how do we find line graphs?

Note: you can zoom in and zoom out with the mouse scroll wheel, you can also use the panel on the bottom-right of the screen to navigate the graph.

**Reminder: do not use screenshots**; use `File > Export as image`

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
Laia: I have no idea what this passthrough mapping is? 
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

## 2.5. How to change the entire layout

Try some layouts ("Layout" menu)

* Degree Sorted Circle Layout > All nodes
* Edge Weighted Spring Embedded Layout
* Prefuse Force Directed Layout

*You do not need to include anything from this part (part 2) in your report.*

# 3. Basic network analysis

## 3.1. Plot degree distributions

Look at the results from the network analysis (you will need to go to ``View > Show results panel`` -- if it does not show up, try hiding and showing the results panel)

* [**REPORT**] Include a plot with the degree distributions in all two graphs (Karate, Tortoises).

*Tip: the user interface of Cytoscape is a bit confusing, as the bottom panel needs to be showing `Node Table` for the `Node Degree Distribution` button to work properly.*


# 4. Working with a large network

The Marvel Universe Social Graph contains characters from the Marvel Universe that appear in the same comic number. It contains over half a million edges. It is formatted in the following way:

    BLACK PANTHER/T'CHAL<tab>HAWK
    BLACK PANTHER/T'CHAL<tab>LOKI [ASGARDIAN]
    BLACK PANTHER/T'CHAL<tab>HULK/DR. ROBERT BRUC
    SPIDER-MAN/PETER PAR<tab>HULK/DR. ROBERT BRUC
    ...

## 4.1. Import this network into Cytoscape

To import it into Cytoscape:

* File > Import > Network from File ...
* Select `marvel-hero.csv`
* Advanced Options ...: indicate the delimiter is only a tabulator (**TAB**).
  * :warning: If you keep the default delimiter, a comma, or you use tabulator and comma, you will mistakenly get too many nodes (as node names include commas inside) and Cytoscape may hang for a long time or crash.
* Column 1 should be "Source" (it's a green disc)
* Column 2 should be "Target" (it's a red target)
* OK
* It might ask to create a view, do it. That might take a few minutes.

*Tip: change the style to "minimal" to see the graph better.*

[**REPORT**] Include this graph in your report.

[**REPORT**] What are the top 20 nodes with the largest degree?

## 4.2. Create sub-graphs

* Search for one Marvel character -- ideally not a very well-known one, otherwise you will have too many nodes. (maximum a degree of 30)
  * Option 1: use the search box that is on top of the display
  * Option 2: find this node in the node table, select it, and then use the secondary button to indicate "Select nodes from selected rows"
* Click on the two-house icon on top, it means *neighbor*
* Now you've selected one character and all his neighbors.
* `File > New Network > From selected nodes, all edges`

[**REPORT**] Indicate the number of nodes and edges of this sub-graph, it appears on the left panel next to the name of the network.

* Run the network analyzer

:warning: **Important**: by default Cytoscape has a [level of detail](http://manual.cytoscape.org/en/stable/Rendering_Engine.html#what-is-level-of-detail-lod) setting that is similar to the one found in videogames. If the current view contains more than *render.nodeLabelThreshold*, the node labels are not displayed. You can toggle between full details and reduced details using "View > Always Show Graphics Details". You can also permanently adjust this by going to "Edit > Preferences". Depending on the computer, you can set this up to 2000 from the default of 200. Be careful: this will block your computer when dealing with large networks.

# 5. Creating a network

Now we will practice creating small networks.

## 5.1. Creating from existing spreadsheets

We will create a network from two spreadsheets. The first one, `got-characters.csv`, contains the name and house of the characters in the series *Game of Thrones* by George R. R. Martin. The second one, `got-relationships.csv` contains relationships between characters.

First we import the edges:

* ``File > Import > Network from file ...``
* Use file ``got-relationships.csv``
* Select for `src`: "Source Node" (it's a green disc)
* Select for `dest`: "Target Node" (it's a red target)
* Select "Edge Attribute" for the other columns

Now we import the node attribute:

* ``File > Import > Table from file ...``
* Use file ``got-characters.csv``
* Import data as "Node Table Columns"
* The first column (id) should be the key.
* The other columns should be attributes

Next, style the network:

* Use the *character-name* of the character as the node label.
* Use the *degree* as the size of the node (you will need to run the network analysis first with Tools > Analyze Network)
* Use the *house-birth* attribute to determine the shape and color of nodes. Use style, shape, fill-color, and discrete mappings.
* Use the *relation* attribute to label edges. Leave edges in color black, except for edges representing killing, which should be in red.

[**REPORT**] Include the graph of *Game of Thrones*.

[**REPORT**] Select and extract (i.e., File > New Network > From Selected Nodes, All Edges) a graph containing one clique of four or more characters. Indicate which characters are involved, and style the edges so that they show as label the *relation* between the characters.

[**REPORT**] Show two examples of a multi-edge in this graph. Indicate which characters are involved. Extract the corresponding (2-nodes) subgraphs.

[**REPORT**] Describe any observation you can make about how node attribute "house of birth" is distributed in the graph.

## 5.2. Create a new network in a CSV file

Now, create a network on your own using CSV files, on whatever topic of your choice as long as the network is **real**. You will need two CSV files: one for the network and one for the attributes. The network should include between 20 and 30 nodes.

Some ideas:

* Nodes can be music bands or artists, attributes whether the node is a band or an artist, edges connect artists to the bands they have played in, or you can also have "genre" nodes for different genres/subgenres
* Nodes can be characters in a movie, edges connecting characters depending on their affinity.
* Nodes can be countries, attributes can be population sizes, connections can be countries that share a border.
* Note that edges can also have attributes, which you can use to change the color or style of lines in the graph.

These are only ideas. Be creative.

*Tip:* to include a legend, you can use the Cytoscape app [legend creator](https://apps.cytoscape.org/apps/legendcreator).

[**REPORT**] Describe the graph you created.

[**REPORT**] Include two tables with the contents of the CSV files you created (not screenshots).

[**REPORT**] Draw the graph in Cytoscape and include it in your report.



# DELIVER (INDIVIDUALLY)

:warning: First of all, read [delivering your report](../upf/upf-evaluation.md) on the evaluation guidelines, and check your report against those guidelines before submitting.

Deliver a brief report of at most 9 pages (it can be less!!), in PDF format. Organize your report as follows:

* For each section, you should include basically the parts marked "[**REPORT**]" in this readme:
   * Section 1 should be a table with the number of nodes and adges in the networks used throught this practise
   * Section 2 should be everything you were asked to do in 1.1 and 1.2
   * Section 3 should be everything that you were asked to do in section 3.1
   * Section 4 should be everything that you were asked to do in section 4.1, 4.2
   * Section 5 sould be everything that you were asked to do in section 5.1, 5.2

**Please be brief,** you do not need to write too much; your report can be less than nine pages. A "brief commentary" means one or two paragraphs.

Your report should end with the following text:

**I hereby declare that all of the text, tables, and figures in this report were produced by myself.**
