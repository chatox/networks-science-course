# List of theory topics

There are 12 theory sessions of 2 hours each. They will all take place face-to-face. Please bring your laptop. One theory session is devoted to the mid-term exam (see below). 

:construction: These materials should not be considered final until the end of the course. Theory sessions from 6 to 12 will be uploaded after the mid-term exam.

**Before each class, there are short videos you should watch.** They are up to 20 minutes in total, and watching them requires some preparation/scheduling on your part. Please set aside time in your schedule to watch these videos before coming to class, ideally on the day before.

**During class,** I will present the contents using slides and we will do together some exercises using Padlets or Google Spreadsheets, or on the blackboard. 

**After each session, there is some reading for you to do.** These readings will be much easier after you have attended each lecture, will bring depth to what you learn in class, and will help you remember these contents better. Think of these readings as continuous studying that will save time and effort when preparing for the exams.

**Exams.** After four sessions, a *midterm exam* will be taken. At the end of the course, a *final exam* will be taken. The exam questions are based exclusively on the materials shown or discussed in the lectures during class. No laptops or phones will be allowed.


## Session 1: Why studying Network Science

### Before class

* Take a look at the list of [theory topics](./),  [practice sessions](../practicum/README.md), and [evaluation rules](../upf/upf-evaluation.md)

### During class

* Lecture TT01: Introduction to Networks [pdf](pdf/tt01-intro.pdf)
   * :tv: First minute of [The hidden networks of everything](https://www.youtube.com/watch?v=RfgjHoVCZwU)
   * Exercise: find examples of networks (pin board)
* Course overview
   * Overview of [theory topics](./)
   * Overview of [practice sessions](../practicum/README.md)
   * Overview of [evaluation rules](../upf/upf-evaluation.md)
* Lecture TT02: Basics of Graph Theory [pdf](pdf/tt02-basics.pdf)
   * Exercise: draw degree distribution (spreadsheet)
   * Exercise: left-project and right-project a graph

### After class

* Read [chapter 2](http://networksciencebook.com/chapter/2) of the book by Barabási
* Read [chapter 0](https://github.com/CambridgeUniversityPress/FirstCourseNetworkScience/tree/master/sample/chapters) of "A first course on network science"

### Optional/additional material

Both of these are great to provide context for the course, and will help you stay motivated. I strongly suggest you set aside some time to watch them within the first 2-3 weeks of the trimester.

* :tv: Watch the 45-minutes documentary [The Emergence of Network Science](https://www.cornell.edu/video/emergence-of-network-science)
* :tv: Watch the one-hour talk "[The Sociological Science Behind Social Networks and Social Influence](https://www.youtube.com/watch?v=wadBvDPeE4E)" by Nicholas Christakis (has subtitles in English).


## Session 2: We live in a small world

### Before class

* :tv: Watch this 9-minutes video about [The Science of Six Degrees of Separation](https://www.youtube.com/watch?v=TcxZSmzPw8k)
* :tv: Watch this 5-minutes video of [explanation of network centrality measures](https://www.youtube.com/watch?v=NgUj8DEH5Tc)

### During class

* Lecture TT03: Connectivity in Graph Theory [pdf](pdf/tt03-connectivity.pdf)
   * Quick exercise: find strongly connected components
* Lecture TT04: Centrality in Graph Theory [pdf](pdf/tt04-centrality.pdf)
   * Exercise: compute closeness and harmonic closeness (spreadsheet)
   * Exercise: compute node betweenness (pin board)
   * Exercise: run the Brandes and Newman algorithm for betweenness

### After class

* :tv: Watch the first 15-minutes of this 26-minutes video on [degree, betweenness, and closeness as centrality measures](https://www.youtube.com/watch?v=RXohUeNCJiU&list=PL2rR6Wa-StjYOW7v6J8_npck6EDOKEbCN&index=7) by Lada Adamic. The first half of the video is about degree, the second half about betweenness and closeness.
* Read sections 10.2.3 on betweenness and 10.2.4 on the Girvan-Newman algorithm in [Mining Massive Datasets](http://infolab.stanford.edu/~ullman/mmds/book.pdf)
* Read section 3.6 on betweenness and graph partitioning of [chapter 3](http://www.cs.cornell.edu/home/kleinber/networks-book/networks-book-ch03.pdf) of the book by Easley and Kleinberg


## Session 3: Friends will be friends

### Before class

* :tv: Watch the 1-minutes video on the [Friendship Paradox](https://www.youtube.com/watch?v=httLvVufAYs)
* :tv: Watch the 4-minutes video on [clustering coefficients](https://www.youtube.com/watch?v=YkatiyqHCXk)

### During class

* Lecture TT05: Degree Correlations in Graph Theory [pdf](pdf/tt05-assortativity.pdf)
   * Exercise: average nearest neighbors' degree in uncorrelated networks (blackboard)
* Lecture TT06: Clustering and Homophily in Graph Theory [pdf](pdf/tt06-clustering.pdf)
   * Exercise: compute local clustering coefficients (pin board)
   * Exercise: homophilic, heterophilic, or neutral (pin board)

### After class

* :tv: Watch this 6-minutes video on [Why we prefer people just like us, and why that's potentially dangerous](https://www.youtube.com/watch?v=O7CJBnGkqEk) by Nicholas Christakis

### Optional/additional material

* If you are not sure whether you understood the friendship paradox or not, or if you want to learn more about it, watch this [half-hour explanation of the friendship paradox](https://www.youtube.com/watch?v=7ffzDepERnQ)

  
## Session 4: PageRank and case study

### Before class

* :tv: Watch this 5-minutes [animation explaining PageRank](https://www.youtube.com/watch?v=meonLcN7LD4)

### During class

* Lecture TT07: PageRank [pdf](pdf/tt07-pagerank.pdf)
   * Exercise: compute simplified PageRank (spreadsheet)
* Lecture TT08: Case study on centrality [pdf](pdf/tt08-casestudy.pdf) - [notebook](../practicum/data/case-study-florentine)

### After class

* Read the [chapter 14](http://www.cs.cornell.edu/home/kleinber/networks-book/networks-book-ch14.pdf) of the book by Easley and Kleinberg
* :tv: Watch the (10-minutes each) lessons on PageRank [2.5](https://www.youtube.com/watch?v=bK934gcJMS4), [2.6](https://www.youtube.com/watch?v=Nvb1WVWoYt4) by Jure Leskovec
* :tv: Watch the lessons [matrix formulation of PageRank](https://www.youtube.com/watch?v=e2SZY3NbtQ8) and [PageRank and random walks](https://www.youtube.com/watch?v=CWzmnzB04eg) by Jure Leskovec

## Session 5: Mid-term exam (October 22nd, 2025, 16:30)

### Before class

Study on your own, try to solve exams from past years. 

### During class

We will have a mid-term exam; there will be no lecture after the exam. The topics for the exam will be from lectures TT01-TT07.

## Session 6: Modelling homogeneous networks

### Before class

* :tv: Watch the 17-minutes video on [the ER random graph model](https://www.youtube.com/watch?v=3PxteAgVf0o) by Lada Adamic (has subtitles in English)

### During class

* Lecture TT09: The Erdos Renyi (ER) network model [pdf](pdf/tt09-ERmodel.pdf)
   * Exercise: guess the formula for the expected number of links
   * Exercise: compute the expected number of links and expected average degree
* Lecture TT10: Properties of ER networks [pdf](pdf/tt10-ERproperties.pdf)
   * Exercise: guess the critical point at which a giant connected component emerges
   * Exercise: find critical N for a graph to be connected

### After class

* Read [chapter 3](http://networksciencebook.com/chapter/3) of the book by Barabási

## Session 7: Scale-free Networks

### Before class

* :tv: Watch this 20-minutes [video on Zipf, Pareto, and power laws](https://www.youtube.com/watch?v=ViUqxEF4plA&list=PL2rR6Wa-StjYOW7v6J8_npck6EDOKEbCN&index=10) by Lada Adamic. It is a great explanation of a phenomenon that goes well beyond networks.

### During class

* Lecture TT11: Scale-free (SF) networks [pdf](pdf/tt11-SFnetworks.pdf)
   * Exercise: compute nodes with an expected degree
* Lecture TT12: Distances in SF networks [pdf](pdf/tt12-distancesSFnets.pdf)
   * Exercise: compare average distances estimators for some networks

### After class

* Read the [chapter 4](http://networksciencebook.com/chapter/4) of the book by Barabási


## Session 8: Modelling heterogeneous networks

### Before class

* :tv: Watch the 13-minutes video on [preferential attachment](https://www.youtube.com/watch?v=hgrJCBmdjws) from a course on fractals and scaling

### During class

* Lecture TT13: Network models: Barabasi-Albert networks [pdf](pdf/tt13-BAmodel.pdf)
   * Exercise: write formula for number of nodes and edges over time
* Lecture TT14: Network models: Properties of BA networks [pdf](pdf/tt14-propertiesBAnetworks.pdf)

### After class

* Read the [chapter 5](http://networksciencebook.com/chapter/5) of the book by Barabási


## Session 9: Communities

### Before class

* :tv: Watch this 10-minutes video on [k-core decomposition](https://www.youtube.com/watch?v=rHVrgbc_3JA)
* :tv: Watch the 10-minutes lecture on [why detecting communities](https://www.youtube.com/watch?v=INR0N3nA8uU&list=PL2rR6Wa-StjYOW7v6J8_npck6EDOKEbCN&index=12) by Lada Adamic

### During class

* Lecture TT15: Community structure [pdf](pdf/tt15-community_structure.pdf)
   * Exercise: perform a k-core decomposition
   * Exercise: indicate if communities are strong or weak
   * Exercise: compute cut size under two different partitions (pin board)
* Lecture TT16: Community detection [pdf](pdf/tt16-community_detection.pdf)
   * Exercise: compute modularity
   * Exercise: invent a variant of the ER model that generates graphs having two communities

### After class

* Read the [sections 9.1 and 9.2](http://networksciencebook.com/chapter/9) of the book by Barabási

### Optional/additional material

* Read [sections 1 and 2 of this paper on the k-core decomposition](https://link.springer.com/article/10.1007/s00778-019-00587-4) -- do not worry if you cannot follow all details

## Session 10: Spectral graph embedding

### Before class

* :tv: Watch the lessons on [graph Laplacian](https://www.youtube.com/watch?v=Cedjf9G0otE) and [spectral graph partitioning](https://www.youtube.com/watch?v=siCPjpUtE0A) by Jure Leskovec

### During class

* Lecture TT17: spectral graph theory [pdf](pdf/tt17-spectral_graph_theory.pdf)
   * Exercise: perform random 2D projection of a graph
* Lecture TT18: spectral graph embedding [pdf](pdf/tt18-spectral_graph_embedding.pdf)
   * Exercise: spectral projection of a graph

### After class

* :tv: Watch the lesson on [partitioning in three or more communities](https://www.youtube.com/watch?v=siCPjpUtE0A) by Jure Leskovec at Stanford

### Optional/additional materials

* :tv: Watch the lessons on [heuristics for finding communities](https://www.youtube.com/watch?v=yz0oIMHOz_8&list=PL2rR6Wa-StjYOW7v6J8_npck6EDOKEbCN&index=13), and [community finding algorithms](https://www.youtube.com/watch?v=MLmpyL1NdCs&list=PL2rR6Wa-StjYOW7v6J8_npck6EDOKEbCN&index=14) by Lada Adamic
* :tv: Watch the lessons on [detecting communities as clusters](https://www.youtube.com/watch?v=c0_vNfNZ4JM) and [what makes a good clustering](https://www.youtube.com/watch?v=zLuVrqlYKyg) by Jure Leskovec at Stanford


## Session 11: Social Dynamics

### Before class

* :tv: Watch this 10 minutes [crash course on social influence](https://www.youtube.com/watch?v=UGxGDdQnC1Y) explaining some psychology concepts related to influence
* :tv: Watch this 7 minutes [overview of network diffusion elements](https://www.youtube.com/watch?v=bTXUJQhEqL0)

### During class

* Lecture TT19: Introduction to Network Dynamics [pdf](pdf/tt19-network_dynamics.pdf)
   * Exercise: indicate phenomena that spread virally (pin board)
* Lecture TT20: Information diffusion [pdf](pdf/tt20-info_diffusion.pdf)
   * Exercise: simulate linear threshold model (spreadsheet)
   * Exercise: simulate independent cascade model (spreadsheet)

### After class

* Read [chapter 19](http://www.cs.cornell.edu/home/kleinber/networks-book/networks-book-ch19.pdf) of the book by Easley and Kleinberg


## Session 12: Modelling Epidemics

### Before class

* :tv: Watch this 13-minutes [infection simulations](https://www.youtube.com/watch?v=7OLpKqTriio)
* :tv: Watch this 24-minutes [explanation of the mathematics of the SIR model for COVID](https://www.youtube.com/watch?v=NKMHhm2Zbkw)

### During class

* Lecture TT21: Modelling Epidemics [pdf](pdf/tt21-epidemics.pdf)
   * Exercise: How to reduce R0 of an epidemic
* Lecture TT22: Epidemics on Networks [pdf](pdf/tt22-epi_networks.pdf)

### After class

* Read [chapter 10](http://networksciencebook.com/chapter/10) of the book by Barabási
* Read [chapter 21](http://www.cs.cornell.edu/home/kleinber/networks-book/) of the work by Easley and Kleinberg


## Final Exam (December 12th, 2025 at 15:00)

The final exam will include the material seen in class after the midterm exam. 



# Sources/credits

Some theory topics closely follow the "[Networks Science](http://networksciencebook.com/)" book (2016) and course by Albert-László Barabási. In all cases, the sources are indicated either at the beginning or in the footer of the slides. Please feel free to use, copy, and adapt contents from these slides for whatever purposes, giving proper attribution.

[<img src="../upf/cc-by-80x15.png" width="80" height="15" hspace="4"/>](https://creativecommons.org/licenses/by/4.0/) Slides available under a [Creative Commons](https://creativecommons.org/licenses/by/4.0/) license unless specified otherwise.


