Select all
### SELECT * FROM FilmLocations;

Select specific cols
### SELECT Title, Director, Writer FROM FilmLocations;

Select Title ReleaseYear and Location Columns from the table where ReleaseYear is greater than or equal to 2001
### SELECT Title, ReleaseYear, Locations FROM FilmLocations WHERE ReleaseYear>=2001;

Retrieve the fun facts and filming locations of all films.
### SELECT FunFacts, Locations FROM FilmLocations;

Retrieve the names of all films released in the 20th century and before (release years before 2000 including 2000), along with filming locations and release years.
### SELECT Title, Locations, ReleaseYear FROM FilmLocations WHERE ReleaseYear <=2000;


Retrieve the names, production company names, filming locations, and release years of the films not written by James Cameron.
### SELECT Title, Locations, ReleaseYear, ProductionCompany FROM FilmLocations WHERE Writer!="James Cameron";