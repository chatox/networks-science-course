# Practice Session 05: Networks from Text

In this session we will learn to construct a network from a set of implicit relationships. The relationships that we will study are between accounts in Twitter, a micro-blogging service.

We will say that there is a link of weight *w* from account *x* to account *y*, if during a given time period, account *x* has re-tweeted (re-posted) or mentioned *w* times account *y*.

The input material you will use is a file named `EstamosPorTi.json.gz`. This is a gzip-compressed file, which you can de-compress using the `gunzip` command. The file contain about 16,800 messages ("tweets") posted between October 1st, 2017, and October 24th, 2017, and using the hashtag `#EstamosPorTi`. Background information on this collection is available on [the Internet Archive](https://archive.org/details/EstamosporTIOohmm2018032618831Ids).

# 0. How was this file obtained?

This file was obtained using the [Tweet ID Catalog](https://www.docnow.io/catalog/). This is a website that provides several collections of tweets, however, they only provide the identifier of the tweet, known as a tweet-id.

To recover the entire tweet, a process commonly known as *re-hydration* needs to be used, which involves querying an API from Twitter, giving the tweet-id, and obtaining the tweet. This can be done with a little bit of programming or using a software such as [Hydrator](https://github.com/docnow/hydrator#readme).

The tweet is in a format known as [JSON](https://en.wikipedia.org/wiki/JSON#Example). Python's JSON library takes care of translating it into a dictionary.

# 1. How to read the tweets

We do not need to uncompress this file (it is about 132 MB uncompressed, but only 11 MB compressed).

```python
import io
import json
import gzip

INPUT_FILENAME = "EstamosPorTi.json.gz"

with gzip.open(INPUT_FILENAME, "rt") as input_file:
    for line in input_file:
        tweet = json.loads(line)
        author = tweet["user"]["screen_name"]
        message = tweet["full_text"]
        print("%s: '%s'" % (author, message))
```

If instead you want to open it in uncompressed, first `gunzip` the file and then do:

```python
INPUT_FILENAME = "EstamosPorTi.json"

with io.open(INPUT_FILENAME, "r") as input_file:
```

The rest of the code stays the same.

Tip: place all the `import` commands in a single cell at the top of your file.

# 2. How to extract mentions

What we need one is a function to extract mentions, so that if we give, for instance "RT @Jordi: check this post by @Xavier", it returns the list ["@Jordi", "@Xavier"].

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
    print("%s -> %s" % (author, mention))
```

# 3. Aggregating

We are going to count how many times a mention happen. To do this, we will keep a dictionary:

```python
counts = {}
```

Each key in the dictionary will be a tuple `(author, mention)` where `author` is the username of the person who writes the message, and `mention` the username of someone who is mentioned in the message. To update the dictionary, we use this code:

```python
for mention in mentions:
    key = (author, mention)
    if key in count:
        count[key] += 1
    else:
        count[key] = 1
```

# 4. Write to file

Now we will create the network on disk:

```python
OUTPUT_FILENAME = "EstamosPorTi.csv"

with io.open(OUTPUT_FILENAME, 'w') as output_file:
    writer = csv.writer(output_file, delimiter='\t', quotechar='"')
    writer.writerow(["Source", "Target", "Weight"])
    for key in count:
        writer.writerow([key[0], key[1], count[key]])
```

Remember to `import csv` at the beginning of the file. You may have to press `Shift-Enter` in the cell with the imports.

5. Open this file in Cytoscape

TO DO CONTINUE
TO DO CONTINUE
TO DO CONTINUE
TO DO CONTINUE
TO DO CONTINUE
TO DO CONTINUE
TO DO CONTINUE 

# DELIVER (individually)

At the end of the session, deliver an image file in .png format (File > Export as image) of the network you created.
