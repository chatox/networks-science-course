# Assignment 01: Network generation and display

## Materials

For this assignment you need the file [movie_metadata.csv](data/movie_metadata.csv) which contains information about 5,000 movies.

## Task

The task is to write Python code, in a Jupyter Notebook, that reads the `movie_metadata.csv` file and creates four CSV files.

1. The first CSV file, `movie-movie-edges.csv`, should describe the *movie-movie graph* in which two movies are connected if they share the same director or one actor. It should have a minimum of two columns (`movie1` and `movie2`), but you can include additional columns representing attributes of the relationship between the two movies (e.g., number of actors in common).

2. The second CSV file, `actor-actor-edges.csv`, should describe the *actor-actor graph* in which two actors or actresses are connected if they appeared in the same movie. It should have a minimum of two columns (`actor1` and `actor2`), but you can include additional columns representing attributes of the relationship between the two actors (e.g., number of movies in common).

3. The third CSV file, `movie-attributes.csv`, should describe *movie attributes*. The first column should be the movie name, and the remaining columns some attributes of each movie.

4. The fourth CSV file, `actor-attributes.csv`, should describe *actor attributes*. The first column should be the actor/actress name and the remaining columns some attributes of each actor.

Then, you will open these CSV files from Cytoscape to visualize them, importing the `*-edges.csv` files as graphs, and the `*-attributes.csv` as tables. This is similar to what you did in one of the practices, but instead of creating the CSV files by hand, you create them using Python.

:warning: **Check your output to make sure that you are connecting movies only if they have the same director or share an actor**. If the movie-movie network takes a long time to load, does not load at all, or crashes Cytoscape, it is very likely that you made a mistake during its generation. Check some pairs of movies at the beginning, middle, end of the *movie-movie* graph and see if they are really related in the movie metadata file. Check that you are dealing correctly with cases in which one of the actors is empty, i.e., do not connect movies if their intersection is just one actor whose name is empty.

:bulb: **If there are too many nodes for Cytoscape to visualize (layout), then you should focus on a sub-group of movies**. You can create a file `movie-movie-selected-edges.csv` having only edges connecting two movies that have a certain characteristic, or edges in which at least one of the two movies has a certain characteristic. This characteristic may be, for instance, having a budget or gross earnings of more than a certain amount, being older or newer than a certain year, belonging to a certain genre, containing a certain key word in their title, or featuring a certain director or actor/actress. Select any sub-set of movies that is large enough to be interesting but small enough for Cytoscape to visualize it.

## Mandatory attributes

### Movie attributes

For movie colors, use their genre (use the first genre if a list of genres is given).

For sizes of movies, you can use their `imdb_score` (a proxy for quality), `num_user_for_reviews` (a proxy for popularity),  `gross` (the total amount of money earned through tickets) or a combination of them.

### Actor attributes

Actor colors represent their dominant genre (the most common genre in the list of genres of the movies they appear on). Note that to compute actor colors you need all genres of each movie, not just their first genre.

For sizes of actors/actresses you can use their number of likes in Facebook, or the number of movies in which they have acted.

## Optional attributes

You can also include edge attributes, e.g., thicker edges for links connecting actors who collaborate in many movies.

You can use different node shapes for different clusters obtained using clustering (using the ModuLand plug-in).

Feel free to also create graphs mixing movies and actors, or to create sub-graphs that illustrate something specific (e.g., the sub-graph of all horror movies, or all comedy movies).

# Deliver (groups of two)

A .zip or .tar.gz file containing your report, your code, and the data files you generated.

The report should be an insightful, informative, readable, beautiful, clear, concise two-pages document in PDF with images from Cytoscape and your findings. Be creative. Feel free to focus on a sub-category of movies or actors if you have some interesting finding to report on them.

The code should be the Python notebook (.ipynb file) that you wrote.

**Both members of the group should learn Python**, as we will continue using Python throughout the course, hence, make sure you are not given non-Python tasks only in the division of work.

The report should end with the following statement: **We hereby declare that, except for the code provided by the course instructors, all of our code, report, and figures were produced by ourselves.**
