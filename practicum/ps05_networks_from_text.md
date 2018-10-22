# Practice Session 05: Networks from Text

In this session we will learn to construct a network from a set of implicit relationships. The relationships that we will study are between accounts in Twitter, a micro-blogging service.

We will create two networks: one directed and one undirected.

In the **directed mention network**, we will say that there is a link of weight *w* from account *x* to account *y*, if account *x* has re-tweeted (re-posted) or mentioned *w* times account *y*.

In the **undirected co-mention network**, we will say that there is a link of weight *w* between accounts *x* and *y*, if both accounts have been mentioned together in *w* tweets.

# 0. Input: a collection of tweets

The input material you will use is a file named `EstamosPorTi.json.gz`. This is a gzip-compressed file, which you can de-compress using the `gunzip` command. The file contain about 16,800 messages ("tweets") posted between October 1st, 2017, and October 24th, 2017, and using the hashtag `#EstamosPorTi`. Background information on this collection is available on [the Internet Archive](https://archive.org/details/EstamosporTIOohmm2018032618831Ids).

The tweets are in a format known as [JSON](https://en.wikipedia.org/wiki/JSON#Example). Python's JSON library takes care of translating it into a dictionary.

## How this file was obtained

This file was obtained from the [Tweet ID Catalog](https://www.docnow.io/catalog/). This is a website that provides several collections of tweets, however, they only provide the identifier of the tweet, known as a tweet-id.

To recover the entire tweet, a process commonly known as *re-hydration* needs to be used, which involves querying an API from Twitter, giving the tweet-id, and obtaining the tweet. This can be done with a little bit of programming or using a software such as [Hydrator](https://github.com/docnow/hydrator#readme).

# 0. Imports

```python
import io
import json
import gzip
```

# 1. How to read the tweets

We do not need to uncompress this file (it is about 132 MB uncompressed, but only 11 MB compressed).

```python
INPUT_FILENAME = "EstamosPorTi.json.gz"

with gzip.open(INPUT_FILENAME, "rt", encoding="utf-8") as input_file:
    for line in input_file:
        tweet = json.loads(line)
        author = tweet["user"]["screen_name"]
        message = tweet["full_text"]
        print("%s: '%s'" % (author, message))
```

If instead you want to open it in uncompressed, first `gunzip` the file and then do:

```python
INPUT_FILENAME = "EstamosPorTi.json"

with io.open(INPUT_FILENAME, "r", encoding="utf-8") as input_file:
```

The rest of the code stays the same.

*Tip*: place all the `import` commands in a single cell at the top of your notebook.

# 2. How to extract mentions

What we need now is a function to extract mentions, so that if we give, for instance `RT @Jordi: check this post by @Xavier`, it returns the list `["Jordi", "Xavier"]`.

This is such function:

```python
import re

def extract_mentions(text):
    return re.findall("@([a-zA-Z0-9]{5,20})", text)
```

Note that the `import re` command must be at the beginning of the file, together with the other imports. You may need to execute the cell that contains the import by pressing `Shift-Enter` on it.

You can now print all the links between accounts by doing:

```python
mentions = extract_mentions(message)
for mention in mentions:
    print("%s mentioned %s" % (author, mention))
```

# 3. Aggregating

We are going to count how many times a mention happen. To do this, we will keep a dictionary:

```python
count = {}
```

Each key in the dictionary will be a tuple `(author, mention)` where `author` is the username of the person who writes the message, and `mention` the username of someone who is mentioned in the message. To update the dictionary, use this code while you are reading the input file:

```python
for mention in mentions:
    key = (author, mention)
    if key in count:
        count[key] += 1
    else:
        count[key] = 1
```

# 4. Write to file

Now we will create the network on disk. Place this code on a new cell and execute it after running the previous cell in which you read the file and updated the `count` dictionary:

```python
OUTPUT_FILENAME = "EstamosPorTi.csv"

with io.open(OUTPUT_FILENAME, "w") as output_file:
    writer = csv.writer(output_file, delimiter='\t', quotechar='"')
    writer.writerow(["Source", "Target", "Weight"])
    for key in count:
        author = key[0]
        mention = key[1]
        weight = count[key]
        writer.writerow([author, mention, weight])
```

Remember to `import csv` at the beginning of the file. You may have to press `Shift-Enter` in the cell with the imports.

Create two files: one `EstamosPorTi.csv` containing all edges, and one `EstamosPorTi-w2.csv` containing all edges appearing twice or more.

# 5. Open the directed mention network in Cytoscape

Open the `EstamosPorTi-w2.csv` file in Cytoscape. The file is large so you may need to "View > Show Graphics Details" and "View > Hide Graphics Details".

Style the network:

* Run "Tools > Network Analyzer > Network Analysis > Analyze Network ..."
* Style nodes by setting their size proportional to their in-degree (treat the network as directed).
* Style edges by setting their width using the *weight* attribute.

Look at the Results Panel of the network analyzer. There is interesting information here, particularly in the "Simple Parameters" and degree distribution tabs.

Run the ModuLand plug-in to create a clustering of this graph using the *weight* edge attribute.

# 6. Create a co-mention network

The co-mention network connects two accounts if they are both mentioned in the same tweet. The weight of the edge is the number of tweets in which the accounts are co-mentioned.

Create new code to generate the co-mention network by modifying the previous code (make a copy of those cells so you can keep your old code, too). First, you need a way of creating pairs of co-mentioned nodes while you read the input file; this is the relevant code snippet:

```python
for mention1 in mentions:
    for mention2 in mentions:
        if mention1 < mention2:
            key = (mention1, mention2)
            if key in co_mentions:
                co_mentions[key] += 1
            else:
                co_mentions[key] = 1
```

Second, you need to write this to a file `EstamosPorTi-CoMentions.csv` using the CSV writer, as we did before; this is the relevant code snippet:

```python
for key in co_mentions:
    mentioned1 = key[0]
    mentioned2 = key[1]
    weight = co_mentions[key]
    writer.writerow([mentioned1, mentioned2, weight])
```

# 7. Open the undirected co-mention network in Cytoscape

Open the `EstamosPorTi-CoMentions.csv` file in Cytoscape.

Style the network so that line widths are larger for edges with large weights, and node sizes are larger for nodes with large degrees. Remember you need to run the network analyzer first.

Use "Layout > Prefuse Force Directed Layout > All Nodes > Weight" to create a layout by edge weight.

Run the ModuLand plug-in to create a clustering of this graph using the *Weight* attribute as weight.

# DELIVER (individually or in pairs)

Deliver a zip file containing your code and report.

The code should be your Python notebook (a `.ipynb` file).

The report should be a two-page PDF file.

* On the first page, include an image of the directed network (exported, not a screenshot), and 2-3 lines with your observations.
* On the second page, include an image of the undirected network (exported, not a screenshot), and 2-3 lines with your observations.

In your observations you can mention high-centrality nodes, the type of components you observe, and/or some aspects that you find relevant from the results of the network analyzer (e.g., number of nodes, edges, connected components, characteristic path lengths, average degrees, etc.). Do not include a screenshot of the results panel: describe what you see there using the numbers from the analysis and your own words.

*Tip*: use an online document editor to work on this, it will make collaborating easy.
