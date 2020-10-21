# Practice Session 02: Cytoscape Advanced

## Materials for this Session

(See [how to download](data/README.md) in the README of the data/ directory)

* Marvel Universe Social Graph: [hero-network.csv](data/hero-network.csv)
* Les miserables graphs: [les_miserables-characters.csv](https://github.com/chatox/networks-science-course/blob/master/practicum/data/les_miserables-characters.csv) and [les_miserables-chapters.csv](https://github.com/chatox/networks-science-course/blob/master/practicum/data/les_miserables-chapters.csv)

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

[**REPORT**] Include a brief commentary on the number of nodes and edges in different sub-graphs from different characters. Why do you think influences these numbers?

:warning: **Important**: by default Cytoscape has a [level of detail](http://manual.cytoscape.org/en/stable/Rendering_Engine.html#what-is-level-of-detail-lod) setting that is similar to the one found in videogames. If the current view contains more than *render.nodeLabelThreshold*, the node labels are not displayed. You can toggle between full details and reduced details using "View > Show Graphics Details" and "View > Hide Graphics Details." You can also permanently adjust this by going to "Edit > Preferences". Depending on the computer, you can set this up to 2000 from the default of 200. Be careful: this will block your computer when dealing with large networks such as the hero network.

# 2. Creating a network

Now we will practice creating small networks.

## 2.1. Creating from existing spreadsheets

We will create a network from two spreadsheets. The first one, `les_miserables-characters.csv`, contains the name and gender of the characters in the novel *Les Misérables* by Victor Hugo. The second one, `les_miserables-chapters.csv` contains the number of chapters in which two characters appear.

First we import the network:

* ``File > Import > Network from file ...``
* Use file ``les_miserables-chapters.csv``
* Select for name1: "Source Node" (it's a green disc)
* Select for name2: "Target Node" (it's a red target)
* Select for numchapters: "Edge Attribute"

Run the network analysis and create a prefuse force directed layout on the attribute ``numchapters``.

Now we import the node attribute:

* ``File > Import > Table from file ...``
* Use file ``les_miserables-characters.csv``
* Import data as "Node Table Columns"
* The first column (name) should be the key.
* The second column (gender) should be an attribute

Now, use the "gender" attribute to determine the shape and color of nodes. Use style, shape, fill-color, and discrete mappings.

[**REPORT**] Include the graph of *Les Misérables*.

[**REPORT**] Include a brief commentary on what do you observe with respect to gender in this novel, according to the graph you are looking at.

## 2.2. Create a new network in a CSV file

Now, create a network on your own using CSV files, on whatever topic of your choice as long as the network is **real**. You will need two CSV files: one for the network and one for the attributes. The network should include between 15 and 30 nodes.

Some ideas:

* Nodes can be characters in a movie, edges connecting characters depending on their affinity.
* Nodes can be music bands or artists, attributes whether the node is a band or an artist, edges connect artists to the bands they've played in.
* Nodes can be countries, attributes can be population sizes, connections can be countries that share a border.
* Note that edges can also have attributes, which you can use to change the color or style of lines in the graph.

These are only ideas. Be creative.

*Tip:* to include a legend, you can use the Cytoscape app [legend creator](https://apps.cytoscape.org/apps/legendcreator).

[**REPORT**] Describe the graph you created.

[**REPORT**] Include two tables with the contents of the CSV files you created (not screenshots).

[**REPORT**] Draw the graph in Cytoscape and include it in your report.

# DELIVER (INDIVIDUALLY)

Deliver a report describing these networks, having at most 4 pages in PDF. The report should have **three numbered sections**: one for the *Marvel* network, one for *Les Misérables*, and one for the network you created. Remember to include all of the elements marked [**REPORT**] above.
