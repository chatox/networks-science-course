# Assignment 01: Network generation and display

## Materials

For this assignment you need the file `movie_metadata.csv` which contains information about 5,000 movies.

## Task

The task is to create two graphs:

1. A movie-movie graph in which two movies are connected if they share the same director or one actor.

2. An actor-actor graph in which two actors or actresses are connected if they appeared in the same movie.

## Mandatory attributes

### Movie attributes

For movie colors, use their genre (use the first genre if a list of genres is given).

For sizes of movies, you can use their `imdb_score` (a proxy for quality), `num_user_for_reviews` (a proxy for popularity),  `gross` (the total amount of money earned through tickets) or a combination of them.

### Actor attributes

Actor colors represent their dominant genre (the most common genre in the list of genres of the movies they appear on). Note that to compute actor colors you need all genres of the movies, not just the first genre.

For sizes of actors/actresses you can use their number of likes in Facebook, or the number of movies in which they have acted.

## Optional attributes

You can also include edge attributes, e.g., thicker edges for links connecting actors who collaborate in many movies.

You can use different node shapes for different clusters obtained using clustering.

Feel free to also create graphs mixing movies and actors, or to create sub-graphs that illustrate something specific (e.g., the sub-graph of all horror movies, or all comedy movies).

# Deliver (groups of two)

A .zip or .tar.gz file containing your report and code.

The report should be an insightful, informative, readable, beautiful, clear, concise two-pages document in PDF with images from Cytoscape and your findings. Be creative. Feel free to focus on a sub-category of movies or actors if you have some interesting finding to report on them.

The code should contain the Python code (Python notebook) that you used to pre-process the data for Cytoscape.

The report should end with the following statement: **We hereby declare that, except for the code provided by the course instructors, all of our code, report, and figures were produced by ourselves.**

**Both members of the group should learn Python**, as we will continue using Python throughout the course, hence, make sure you are not given non-Python tasks only in the division of work.
