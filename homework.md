## SQL Questions

First create a database called fringe_shows
```
  #terminal
  psql
  create database fringe_shows;
  \q
```

Populate the data using the script - fringeshows.sql
```
  #terminal
  psql -d fringe_shows -f fringeshows.sql
```

Using the SQL Database file given to you as the source of data to answer the questions.  Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.


## Section 1

  Revision of concepts that we've learnt in SQL today

  1. Select the names of all users.

  SELECT name FROM users;

  Keith Douglas
  Craig Morton
  Sandy McMillan
  Adrian Tuckwell
  Alex Bazlinton
  Bertie Coll
  Bobby Ross
  Carlos Pereira
  Claudia Menting
  Cookie Lacson
  Cyrus Balsara
  David OLeary
  Diana Man
  Euan Ramsay
  Josephine Elder
  Kate Manson
  Kyle Grenell
  Matthew Jeorrett
  Max Veasey
  Paul Milne
  Pavlos MacDonald-Kosmidis
  Ross Loggie
  Thomas Crines
  Tom Benham


  2. Select the names of all shows that cost less than £15.

  SELECT name FROM shows WHERE price < 15 ;

  Le Haggis
   Paul Dabek Mischief 
   Best of Burlesque
   Two become One
   Urinetown
   Two girls, one cup of comedy
  (6 rows)


  3. Insert a user with the name "Val Gibson" into the users table.

  INSERT INTO "users" (name) VALUES ('Val Gibson');

  SELECT name FROM "users";

  4. Insert a record that Val Gibson wants to attend the show "Two girls, one cup of comedy".

  INSERT INTO shows_users (show_id, user_id) VALUES (12, 25);

  5. Updates the name of the "Val Gibson" user to be "Valerie Gibson".

  UPDATE users SET name = ('Valerie Gibson') WHERE name = ('Val Gibson');

  6. Deletes the user with the name 'Valerie Gibson'.

  DELETE FROM users WHERE name = ('Valerie Gibson');

  7. Deletes the shows for the user you just deleted.

  DELETE FROM shows_users WHERE show_id = 12 AND user_id = 25;


## Section 2

  This section involves more complex queries.  You will need to go and find out about aggregate funcions in SQL to answer some of the next questions.

  9. Select the names and prices of all shows, ordered by price in ascending order.

  SELECT * FROM shows ORDER BY price ASC;

   id | created_at |                  name                   | price 
  ----+------------+-----------------------------------------+-------
   12 | 2016-08-23 | Two girls, one cup of comedy            |  6.00
    9 | 2016-08-23 | Best of Burlesque                       |  7.99
   10 | 2016-08-23 | Two become One                          |  8.50
   11 | 2016-08-23 | Urinetown                               |  8.50
    5 | 2016-08-23 | Paul Dabek Mischief                     | 12.99
    1 | 2016-08-23 | Le Haggis                               | 12.99
    6 | 2016-08-23 | Joe Stilgoe: Songs on Film – The Sequel | 16.50
    4 | 2016-08-23 | Game of Thrones - The Musical           | 16.50
    2 | 2016-08-23 | Shitfaced Shakespeare                   | 16.50
    7 | 2016-08-23 | Aaabeduation – A Magic Show             | 17.99
    3 | 2016-08-23 | Camille O'Sullivan                      | 17.99
   13 | 2016-08-23 | Balletronics                            | 32.00
    8 | 2016-08-23 | Edinburgh Royal Tattoo                  | 32.99

  10. Select the average price of all shows.

    SELECT AVG(price) FROM shows;

    15.9569230769230769

    SELECT ROUND(AVG(PRICE), 2) FROM shows;

    15.96

    #CHECK ROUND

  11. Select the price of the least expensive show.

  SELECT MIN(price) FROM SHOWS

  6.00

  12. Select the sum of the price of all shows.

  SELECT SUM(price) FROM shows;

  207.44

  13. Select the sum of the price of all shows whose prices is less than £20.

  SELECT  SUM(price) FROM shows WHERE price < 20;

  142.45

  14. Select the name and price of the most expensive show.

    SELECT name, price FROM shows WHERE price = (SELECT MAX(price) FROM shows);

              name          | price 
    ------------------------+-------
     Edinburgh Royal Tattoo | 32.99

  15. Select the name and price of the second from cheapest show.

    SELECT name, price FROM shows ORDER BY price LIMIT 1 OFFSET 1;

          name        | price 
    -------------------+-------
     Best of Burlesque |  7.99


  16. Select the names of all users whose names start with the letter "N".

  17. Select the names of users whose names contain "er".


## Section 3

  The following questions can be answered by using nested SQL statements but ideally you should learn about JOIN clauses to answer them.

  18. Select the time for the Edinburgh Royal Tattoo.

  19. Select the number of users who want to see "Shitfaced Shakespeare".

  20. Select all of the user names and the count of shows they're going to see.

  21. SELECT all users who are going to a show at 17:15.
