# List of theory topics

There are 12 theory sessions of 2 hours each. They will all take place face-to-face. Please bring your laptop. One theory session is devoted to the mid-term exam (see below). 

:construction: These materials should not be considered final until the end of the course. Theory sessions from 6 to 12 will be uploaded after the mid-term exam.

**Before each class, there are short videos you should watch.** They are up to 20 minutes in total, and watching them requires some preparation/scheduling on your part. Please set aside time in your schedule to watch these videos before coming to class, ideally on the day before.

**During class,** I will present the contents using slides and we will do together some exercises using Padlets or Google Spreadsheets, or on the blackboard. 

**After each session, there is some reading for you to do.** These readings will be much easier after you have attended each lecture, will bring depth to what you learn in class, and will help you remember these contents better. Think of these readings as continuous studying that will save time and effort when preparing for the exams.

**Exams.** After four sessions, a *midterm exam* will be taken. At the end of the course, a *final exam* will be taken. The exam questions are based exclusively on the materials shown or discussed in the lectures during class. You will be allowed to bring your notes to the exams. No laptops or phones will be allowed.


## Session 1: Why studying Network Science

### Before class

* Take a look at the list of [theory topics](./),  [practice sessions](../practicum/README.md), and [evaluation rules](../upf/upf-evaluation.md)

### During class

* Lecture TT01: Networks: Introduction [pdf](pdf/tt01-intro.pdf)
   * :tv: First minute of [The hidden networks of everything](https://www.youtube.com/watch?v=RfgjHoVCZwU)
   * Exercise: find examples of networks (pin board)
* Course overview
   * Overview of [theory topics](./)
   * Overview of [practice sessions](../practicum/README.md)
   * Overview of [evaluation rules](../upf/upf-evaluation.md)
* Lecture TT02: Graph Theory: Basics [pdf](pdf/tt02-basics.pdf)
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

* Lecture TT03: Graph Theory: Connectivity [pdf](pdf/tt03-connectivity.pdf)
   * Quick exercise: find strongly connected components
* Lecture TT04: Graph Theory: Centrality [pdf](pdf/tt04-centrality.pdf)
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

* Lecture TT05: Graph Theory: Degree Correlations  [pdf](pdf/tt05-assortativity.pdf)
   * Exercise: average nearest neighbors' degree in uncorrelated networks (blackboard)
* Lecture TT06: Graph Theory: Clustering, and Homophily  [pdf](pdf/tt06-clustering.pdf)
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

## Session 5: Mid-term exam (October 23rd, 2024, 16:30)

### Before class

Study on your own, try to solve exams from past years. 

### During class

We will have a mid-term exam; there will be no lecture after the exam. The topics for the exam will be from lectures TT01-TT07.


## Session 6: The Erdos Renyi model

### Before class

* :tv: Watch the 17-minutes video on [the ER random graph model](https://www.youtube.com/watch?v=3PxteAgVf0o) by Lada Adamic (has subtitles in English)

### During class

* Lecture TT09: Network models: Erdos Renyi (ER) networks [pdf](pdf/tt09-ERmodel.pdf)
   * Exercise: guess the formula for the expected number of links
   * Exercise: compute the expected number of links and expected average degree
* Lecture TT10: Network models: properties of ER networks [pdf](pdf/tt10-ERproperties.pdf)
   * Exercise: guess the critical point at which a giant connected component emerges
   * Exercise: find critical N for a graph to be connected

### After class

* Read [chapter 3](http://networksciencebook.com/chapter/3) of the book by Barabási

## Session 7: Scale-free Networks

### Before class

* :tv: Watch this 20-minutes [video on Zipf, Pareto, and power laws](https://www.youtube.com/watch?v=ViUqxEF4plA&list=PL2rR6Wa-StjYOW7v6J8_npck6EDOKEbCN&index=10) by Lada Adamic. It is a great explanation of a phenomenon that goes well beyond networks.

### During class

* Lecture TT11: Scale-free (SF) networks [pdf](pdf/tt13-scale_free_networks.pdf)
   * Exercise: compute nodes with an expected degree
* Lecture TT12: Distances in SF networks [pdf](pdf/tt14-distances_scale_free_nets.pdf)
   * Exercise: compare average distances estimators for some networks

### After class

* Read the [chapter 4](http://networksciencebook.com/chapter/4) of the book by Barabási


## Session 8: Modelling SF networks

### Before class

* :tv: Watch the 13-minutes video on [preferential attachment](https://www.youtube.com/watch?v=hgrJCBmdjws) from a course on fractals and scaling

### During class

* Lecture TT13: Network models: preferential attachment [pdf](pdf/tt16-preferential_attachment.pdf)
   * Exercise: guess slope of degree distribution, using NetLogo to run simulations (pin board)
   * Exercise: write formula for number of nodes and edges over time
* Lecture TT14: Degrees under preferential attachment [pdf](pdf/tt17-preferential_attachment_degree.pdf)

### After class

* Read the [chapter 5](http://networksciencebook.com/chapter/5) of the book by Barabási

# Sources/credits

Some theory topics closely follow the "[Networks Science](http://networksciencebook.com/)" book (2016) and course by Albert-László Barabási. In all cases, the sources are indicated either at the beginning or in the footer of the slides. Please feel free to use, copy, and adapt contents from these slides for whatever purposes, giving proper attribution.

[<img src="../upf/cc-by-80x15.png" width="80" height="15" hspace="4"/>](https://creativecommons.org/licenses/by/4.0/) Slides available under a [Creative Commons](https://creativecommons.org/licenses/by/4.0/) license unless specified otherwise.
