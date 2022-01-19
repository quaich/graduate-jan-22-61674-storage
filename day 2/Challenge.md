1) Select the movie_name & release_date of every movie.
SELECT movie_name, release_date FROM movies;

2) Select the first and last names of all American directors.
SELECT first_name, last_name FROM directors WHERE nationality = 'American';

3) Select all male actors born after the 1st of January 1970.
SELECT first_name, last_name FROM actors WHERE date_of_birth > '01-01-1970' AND gender = 'M';

4) Select the names of all movies which are over 90 minutes long and movie language is English.
SELECT movie_name FROM movies WHERE movie_lang = 'English' and movie_length > 90;

5) Select the movie names & movie language of all movies with a movie language of English, Spanish, or Korean.
SELECT movie_name, movie_lang FROM movies WHERE movie_lang = 'English' or movie_lang = 'Spanish' or movie_lang = 'Korean';

6) Select the first and last names of the actors whose last name begins with M and were born between 01/01/1940 and 31/12/1969.
SELECT first_name, last_name FROM actors WHERE last_name LIKE 'M%' and date_of_birth > '01-01-1940' and date_of_birth < '31-12-1969';

7) Select the first and last names of the directors with natioanlity of British, French or German born between 01/01/1950 and 31/12/1980.
SELECT first_name, last_name from directors WHERE nationality = 'British' or nationality = 'French' or nationality = 'German' and date_of_birth > '01-01-1950' and date_of_birth < '31-12-1980';
