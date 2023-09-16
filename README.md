1. **Importing Libraries**: The code begins by importing necessary libraries, including Apache Log4j for logging, Apache Spark for distributed data processing, and related Spark functions.

2. **Setting Logging Level**: It sets the log level to error to reduce the amount of console output generated by Spark.

3. **Creating SparkSession**: It creates a SparkSession, which is the entry point to using Spark functionality.

4. **Loading and Processing Movie Ratings Data**:
   - It loads movie ratings data from a file into an RDD (Resilient Distributed Dataset).
   - Defines a case class `Rating` to structure the data.
   - Transforms the RDD into a DataFrame and registers it as a temporary table.

5. **Loading and Processing Movie Data**:
   - It loads movie data from another file into an RDD.
   - Defines a case class `Movie` to structure the data.
   - Transforms the RDD into a data frame, selecting relevant columns.

6. **SQL Query for Movie Statistics**:
   - It executes an SQL query to calculate statistics for movies:
     - Counts the number of times each movie has been rated.
     - Calculates the average rating for each movie.
     - Filters the results to include only movies with more than 1000 ratings and an average rating greater than 4.0.

7. **Enabling Broadcast Join**: It configures Spark to use broadcast join, optimizing the join operation if the `movieDf` DataFrame is small enough to fit in memory.

8. **Joining DataFrames**:
   - It specifies the join type as inner and the join condition.
   - Performs the join between the statistics DataFrame (`dff`) and the movie DataFrame (`movieDf`).
   - Drops unnecessary columns from the result.

9. **Displaying the Result**: Finally, it shows the resulting DataFrame, which contains movie statistics joined with movie names. The result includes only the relevant columns.

This code essentially calculates statistics for highly-rated movies with a sufficient number of ratings and then combines this data with movie names. The use of Apache Spark allows for efficient distributed data processing, making it suitable for handling large datasets.

Note- I'm using a rating system based on a minimum of 1000 users rating the movie and for the top-rated movie the condition is given a minimum of 4 stars as an average rating.


Output-

+-------------------------------------------------+
|movieName                                        |
+-------------------------------------------------+
|Godfather, The (1972)                            |
|Pulp Fiction (1994)                              |
|Shakespeare in Love (1998)                       |
|Silence of the Lambs, The (1991)                 |
|Raiders of the Lost Ark (1981)                   |
|Stand by Me (1986)                               |
|When Harry Met Sally... (1989)                   |
|M*A*S*H (1970)                                   |
|North by Northwest (1959)                        |
|Christmas Story, A (1983)                        |
|Star Wars: Episode VI - Return of the Jedi (1983)|
|Run Lola Run (Lola rennt) (1998)                 |
|Apocalypse Now (1979)                            |
|Rain Man (1988)                                  |
|Indiana Jones and the Last Crusade (1989)        |
|2001: A Space Odyssey (1968)                     |
|Princess Bride, The (1987)                       |
|Taxi Driver (1976)                               |
|Seven (Se7en) (1995)                             |
|Clockwork Orange, A (1971)                       |
+-------------------------------------------------+# 
