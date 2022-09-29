# Practice Session 02: Cytoscape Advanced

## Materials for this Session

(See [how to download](data/README.md) in the README of the data/ directory)

* Marvel Universe Social Graph: [hero-network.csv](data/hero-network.csv)
* Game of Thrones Characters: [got-characters.csv](data/game-of-thrones/got-characters.csv) and [got-relationships.csv](data/game-of-thrones/got-relationships.csv)

## Contents

1. Importing networks
1. Creating networks
1. Editing networks

# 1. Working with a large network

The Marvel Universe Social Graph contains characters from the Marvel Universe that appear in the same comic number. It contains over half a million edges. It is formatted in the following way:

    BLACK PANTHER/T'CHAL<tab>HAWK
    BLACK PANTHER/T'CHAL<tab>LOKI [ASGARDIAN]
    BLACK PANTHER/T'CHAL<tab>HULK/DR. ROBERT BRUC
    SPIDER-MAN/PETER PAR<tab>HULK/DR. ROBERT BRUC
    ...

## 1.1. Import this network into Cytoscape

To import it into Cytoscape:

* File > Import > Network from File ...
* Select `hero-network.csv`
* Advanced Options ...: indicate the delimiter is only a tabulator (**TAB**).
  * :warning: If you keep the default delimiter, a comma, or you use tabulator and comma, you will mistakenly get too many nodes (as node names include commas inside) and Cytoscape may hang for a long time or crash.
* Column 1 should be "Source" (it's a green disc)
* Column 2 should be "Target" (it's a red target)
* OK

*Tip: change the style to "minimal" to see the graph better.*

[**REPORT**] Include this graph in your report.

[**REPORT**] What are the top 10 nodes with largest degree?

## 1.2. Create sub-graphs

* Search for the node named "RAVEN"
  * Option 1: use the search box is on top of the display
  * Option 2: find this node in the node table, select it, and then use the secondary button to indicate "Select nodes from selected rows"
* Click on the two-house icon on top, it means *neighbor*
* Now you've selected one character and all his neighbors.
* `File > New Network > From selected nodes, all edges`

[**REPORT**] Indicate the number of nodes and edges of this sub-graph, it appears on the left panel next to the name of the network.

* Run the network analyzer
* Run the Prefuse Force Directed Layout using edge betweenness as a weight

[**REPORT**] Describe what you see in this graph. If you see any community structure, describe it.

* Do the same for another character

[**REPORT**] Indicate the number of nodes and edges in the sub-graph of nodes connected to the other character you found

Note that you can also select by other characteristics, such as degree, by creating a filter in the "Select" panel.

[**REPORT**] Include a brief commentary on the number of nodes and edges in different sub-graphs from different characters. Why do you think influences these numbers?

:warning: **Important**: by default Cytoscape has a [level of detail](http://manual.cytoscape.org/en/stable/Rendering_Engine.html#what-is-level-of-detail-lod) setting that is similar to the one found in videogames. If the current view contains more than *render.nodeLabelThreshold*, the node labels are not displayed. You can toggle between full details and reduced details using "View > Show Graphics Details" and "View > Hide Graphics Details." You can also permanently adjust this by going to "Edit > Preferences". Depending on the computer, you can set this up to 2000 from the default of 200. Be careful: this will block your computer when dealing with large networks such as the hero network.

# 2. Creating a network

Now we will practice creating small networks.

## 2.1. Creating from existing spreadsheets

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
* Use the *relationship* attribute to label edges. Leave edges in color black, except for edges representing killing, which should be in red.

[**REPORT**] Include the graph of *Game of Thrones*.

[**REPORT**] Show one example of a long chain (4 or more characters) in this graph. Indicate which characters are involved.

[**REPORT**] Show one example of a multi-edge in this graph. Indicate which characters are involved.

[**REPORT**] Describe any observation you can make about how node attribute "house of birth" relates to edge attribute "relationship"

## 2.2. Create a new network in a CSV file

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

Deliver a report describing these networks, having at most 4 pages in PDF. The report should have **four numbered sections**:

* Section 1 for a table with the number of nodes and edges in the three networks
* Section 2 for the *Marvel* network
* Section 3 for the *Game of Thrones* network
* Section 4 for the network you created

Remember to include all of the elements marked [**REPORT**] above.

**Note**: If you find any mistake in the Game of Thrones graph, e.g., something wrong with respect to the TV series, please send us the corrected CSV files.

Your report should end with the following text:

**I hereby declare that all of the text, tables, and figures in this report were produced by myself.**
