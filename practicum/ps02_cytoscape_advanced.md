# Practice Session 02: Cytoscape Advanced

## Materials for this Session

(See [how to download](data/README.md) in the README of the data/ directory)

* Marvel Universe Social Graph: [hero-network.csv](data/hero-network.csv)
* Barcelona holidays data: [holidays-bcn-network.csv](data/holidays-bcn-network.csv) and [holidays-bcn-node-attributes.csv](data/holidays-bcn-node-attributes.csv)

## Contents

1. Importing networks
1. Creating networks
1. Editing networks

# 1. Working with a large CSV file

The Marvel Universe Social Graph contains characters from the Marvel Universe that appear in the same comic number. It contains over half a million edges. It is formatted in the following way:

    BLACK PANTHER/T'CHAL<tab>HAWK
    BLACK PANTHER/T'CHAL<tab>LOKI [ASGARDIAN]
    BLACK PANTHER/T'CHAL<tab>HULK/DR. ROBERT BRUC
    SPIDER-MAN/PETER PAR<tab>HULK/DR. ROBERT BRUC
    ...

## 1.1. Import this network into Cytoscape

To import it into Cytoscape:

* File > Import > Network > File ...
* Select `hero-network.csv`
* Advanced Options ...: indicate the delimiter is a tabulator (**TAB**).
  * :warning: If you use the default delimiter, a comma, you will mistakenly get too many nodes (as node names include commas inside) and Cytoscape may hang for a long time or crash.
* Column 1 should be "Source" (it's a green disc)
* Column 2 should be "Target" (it's a red target)
* OK

Tip: change the style to minimalistic to see the graph better.

[**REPORT**] Include this graph in your report.

[**REPORT**] Indicate what you believe are the small components that are disconnected from the main connected component.

## 1.2. Create sub-graphs

* Search for the node named "BLACK PANTHER/T'CHAL"
  * Option 1: use the search box is on top of the display. Depending on the OS (usually in Linux-based systems) you should add \ in the search in order to exclude special characters: "BLACK\ PANTHER/T'CHAL"
  * Option 2: find this node in the node table, select it, and then use the secondary button to indicate "Select nodes from selected rows"
* Click on the two-house icon on top, it means *neighbor*
* Now you've selected one character and all his neighbors.
* File > New > Network > From selected nodes, all edges

[**REPORT**] Indicate the number of nodes and edges of this sub-graph, it appears on the left panel next to the name of the network.

* Do the same for a less popular character "ENCHANTRESS"
* Notice the number of nodes is much smaller but the number of edges is not proportionally as small. Why do you think this happens?

[**REPORT**] Indicate the number of nodes and edges in the sub-graph of nodes connected to "ENCHANTRESS".

Note that you can also select by other characteristics, such as degree, by creating a filter in the "Select" panel.

:warning: **Important**: by default Cytoscape has a [level of detail](http://manual.cytoscape.org/en/stable/Rendering_Engine.html#what-is-level-of-detail-lod) setting that is similar to the one found in videogames. If the current view contains more than *render.nodeLabelThreshold*, the node labels are not displayed. You can toggle between full details and reduced details using "View > Show Graphics Details" and "View > Hide Graphics Details." You can also permanently adjust this by going to "Edit > Preferences". Depending on the computer, you can set this up to 2000 from the default of 200. Be careful: this will block your computer when dealing with large networks such as the hero network.

# 2. Creating a network

Now we will practice creating small networks.

## 2.1. Creating from existing spreadsheet

We will create a network from two small spreadsheets. The first one, `holidays-bcn-network.csv`, contains month names and the holidays in those months. The second one, `holidays-bcn-node-attributes.csv`, contains the type of each holiday.

First we import the network:

* Import as a network `holidays-bcn-network.csv`
* Remember to set the advanced options for "," as a separator and to *not* use the first row as column names.
* Select for column 1: "Source Node" (it's a green disc)
* Select for column 2: "Target node" (it's a red target)

Now we import the node attribute:

* File > Import > Table > File ...
* Select `holidays-bcn-node-attributes.csv`
* Import data as "Node Table Columns"
* Set the advanced options for "," as a separator and *not* to use the first row as names
* The first column (the holiday name) should be the key.
* The second column (the holiday type) should be an attribute; name this attribute "type of holiday"

Now, use the "type of holiday" attribute to determine the shape and color of nodes. Use style, shape, fill-color, and discrete mappings. You will have to manually select a color for each of the three types of holidays. Make sure the month names are ellipses, the holidays are rectangles, and 4 colors are used (one color for the month name, and one different color for each holiday type). Manually arrange months in chronological order.

[**REPORT**] Include the graph of holidays.

## 2.2. Create a new network in a CSV file

Now, create a network on your own using CSV files. You will need two CSV files: one for the network and one for the attribute.

Include at least 12 nodes, and at least one attribute per node. Be creative (but tasteful). For instance, you can create a social network of friends, a network of characters in a movie, TV series, or novel, a network of musicians and music bands, or sportsmen/sportswomen and teams, or anything you find interesting.

[**REPORT**] Include two tables with the contents of the CSV files you created (not screenshots).

[**REPORT**] Include the graph you created and styled from these CSV files.

## 2.3. Creating inside the application

Creating a small network inside the application is easy: File > New > Network > Empty Network.

* To add nodes, right click on the display and create a new nodes.
* To add edges, select two nodes by holding "shift" while you click on them, then right click on the display and then Add > Edge containing the selected nodes.
* Deleting nodes/edges is easy, practice this
* Learn to edit node names (should change this visibly)
* Learn to edit interactions (should change this visibly)

Create a small graph of 4-5 nodes and 2-3 connections.

[**REPORT**] Include the graph you created and styled within the application.

# DELIVER (INDIVIDUALLY)

Deliver a report having at most 4 pages in PDF, containing each of the elements marked [**REPORT**] above. You do not need to add a long narrative explanation to your report, just the requested elements.

For each of those elements:

* Include the section number where each element is requested.
* Include a descriptive title, remembering to indicate from which network each element comes.
* For images and plots, include a brief commentary.
