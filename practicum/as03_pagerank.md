# Assignment 03: PageRank

This task is based on a collection of hosts in the UK that has been used for multiple studies on the effect of web spam. We have a graph at the host level, and a list of hosts known to be spam.

## Materials

For this assignment we will use the [WEBSPAM-UK2007](http://chato.cl/webspam/datasets/uk2007/) collection. First, we will use a list of host names and a graph of links between hosts. Feel free to decompress these files to inspect them, **but your code must read only these files in compressed form**.

* The list of host names in  [uk-2007-05.hostnames.txt.gz](http://chato.cl/webspam/datasets/uk2007/links/uk-2007-05.hostnames.txt.gz)
* The links between hosts in  [uk-2007-05.hostgraph_weighted.graph-txt.gz](http://chato.cl/webspam/datasets/uk2007/links/uk-2007-05.hostgraph_weighted.graph-txt.gz)

Additionally, we will use these files (uncompressed) that contain labels for the hosts:

* The file `WEBSPAM-UK2007-SET1-labels.txt` inside [webspam-uk2007-set1-1.0.tar.gz](http://chato.cl/webspam/datasets/uk2007/webspam-uk2007-set1-1.0.tar.gz)
* The file `WEBSPAM-UK2007-SET2-labels.txt` inside [webspam-uk2007-set2-1.0.tar.gz](http://chato.cl/webspam/datasets/uk2007/webspam-uk2007-set1-2.0.tar.gz)

## Task

Your task is to compute PageRank twice: first considering all the links, and then ignoring links from or to a known spam host.

## 1. Read hostnames

Read the hostnames from `uk-2007-05.hostnames.txt.gz` without decompressing the file, into a dictionary `id2name`.

```python
with gzip.open(INPUT_HOSTNAMES, "rt", encoding="utf-8") as input_file:
    reader = csv.reader(input_file, delimiter=' ', quotechar='"')
    for record in reader:
        ...
```

Verify:

```python
print(id2name[801])
print(id2name[4778])
N = len(id2name)
print(N)
```

This should print:

```
bacteria.stats.ox.ac.uk
medphoto.wellcome.ac.uk
114529
```

Note that for this to work you must always convert the hostids to numbers, by using `int()`, otherwise they will be strings and would not be usable to address positions in an array.

# 2. Iterate through the graph

Perform `iterations=20` iterations with `alpha=0.85`. In each iteration, you will read the file of the graph, **without loading the entire graph in memory**. This means each iteration involves opening (and implicitly, closing) the file `uk-2007-05.hostgraph_weighted.graph-txt.gz`.

This file has the following structure:

* Line 0 contains the number of nodes, verify this in your code
* Line i contains a space-separated link of outlinks of host `source=i-1`
   * Each outlink is a colon-separated link of `destination:weight`; ignore the weight

Perform the following:

* At the beginning, initialize the vector `pagerank` as 1/N and the vector `pagerank_aux` as 0.
* For `iterations` iterations:
   * Read the graph and for every link from *source* to *destination*:
      * Add to `pagerank_aux[destination]` the value `pagerank[source]/degree`, where *degree* is the out-degree of the source node (i.e, its number of out-links).
   * Set the vector pagerank to *alpha x pagerank_aux + (1-alpha) x (1/N)*.

Remember: do not keep the graph in memory, because that will limit the size of the graphs your code can handle. At every iteration you must read the file again.

# 3. Find the nodes with higher PageRank

You can use the `enumerate()` function which converts a list `[a, b, c]` into `[(0,a), (1,b), (2,c)]` and then `sort()` as follows:

```python
hosts_by_pagerank = sorted(enumerate(pagerank), key=lambda x: x[1], reverse=True)
```

The top-3 commercial hosts (i.e., containing `.co.uk` in their hostname) should be Adobe, the BBC, and the National Rail Service.

# 4. Read a list of spam hosts

Now, read a list of known spam hosts from the files `WEBSPAM-UK2007-SET1-labels.txt` and `WEBSPAM-UK2007-SET1-labels.txt` (merge both lists).

We will consider as spam only the ones that have `spam` next to their host-id.

Read these in a dictionary `is_spam` with keys that are numbers and value `True` to identify spam hosts (ignore the non-spam hosts).

```python
print(len(is_spam))
344
print(is_spam)
{112: True, 322: True, 728: True, ..., 114469: True}
```

# 5. Run non-spam PageRank

Now, run non-spam PageRank. For this, simply ignore any link in which either the source or the destination is a known spam host. You can query this with `if src not in is_spam` and `if dest not in is_spam` (in your code, name `src` the host-id of the source of the link, `dest` the host-id of the destination of the link).

Note that you still have to iterate through the entire file, so even if you know that, e.g., the current line in the file is a spam host, you still have to read that line so the file pointer can advance.

# 6. Compute spam gain

Finally, compute the gain of every host as *(Normal PageRank) / (No spam PageRank)*.

Among the top hosts you might find a mixture of "spammy" (business that tend to rely on spam) and "normal" sites, because spammers also point to legitimate sites to disguise their actions.

# 7. Compute one variant of PageRank

Implement at least one variant of PageRank. Two ideas follow, but feel free to experiment with your own:

1. Restarting to a certain subset of nodes (e.g., .gov.uk or .ac.uk sites)
1. Dividing by log of degree (or some other transformation) instead of degree
1. Ignoring nodes having an anomalously large out-degree

# Deliver (groups of two)

A .zip or .tar.gz file containing your code and report.

The code should contain the Python notebook that you created. In this practice it is important that you **do not duplicate code**. Use functions instead.

The report should contain:

1. The list of top-20 sites by PageRank
1. The list of top-20 sites by No-spam-PageRank
1. Your comment (1-2 paragraphs) on the similarities/differences between the two lists above
1. The list of top-20 sites containing `.co.uk` by PageRank
1. The list of top-20 sites containing `.co.uk` by No-spam-PageRank
1. Your comment (1-2 paragraphs) on the similarities/differences between the two lists above
1. The list of top-20 sites by spam gain
1. Your comment (1-2 paragraphs) on the list of sites by spam gain
1. The list of top-20 sites by your variant of PageRank
1. Your comment (1-2 paragraphs) on the list of top sites by your variant of PageRank

The report should end with the following statement: **We hereby declare that, except for the code provided by the course instructors, all of our code, report, and figures were produced by ourselves.**
