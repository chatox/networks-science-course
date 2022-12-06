# List of theory topics

:construction: These materials should not be considered final until the end of the course. Materials from previous editions can be found in other branches of the repository for the course.

There are 11 theory sessions of 2 hours each. They will all take place face-to-face. Please bring your laptop.

**Before each class, there are short videos you should watch.** They are up to 20 minutes in total, and watching them requires some preparation/scheduling on your part. Please set aside time in your schedule to watch these videos before coming to class, ideally on the day before.

**During class,** I will present the contents using slides and we will do together some exercises using Padlets or Google Spreadsheets. Please avoid distractions: place your phone in airplane mode, close all other windows in your computer, and try to stay focused. We will pause frequently during the session to help you regain focus. In one of the sessions, a *midterm exam* will be taken, and at the end of the course, a *final exam* will be taken. The exam questions are based exclusively on the materials shown or discussed in the lectures during class.

**After each session, there is some reading for you to do.** These readings will be much easier after you have attended each lecture, will bring depth to what you learn in class, and will help you remember these contents better. Think of these readings as a form of continuous studying that will save you time and effort when preparing for the exams.

## Session 1: Introduction

### Before class

* Take a look at the list of [theory topics](./),  [practice sessions](../practicum/README.md), and [evaluation rules](../upf/upf-evaluation.md)

### During class

* Lecture TT01: Complex Networks [odp](odp/tt01-complex_networks.odp)/[pdf](pdf/tt01-complex_networks.pdf)
   * Exercise: find examples of networks (pin board)
* Lecture TT02: applications networks science [odp](odp/tt02-applications_networks_science.odp)/[pdf](pdf/tt02-applications_networks_science.pdf)
* Course overview
   * Overview of [theory topics](./)
   * Overview of [practice sessions](../practicum/README.md)
   * Overview of [evaluation rules](../upf/upf-evaluation.md)
* Lecture TT03: graph theory basics [odp](odp/tt03-graph_theory_basics.odp)/[pdf](pdf/tt03-graph_theory_basics.pdf)
   * Exercise: draw degree distribution (spreadsheet)
   * Exercise: left-project and right-project a graph

### After class

* Read [chapter 2](http://networksciencebook.com/chapter/2) of the book by Barabási
* Read [chapter 0](https://github.com/CambridgeUniversityPress/FirstCourseNetworkScience/tree/master/sample/chapters) of "A first course on network science"

### Optional/additional material

Both of these are great to provide context for the course, and will help you stay motivated. I strongly suggest you set aside some time to watch them within the first 2-3 weeks of the trimester.

* :tv: Watch the 45-minutes documentary [The Emergence of Network Science](https://www.cornell.edu/video/emergence-of-network-science)
* :tv: Watch the one-hour talk "[The Sociological Science Behind Social Networks and Social Influence](https://www.youtube.com/watch?v=wadBvDPeE4E)" by Nicholas Christakis (has subtitles in English).

## Session 2: Distances, homophily, triangles

### Before class

* :tv: Watch the 4-minutes video on [clustering coefficient](https://www.youtube.com/watch?v=YkatiyqHCXk)

### During class

* Lecture TT04: connectivity [odp](odp/tt04-connectivity.odp)/[pdf](pdf/tt04-connectivity.pdf)
   * Quick exercise: find strongly connected components
* Lecture TT05: homophily and triangles [odp](odp/tt05-homophily_triangles.odp)/[pdf](pdf/tt05-homophily_triangles.pdf)
   * Exercise: homophilic, heterophilic, or neutral (pin board)
   * Exercise: compute local clustering coefficients (pin board)
* Lecture TT06: closeness [odp](odp/tt06-closeness.odp)/[pdf](pdf/tt06-closeness.pdf)
   * Exercise: compute closeness and harmonic closeness (spreadsheet)

### After class

* :tv: Watch this 6-minutes video on [Why we prefer people just like us, and why that's potentially dangerous](https://www.youtube.com/watch?v=O7CJBnGkqEk) by Nicholas Christakis

## Session 3: Betweenness, hubs, and authorities

### Before class

* :tv: Watch this 5-minutes [explanation of network centrality measures](https://www.youtube.com/watch?v=NgUj8DEH5Tc)
* :tv: Watch the first 15-minutes of this 26-minutes video on [degree, betweenness, and closeness as centrality measures](https://www.youtube.com/watch?v=RXohUeNCJiU&list=PL2rR6Wa-StjYOW7v6J8_npck6EDOKEbCN&index=7) by Lada Adamic. The first half of the video is about degree, the second half about betweenness and closeness.
* :tv: Watch the 12-minutes [explanation of Hubs and Authorities](https://www.youtube.com/watch?v=-kiKUYM9Qq8) by Daniel Romero
   * *Or* watch the 15-minutes [explanation of Hubs and Authorities](https://www.youtube.com/watch?v=zydSN8C1Et4) by Jure Leskovec

### During class

* Lecture TT07: betweenness [odp](odp/tt07-betweenness.odp)/[pdf](pdf/tt07-betweenness.pdf)
   * Exercise: compute node betweenness (pin board)
   * Exercise: run the Brandes and Newman algorithm for betweenness
* Lecture TT08: hubs and authorities [odp](odp/tt08-hubs_authorities.odp)/[pdf](pdf/tt08-hubs_authorities.pdf) -- In 2022 we finished the computation, moved rest to next session
   * Exercise: compute hub and authority scores iteratively (spreadsheet)

### After class

* :tv: Watch the rest of the 26-minutes video on [degree, betweenness, and closeness as centrality measures](https://www.youtube.com/watch?v=RXohUeNCJiU&list=PL2rR6Wa-StjYOW7v6J8_npck6EDOKEbCN&index=7) by Lada Adamic. The first half of the video is about degree, the second half about betweenness and closeness.
* Read sections 10.2.3 on betweenness and 10.2.4 on the Girvan-Newman algorithm in [Mining Massive Datasets](http://infolab.stanford.edu/~ullman/mmds/book.pdf)
* Read section 3.6 on betweenness and graph partitioning of [chapter 3](http://www.cs.cornell.edu/home/kleinber/networks-book/networks-book-ch03.pdf) of the book by Easley and Kleinberg

## Session 4: PageRank and case study

### Before class

* :tv: Watch this 5-minutes [animation explaining PageRank](https://www.youtube.com/watch?v=meonLcN7LD4)

### During class

* Lecture TT09: pagerank [odp](odp/tt09-pagerank.odp)/[pdf](pdf/tt09-pagerank.pdf)
   * Exercise: compute simplified PageRank (spreadsheet)
* Lecture TT10bis: case study on centrality [odp](odp/tt10bis-centrality_case_study.odp)/[pdf](pdf/tt10bis-centrality_case_study.pdf) - [notebook](../practicum/data/case-study-florentine)

### After class

* Read the [chapter 14](http://www.cs.cornell.edu/home/kleinber/networks-book/networks-book-ch14.pdf) of the book by Easley and Kleinberg
* :tv: Watch the (10-minutes each) lessons on PageRank [2.5](https://www.youtube.com/watch?v=bK934gcJMS4), [2.6](https://www.youtube.com/watch?v=Nvb1WVWoYt4) by Jure Leskovec
* :tv: Watch the lessons [matrix formulation of PageRank](https://www.youtube.com/watch?v=e2SZY3NbtQ8) and [PageRank and random walks](https://www.youtube.com/watch?v=CWzmnzB04eg) by Jure Leskovec

### Extra content: more on PageRank

* Lecture TT10: pagerank extra material [odp](odp/tt10-pagerank_extra.odp)/[pdf](pdf/tt10-pagerank_extra.pdf)

## Session 5: Mid-term exam (Friday, October 21st, 2022)

### Before class

Study on your own, try to solve exams from past years. Ask your questions in the forum.

### During class

We will have a mid-term exam; there will be no lecture after the exam. The topics for the exam will be TT01-TT09, TT10bis.

## Session 6: Random networks (ER model)

### Before class

* :tv: Watch the 17-minutes video on [the ER random graph model](https://www.youtube.com/watch?v=3PxteAgVf0o) by Lada Adamic (has subtitles in English)

### During class

* Lecture TT11: the random network (ER) model [odp](odp/tt11-random_networks.odp)/[pdf](pdf/tt11-random_networks.pdf)
   * Exercise: guess the formula for expected number of links, using NetLogo to run simulations (pin board)
   * Exercise: compute expected number of links and expected average degree
* Lecture TT12: properties of random networks [odp](odp/tt12-random_networks_properties.odp)/[pdf](pdf/tt12-random_networks_properties.pdf) -- In 2022 we arrived until Wikipedia speedruns, rest moved to the next session
   * Exercise: guess critical point at which a giant connected component emerges, using NetLogo to run simulations (pin board)
   * Exercise: find actors with large distance from Kevin Bacon (pin board)
   * Exercise: find critical N for a graph to be connected

### After class

* Read [chapter 3](http://networksciencebook.com/chapter/3) of the book by Barabási

## Session 7: Scale-free Networks

### Before class

* :tv: Watch this 20-minutes [video on Zipf, Pareto, and power laws](https://www.youtube.com/watch?v=ViUqxEF4plA&list=PL2rR6Wa-StjYOW7v6J8_npck6EDOKEbCN&index=10) by Lada Adamic. It is a great explanation of a phenomenon that goes well beyond networks.

### During class

* Lecture TT13: scale-free networks [odp](odp/tt13-scale_free_networks.odp)/[pdf](pdf/tt13-scale_free_networks.pdf)
   * Exercise: compute nodes with an expected degree
* Lecture TT14: distances in scale-free networks [odp](odp/tt14-distances_scale_free_nets.odp)/[pdf](pdf/tt14-distances_scale_free_nets.pdf) -- In 2022 the timeslot was short, so we moved this to the next class

### After class

* Read the [chapter 4](http://networksciencebook.com/chapter/4) of the book by Barabási

### Optional/additional material

* If you are not sure whether you understood the friendship paradox or not, or if you want to learn more about it, watch this [half-hour explanation of the friendship paradox](https://www.youtube.com/watch?v=7ffzDepERnQ)

## Session 8: Preferential attachment

### Before class

* :tv: Watch the 13-minutes video on [preferential attachment](https://www.youtube.com/watch?v=hgrJCBmdjws) from a course on fractals and scaling

### During class

* Lecture TT16: preferential attachment [odp](odp/tt16-preferential_attachment.odp)/[pdf](pdf/tt16-preferential_attachment.pdf)
   * Exercise: guess slope of degree distribution, using NetLogo to run simulations (pin board)
   * Exercise: write formula for number of nodes and edges over time
* Lecture TT17: degree under preferential attachment [odp](odp/tt17-preferential_attachment_degree.odp)/[pdf](pdf/tt17-preferential_attachment_degree.pdf)
* Lecture TT15: the friendship paradox [odp](odp/tt15-friendship_paradox.odp)/[pdf](pdf/tt15-friendship_paradox.pdf)
   * Exercise: numerical example of friendship paradox (pin board)
   * Exercise: compute expected degree of neighbors

### After class

* Read the [chapter 5](http://networksciencebook.com/chapter/5) of the book by Barabási

### Optional/additional material

* Lecture TT18: other growth models [odp](odp/tt18-other_growth_models.odp)/[pdf](pdf/tt18-other_growth_models.pdf)
   * Exercise: copy model

## Session 9: Communities

### Before class

* :tv: Watch this 10-minutes video on [k-core decomposition](https://www.youtube.com/watch?v=rHVrgbc_3JA)
* :tv: Watch the 10-minutes lecture on [why detecting communities](https://www.youtube.com/watch?v=INR0N3nA8uU&list=PL2rR6Wa-StjYOW7v6J8_npck6EDOKEbCN&index=12) by Lada Adamic

### During class

* Lecture TT19: k-cores [odp](odp/tt19-k_cores.odp)/[pdf](pdf/tt19-k_cores.pdf)
   * Exercise: perform a k-core decomposition
* Lecture TT20: community structure [odp](odp/tt20-community_structure.odp)/[pdf](pdf/tt20-community_structure.pdf)
* Lecture TT21: finding communities [odp](odp/tt21-finding_communities.odp)/[pdf](pdf/tt21-finding_communities.pdf)
   * Exercise: indicate if communities are strong or weak
   * Exercise: compute cut size under two different partitions (pin board)
   * Exercise: compute modularity

### After class

* Read the [sections 9.1 and 9.2](http://networksciencebook.com/chapter/9) of the book by Barabási

### Optional/additional material

* Read [sections 1 and 2 of this paper on the k-core decomposition](https://link.springer.com/article/10.1007/s00778-019-00587-4) -- do not worry if you cannot follow all details

## Session 10: Spectral graph clustering

### Before class

* :tv: Watch the lessons on [graph Laplacian](https://www.youtube.com/watch?v=Cedjf9G0otE) and [spectral graph partitioning](https://www.youtube.com/watch?v=siCPjpUtE0A) by Jure Leskovec

### During class

* Lecture TT22: spectral graph embedding [odp](odp/tt22-spectral_graph_embedding.odp)/[pdf](pdf/tt22-spectral_graph_embedding.pdf)
   * Exercise: perform random 2D projection of a graph

### After class

* :tv: Watch the lesson on [partitioning in three or more communities](https://www.youtube.com/watch?v=siCPjpUtE0A) by Jure Leskovec at Stanford

### Optional/additional materials

* :tv: Watch the lessons on [heuristics for finding communities](https://www.youtube.com/watch?v=yz0oIMHOz_8&list=PL2rR6Wa-StjYOW7v6J8_npck6EDOKEbCN&index=13), and [community finding algorithms](https://www.youtube.com/watch?v=MLmpyL1NdCs&list=PL2rR6Wa-StjYOW7v6J8_npck6EDOKEbCN&index=14) by Lada Adamic
* :tv: Watch the lessons on [detecting communities as clusters](https://www.youtube.com/watch?v=c0_vNfNZ4JM) and [what makes a good clustering](https://www.youtube.com/watch?v=zLuVrqlYKyg) by Jure Leskovec at Stanford

## Session 11: Spreading Phenomena

### Before class

* :tv: Watch this 10 minutes [crash course on social influence](https://www.youtube.com/watch?v=UGxGDdQnC1Y) explaining some psychology concepts related to influence
* :tv: Watch this 7 minutes [overview of network diffusion elements](https://www.youtube.com/watch?v=bTXUJQhEqL0)
* :tv: Watch this 13-minutes [infection simulations](https://www.youtube.com/watch?v=7OLpKqTriio)

### During class

* Lecture TT23: spreading phenomena [odp](odp/tt23-spreading_phenomena.odp)/[pdf](pdf/tt23-spreading_phenomena.pdf)
   * Exercise: explain three contagion variants, using NetLogo to run simulations (pin board)
   * Exercise: indicate phenomena that spread virally (pin board)
* Lecture TT24: models of influence [odp](odp/tt24-models_of_influence.odp)/[pdf](pdf/tt24-models_of_influence.pdf)
   * Exercise: simulate linear threshold model (spreadsheet)
   * Exercise: simulate independent cascade model (spreadsheet)
   * Exercise: list assumptions of these models (pin board)

### After class

* Read [chapter 10](http://networksciencebook.com/chapter/10) of the book by Barabási
* Read [chapter 19](http://www.cs.cornell.edu/home/kleinber/networks-book/networks-book-ch19.pdf) of the book by Easley and Kleinberg
* Read [chapter 21](http://www.cs.cornell.edu/home/kleinber/networks-book/) of the work by Easley and Kleinberg
* :tv: Watch this 24-minutes [explanation of the mathematics of the SIR model for COVID](https://www.youtube.com/watch?v=NKMHhm2Zbkw)

### Optional/additional material

* Lecture TT25: epidemics [odp](odp/tt25-epidemics.odp)/[pdf](pdf/tt25-epidemics.pdf)

## Final Exam

The final exam will include the random network model (TT11-TT12), scale-free networks (TT13-TT14), the preferential attachment model (TT15-T17), community detection (TT19-TT21), spectral methods (TT22), and spreading phenomena (TT23-TT24). This excludes decks not seen in class, optional/additional slide decks, and slides marked "Extra".

# Notes

These slides are made with LibreOffice and the [TexMaths](https://extensions.libreoffice.org/extensions/texmaths-1) extension, which allows to easily enter and edit LaTeX equations that are embedded as images in the slides.

Note that the source files include some solutions, while the PDF files do not include them. Use this while studying: do not look at the solutions until you have tried to solve the problem yourself.

# Sources/credits

Some theory topics closely follow the "[Networks Science](http://networksciencebook.com/)" book (2016) and course by Albert-László Barabási. In all cases, the sources are indicated either at the beginning or in the footer of the slides. Please feel free to use, copy, and adapt contents from these slides for whatever purposes, giving proper attribution.

[<img src="../upf/cc-by-80x15.png" width="80" height="15" hspace="4"/>](https://creativecommons.org/licenses/by/4.0/) Slides available under a [Creative Commons](https://creativecommons.org/licenses/by/4.0/) license unless specified otherwise.
