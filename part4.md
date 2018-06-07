Part 4
The data in this part of the assignment uses the: authors, articles, countries, provinces, cities, residences, and persons tables from earlier in the assignment.

Write SQL queries (in as many steps as necessary) to solve each of the following:

1) Find the author with the name 'Kara Melton' and then select all the articles she has written.

  SELECT title FROM articles WHERE author_id = (SELECT author_id FROM authors WHERE name = 'Kara Melton');


2) Find Ontario in the provinces table and then find all the cities in that province.

  SELECT name FROM cities WHERE province_id = (SELECT id FROM provinces WHERE name = 'Ontario')


3) Who wrote the article called 'Coding Bootcamps and Emotional Labor'?

  SELECT name FROM authors WHERE id = (SELECT author_id FROM articles WHERE title = 'Coding Bootcamps and Emotional Labor');



4) Write a series of SQL queries to find out how many provinces are in Canada.

  SELECT name FROM provinces WHERE country_id = (SELECT country_id FROM countries WHERE name = 'Canada')


5) How many people live at 4740 McDermott Street?

  SELECT COUNT(name) FROM persons WHERE residence_id = (SELECT id FROM residences WHERE address = '4740 McDermott Street');


6) What city is 4740 McDermott Street in?

  SELECT name FROM cities WHERE id = (SELECT city_id FROM residences WHERE address = '4740 McDermott Street');


7) What province is 4740 McDermott Street in?

  SELECT name FROM provinces WHERE id = (SELECT province_id FROM cities WHERE id = (SELECT city_id FROM residences WHERE address = '4740 McDermott Street'));


8) What country is 4740 McDermott Street in?

  SELECT name FROM countries WHERE id = (SELECT country_id FROM provinces WHERE id = (SELECT province_id FROM cities WHERE id = (SELECT city_id FROM residences WHERE address = '4740 McDermott Street')));


9) Find the person named 'Destini Davis' and then use a series of SQL queries to find what country they live in.

  SELECT name FROM countries WHERE id = (SELECT country_id FROM provinces WHERE id = (SELECT province_id FROM cities WHERE id = (SELECT city_id FROM residences WHERE id = (SELECT residence_id FROM persons WHERE name = 'Destini Davis'))));


10) How many articles has Aditya Mukerjee written?

SELECT COUNT(title) FROM articles WHERE author_id = (SELECT id FROM authors WHERE name = 'Aditya Mukerjee');


BONUS
And the name of the article is:

SELECT title FROM articles WHERE author_id = (SELECT id FROM authors WHERE name = 'Aditya Mukerjee');

                          title                          
---------------------------------------------------------
 I Can Text You A Pile of Poo, But I Can’t Write My Name
