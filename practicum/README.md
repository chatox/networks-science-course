# Practicum

## Software requirements

You will need:

* [**Cytoscape**](https://cytoscape.org/download.html) (version 3.10 or higher)
   * The [ClusterMaker2 plug-in](https://apps.cytoscape.org/apps/clustermaker2) for Cytoscape
* **Python 3.11** or higher
   * You can use the [Anaconda](https://www.anaconda.com/products/individual) package manager.
   * If you prefer, you can also use the [`pip`](https://packaging.python.org/en/latest/tutorials/installing-packages/) package manager and Python's built-in [virtual environments](https://docs.python.org/3/library/venv.html).
* Several Python **packages**
   * [networkx](https://networkx.github.io/) — **version 3.5 or higher!**
   * [matplotlib](https://matplotlib.org/)
   * [numpy](https://numpy.org/)
   * [scipy](https://scipy.org/)
* **Jupyter Notebooks**
   * Follow [these instructions](https://jupyter.org/install.html).

Feel free to install the packages on your own, any relevant versions are mentioned above. If you want to be sure you have all the correct versions, you can install using the requirements files provided in this directory:
* `requirements.txt` — can be used with `pip`, see [instructions](https://packaging.python.org/en/latest/tutorials/installing-packages/#requirements-files).
* `environment.yaml` — can be used with `conda`, see [instructions](https://docs.conda.io/projects/conda/en/stable/user-guide/tasks/manage-environments.html#creating-an-environment-from-an-environment-yml-file).

:warning: Please, if you run into problems installing this software, **ask your classmates or in the course forum**. Please do not ask the practice instructors, they absolutely do not have the bandwidth for this.

## Practice sessions

Practice sessions are conducted with a computer.

There are eight practice sessions in this course. The first session's handout is a document, the remaining sessions have handouts that are Python notebooks. Download the notebooks, open them, and follow the instructions there (some instructions are in color and are not visible in the preview shown on the GitHub website). Each session starts with *psNN* and describe the activities that the students must perform during the practice session.

At the end of each handout there is a description of what you should deliver. Please ask in the course forum or to your practice instructor ("*profesor/a de prácticas*") any questions you may have.

**Deadline**

You are expected to deliver your work within the deadline. Deadlines vary: some practices may be delivered several days after the practice sessions, other are expected to be delivered **at the end of the session**, i.e., you will have to complete them within the two hours.


| # | Handouts                                    | Contents | Session Date <br> 101/102 | Deadline <br> 101/102 | Session Date <br> 201 |  Deadline <br> 201 |
|---|---------------------------------------------|----------|------------------|--------------|------------------|--------------|
| 1 | [PS01](ps01-cytoscpe.md)                          | Cytoscape: editing, visualizing, creating, importing and editing networks | Oct. 3rd, 16:30 | Oct. 10th, 16:30 |  Oct. 6th, 18:30 | Oct. 13th, 18:30 |
| 2 | [PS02](ps02-flavors-2025.ipynb)                  | NetworkX and Cytoscape: the flavors network (Management networks data)| Oct. 10th, 16:30 | Oct. 17th, 16:30 | Oct. 13th, 18:30 | Oct. 20th, 18:30 |
| 3 | [PS03](ps03-networks-from-text.ipynb)       | NetworkX: networks from text and networkx visualization | Oct. 14th, 14:30 | Oct. 20th, 14:30 | Oct. 16th, 14:30 | Oct. 22nd, 14:30 |
| 4 | PS04 (Group 1, [Group 2](ps04-weighted_networks-2025V1.ipynb))         | NetworkX: weighted networks | Oct. 21st, 14:30 | Oct. 21st, 16:30  | Oct. 17th, 14:30 | Oct. 17th, 16:30 |
| 5* | PS01-PS04                             | Wrap-up | Oct. 16th, 18:30 | ----- | Oct. 24th, 14:30 | ----- |
| 6 | [PS05](ps05-pagerank.ipynb)                 | NetworkX: PageRank | Oct. 15th, 16:30 | Oct. 22nd, 16:30 | Nov. 6th, 14:30 | Nov. 11th, 14:30 |
| 7 | PS06           | NetworkX: network models | Nov. 4th, 14:30 | Nov. 7th, 14:30 | Nov. 7th, 14:30 | Nov. 12th, 13:30 |
| 8 | PS07        | NetworkX: k-cores | Nov. 14th, 16:30 | Nov. 14th, 18:30 | Nov. 17th, 18:30 | Nov. 17th, 20:30 |
| 9 | PS08              | NetworkX: community detection | Nov. 21st, 16:30 | Nov. 26th, 16:30 | Nov. 24th, 18:30 | Nov. 27th, 18:30 |
| 10* | PS05-PS08                            | Wrap-up | Nov. 25th, 14:30 | ----- | Nov. 27th, 14:30 | -----
| 11* | Old exams                                 | Old exams review | Nov. 26th, 16:30 | ----- | Nov. 28th, 14:30 | -----

\* Participation in wrap-up sessions (#5, #10) and session #11 is **optional**.

## Tutorials/reference

### Cytoscape

* [Cytoscape 8-minutes video tutorial](https://www.youtube.com/watch?v=iGpxX0Kd4Z0&list=PLFQS98nmv__wFmmSDePx9FtQ2TFRS6wdR)
* [Cytoscape tutorial](https://github.com/cytoscape/cytoscape-tutorials/wiki)
* [Emma Towlson's slides](https://www.dropbox.com/s/37zleq3ynw6e0n6/Cytoscape_2017.pdf?dl=0) (old Cytoscape version)

### NetworkX

* [Complex Network Analysis in Python](https://www.amazon.com/gp/product/1680502697/) (2018) by Dmitry Zinoviev. **Also [available as an e-book](https://upfinder.upf.edu/iii/encore/record/C__Rb1557007?lang=cat) for UPF students.**
* [NetworkX documentation](https://networkx.github.io/)
* [Social network analysis with NetworkX](https://blog.dominodatalab.com/social-network-analysis-with-networkx/) by Manojit Nandi
* [NetworkX: Network analysis with Python](https://www.cl.cam.ac.uk/~cm542/teaching/2010/stna-pdfs/stna-lecture8.pdf) by Salvatore Scellato
