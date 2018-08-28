# Practice Session 04: Python data management

In this session we will study an application of complex networks analysis to medicine. We will start with the *diseasome*, a bi-partite network connecting all known genetic diseases (by 2005) with genes whose mutations re implicated in that disease.

The initial dataset `disease-genes.csv` contains the following columns:

1. A disorder *ID*
2. A disorder *Name*
3. A comma-separated list of *Genes*
4. The *OMIM ID* (Online Mendelian Inheritance in Man) of this disorder
5. The location in the *Chromosome*
6. A disorder *Class* indicating the physiological system that is affected

# 0. Elements that you may need

Here are some code snippets that you may need.

## Reading a CSV file

FILENAME should be a string containing the name of the file you're opening. The comma is the field delimiter, and the quote character is the character that is used to protected values that contain commas.

```python
disorders = []
with io.open(FILENAME) as file:
    reader = csv.DictReader(file, delimiter=',', quotechar='"')
    for row in reader:
        disorders.append(row)
```

Now the list `disorders` contains a list of dictionaries. Each dictionary is a disease.

Remember to `import io` and `import csv` for this code to work.

## Split a string and iterate on its parts

If you want to split a string into pieces, you can use the following. Suppose the variables `genes` contains a comma-separated list such as `CYP17A1, CYP17, P450C17`:

```python
gene_list = genes.split(",")
for gene in gene_list:
    gene = gene.strip()
    ...
```

The `str.strip()` method removes whitespace and newlines from the beginning and end of the string, so it's equivalent to `str.lstrip().rstrip()`.

You can also do this in one line of code, using the `map(f, v)` function, which results the result of applying function `f` to each element of list `v`:

```python
gene_list = list(map(str.strip, disorder["Genes"].split(',')))
```

## Intersection of two lists

There are many ways of intersecting two lists in Python, one of the simplest ones is to convert them to sets, and then computing the set intersection using the built-in `&` operator:

```python
def intersection(list1, list2):
    return(list(set(list1) & set(list2)))
```

If you want to test if two lists have elements in common, you can check the length of its intersection (there are other ways). Remember the length of a list is obtained with `len()`:

```python
if len(intersection(list1,list2)) > 0:
    ...
```

## Create a file

We will create tab-separated files to avoid confusing Cytoscape, we will also include a header with the names of the columns.

```python
with io.open(FILEOUT_NAME, "w") as fileout:
    writer = csv.writer(fileout, delimiter='\t', quotechar='"')
    writer.writerow(["name1", "name2", "name3"])
    for disorder in disorders:
        ...
        writer.writerow([value1, value2, value3])
```

Remember to create a variable `FILEOUT_NAME` with the name of the output file you want to create. Create clean code: define the file name and then use it, don't replace `FILEOUT_NAME` by a string constant inside the call to `open()`.

# 1. Draw the diseasome bi-partite graph

## Create a diseasome.csv file

Create an IPython notebook that can create this tab-separated file. Store it as `diseasome.csv`:

    disorder          class       gene
    17,20-lyase ...   Endocrine   CYP17A1
    17,20-lyase ...   Endocrine   CYP17
    17,20-lyase ...   Endocrine   P450C17
    ...

## Import this file in Cytoscape

Remember these files are imported with "File > Import > Network > File ..." and you must select "tab" as the separator in the advanced options. Then, you have to select disorder as a "Source Node", gene as a "Target Node" and class as a "Source Node Attribute".

## Draw this graph

Select the largest connected component of the graph (maintain "shift" pressed while you draw a rectangle around it). Then, create a new graph with the selection (File > New > Network > From selected nodes, all edges).

Draw this sub-graph with ellipses/ovals as nodes, and color the nodes according to the class of disease (Style/Node, Fill Color on Column "class", Discrete Mapping). Do not color all of them, just a few classes. What is the dominant type of disease in this component?

# 2. Draw the disease-disease graph

The bi-partite diseasome is hard to visualize as it mixes diseases and genes. We will now try to visualize only the connections between diseases.

## Create a disease-disease.csv file

The following code lists all the diseases that have at least one gene in common:

```python
for disorder1 in disorders:
    gene_list_1 = ...
    for disorder2 in disorders:
        if disorder2["Name"] != disorder1["Name"]:
            gene_list_2 = ...
            common_genes = intersection(gene_list_1, gene_list_2)
            if len(common_genes) > 0:
                print("Diseases '%s' and '%s' have genes in common" % (disorder1["Name"], disorder2["Name"]))
```

Modify this code to generate a tab-separated file like this one:

    disease1    disease2   ngenes1 ngenes2  class1     class2
    17-alpha... 17,20...    3      3        Endocrine  Endocrine
    3-methyl... Optic ...   2      2        Metabolic  Ophthamological
    Aarskog...  Mental...   3      3        multiple   Neurological
    ...

Where `ngenes1` and `ngenes2` correspond to `len(gene_list_1)` and `len(gene_list_2)` respectively.

If you want to avoid having double edges, change the condition `disorder1["Name"] != disorder2["Name"]` from `!=` (different) to `>` (greater than).

## Import this file into Cytoscape

To import this file remember to select the advanced options of the import, and select tab (and only tab) as the separator.

Now, for the columns you have to indicate their role, and rename the attribute columns so that Cytoscape knows when they are the same attribute.

1. `disease1`: Source Node
2. `disease2`: Target Node
3. `ngenes1`: Source Node Attribute - rename to "num_genes"
4. `ngenes2`: Target Node Attribute - rename to "num_genes"
5. `class1`: Source Node Attribute - rename to "class"
6. `class2`: Target Node Attribute - rename to "class"

## Style and add simple annotations

Use ellipses/ovals as node shapes, with sizes representing the number of genes associated to each disease.

Color the nodes by default gray, and with colors representing the class of diseases (leave "Unclassified" and "multiple" as gray).

Add text annotations (secondary button > add > text annotation) to the first, second, and third largest connected component, with your observations (e.g., "The second largest component is dominated by diseases of type x"). Place the annotations next to the components they refer to (secondary button > edit > move annotation).

# DELIVER (individually)

At the end of the session, deliver a one-page report in PDF containing an image of the disease-disease network you created, styled, and annotated.

## Extra points available

For extra points, group different variants of a disease, which are indicated by the presence of a comma (e.g., "Epilepsy, progressive myoclonic 2B" would be just "Epilepsy"). Note that there should be a single node per disease (i.e., just one "Epilepsy") and this node should contain the union of all genes of the different variants of this disease. Hence, two diseases will be connected if any of their variants have a gene in common.

**Note 0:** if you go for the extra points, add "Diseases are grouped" as a text annotation at the top of your deliverable.

**Note 1:** a list `c` that is the union of two lists `a,b` can be computed in Python with `c = list(set(a) | set(b))`.

**Note 2:** if you go for the extra points, you have 24 hours after the end of this session to deliver. If later you deliver just the standard solution (without grouping), the standard penalty for late delivery will apply.

# References

Goh, K. I., Cusick, M. E., Valle, D., Childs, B., Vidal, M., & Barabási, A. L. (2007). [The human disease network](http://www.pnas.org/content/104/21/8685). Proceedings of the National Academy of Sciences, 104(21), 8685-8690.
