1) Select the American directors ordered from oldest to youngest.
SELECT first_name, last_name FROM directors ORDER BY date_of_birth;

2) Return the distinct nationalities from the directors table.
SELECT DISTINCT nationality FROM directors;

3) Return the first names, last names and date of births of the 10 youngest female actors.
SELECT first_name, last_name, date_of_birth FROM actors ORDER BY date_of_birth DESC LIMIT 10;

4) Return the top 3 movies with the highest international takings.
SELECT movies.movie_name, movie_revenues.international_takings FROM movies INNER JOIN movie_revenues ON movies.movie_id = movie_revenues.movie_id WHERE international_takings IS NOT NULL ORDER BY international_takings DESC LIMIT 3;

5) Concatenate the first and last names of the directors spearated by a space, and call this new column full_name.
SELECT first_name, last_name, first_name || ' ' || last_name AS full_name FROM directors;

6) Return the actors with missing first_names or data_of_births.
SELECT first_name, last_name FROM actors WHERE first_name IS NULL OR date_of_birth IS NULL;

7) Count the number of actors born after the 1st January 1970.
SELECT COUNT(first_name) FROM actors WHERE date_of_birth > '01-01-1970';

8) What was the highest and lowest domestic takings for a movie.
SELECT MAX(movie_revenues.domestic_takings), MIN(movie_revenues.domestic_takings) FROM movies INNER JOIN movie_revenues ON movie_revenues.movie_id = movies.movie_id;

9) What is the sum total movie length for movies rated 15.
SELECT SUM(movie_length) FROM movies WHERE age_certificate = '15';

10) How many Japanese directors are in the directors table.
SELECT COUNT(nationality) FROM directors WHERE nationality = 'Japanese';

11) What is the average movie length for chinese movies.
SELECT AVG(movie_length) FROM movies WHERE movie_lang = 'Chinese';

12) How many directors are there per nationality?
SELECT nationality, COUNT(nationality) FROM directors GROUP BY nationality;

13) What is the sum total movie_length for each age certificate and movie language combination?
SELECT age_certificate, SUM(movie_length) FROM movies GROUP BY age_certificate;

14) Return the movie languages which have a sum total movie length of over 500 minutes.
SELECT movie_lang, SUM(movie_length) FROM movies GROUP BY movie_lang HAVING SUM(movie_length) > 500;

15) Select the directors first and last names, the movie names, and release dates for all Chinese, Korean, and Japanese movies.
SELECT directors.first_name, directors.last_name, movies.movie_name, movies.release_date FROM movies INNER JOIN directors ON directors.director_id = movies.director_id WHERE directors.nationality = 'Chinese' or directors.nationality = 'Korean' or directors.nationality = 'Japanese';

16) Select the movie names, release dates & international takings of all English language movies.
SELECT movies.movie_name, movies.release_date, movie_revenues.international_takings FROM movies INNER JOIN movie_revenues ON movie_revenues.movie_id = movies.movie_id WHERE movies.movie_lang = 'English';

17) Select the movie names, domestic takings and international takings for all movies with either missing domestic takings or missing international takings and order the results by movie name.
SELECT movies.movie_name, movie_revenues.domestic_takings, movie_revenues.international_takings FROM movies INNER JOIN movie_revenues ON movies.movie_id = movie_revenues.movie_id WHERE movie_revenues.domestic_takings IS NULL OR movie_revenues.international_takings IS NULL ORDER BY movies.movie_name ASC;

18) Use left join to select the first and last names of all British directors and the names and age certificates of the movies that they directed.
SELECT directors.first_name, directors.last_name, movies.movie_name, movies.age_certificate FROM directors LEFT JOIN movies ON directors.director_id = movies.director_id WHERE directors.nationality = 'British';

19) Count the number of movies that each director has directed.
SELECT directors.first_name, directors.last_name, COUNT(movies.movie_name) FROM directors INNER JOIN movies ON directors.director_id = movies.director_id GROUP BY directors.first_name, directors.last_name;

20) Select the first names, last names and dates of birth from directors & actors table. Order the result by the date of birth.
SELECT first_name, last_name, date_of_birth from actors UNION SELECT first_name, last_name, date_of_birth from directors ORDER BY date_of_birth;

21) Select the first and last names of all directprs and actors born in the 1960s. Order the result by last name.
SELECT first_name, last_name from actors WHERE date_of_birth BETWEEN '01-01-1960' AND '31-12-1969' UNION SELECT first_name, last_name from directors WHERE date_of_birth BETWEEN '01-01-1960' AND '31-12-1969' ORDER BY last_name;
