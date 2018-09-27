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
* Advanced Options ...: indicate the delimiter is a tabulator, and *not* to use the first row as column names.
* Select for column 1: "Source Node" (it's a green disc)
* Select for column 2: "Target node" (it's a red target)
* OK

Change the style to minimalistic, try to determine what is the disconnected component that is observed in the network.

**Important**: by default Cytoscape has a [level of detail](http://manual.cytoscape.org/en/stable/Rendering_Engine.html#what-is-level-of-detail-lod) setting that is similar to the one found in videogames. If the current view contains more than *render.nodeLabelThreshold*, the node labels are not displayed. You can toggle between full details and reduced details using "View > Show Graphics Details" and "View > Hide Graphics Details." You can also permanently adjust this by going to "Edit > Preferences". Depending on the computer, you can set this up to 2000 from the default of 200.

## 1.2. Create sub-graphs

* Search for the node named "BLACK PANTHER/T'CHAL" - the search box is on top of the display. Depending on the OS (usually in Linux-based systems) you should add \ in the search in order to exclude special characters: "BLACK\ PANTHER/T'CHAL"
* Click on the two-house icon on top, it means *neighbor*
* Now you've selected one character and all his neighbors.
* File > New > Network > From selected nodes, all edges

Notice the number of nodes and edges of this sub-graph, it appears on the left panel next to the name of the network.

* Do the same for a less popular character "ENCHANTRESS"
* Notice the number of nodes is much smaller but the number of edges is not proportionally as small. Why do you think this happens?

Note that you can also select by other characteristics, such as degree, by creating a filter in the "Select" panel.

# 2. Creating a network

Now we will practice creating small networks.

## 2.1. Creating from existing spreadsheet

We will create a network from two small spreadsheets. The first one, `holidays-bcn-network.csv`, contains month names and the holidays in those months. The second one, `holidays-bcn-node-attributes.csv`, contains the type of each holiday.

First we import the network:

* Import as a network `holidays-bcn-network.csv`
* Remember to set the advanced options for "," as a separator and to *not* use the first row as column names.

Now we import the node attribute:

* File > Import > Table > File ...
* Select `holidays-bcn-node-attributes.csv`
* Import data as "Node Table Columns"
* Set the advanced options for "," as a separator and *not* to use the first row as names
* The first column (the holiday name) should be the key.
* The second column (the holiday type) should be an attribute; name this attribute "type of holiday"

Now, use the "type of holiday" attribute to determine the color of nodes. Use style, fill-color, and a discrete mapping. You will have to manually select a color for each of the three types of holidays.

## 2.2. Create a new network

Now, create a network on your own. Include around 10 nodes, and one attribute per node. Be creative (but tasteful). For instance, you can create a social network of friends or characters in a TV series, and some attribute for the type of character.

## 2.3. Creating inside the application

Creating a small network inside the application is easy: File > New > Network > Empty Network.

* To add nodes, right click on the display and create a new nodes.
* To add edges, select two nodes by holding "shift" while you click on them, then right click on the display and then Add > Edge containing the selected nodes.

Create a small graph of 4-5 nodes and 2-3 connections.

# 3. Editing a network

Play with one of the small networks you created from a csv file:

* Delete edges
* Add edges
* Edit node names (should change this visibly)
* Edit interactions (should change this visibly)

# DELIVER (INDIVIDUALLY)

Deliver a report containing:

* an image of the hero network,
* an image of the sub-graph of the hero network you extracted,
* an image of the Barcelona holidays data, and
* an image of the small network you created and styled.

Feel free to include small comments inside or between the images.

