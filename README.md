#SQL

*SQL* (*S*tructured *Q*uery *L*anguage) is a special-purpose programming language designed for managing data held in a relational database management system RDBMS, or for stream processing in a relational data stream management system (RDSMS).
😴

###HUH?

Let's try again... SQL ('_sequel_' for 'muricans) is a programming language we use for interacting with databases. A database being a place we store data. The word 'database' gets thrown around a lot, it's worth bearing in mind that a DB could be a couple of lines of information like a list of phone contacts (where people may have a name, a phone number, home address and email address) to a trillion row table containing every click you've ever made on Facebook in the last two years (known as Clickstream data), or every film ticket sold per film, per day, per cinema, per country (see what I did there 😉).

A '_relational database management system_' is a fancy way of describing a table of data. In an RDBMS database, you'll essentially find all data stored as a table which has rows and columns, with the first row being the column headers. There are other ways of storing data, but that's not important to learning SQL.

So basically SQL is our language to interact with tables of data. Why do it this way, why not use Excel? It's actually simpler this way - storing data on a pure database is smaller and faster than using Excel. It's also easier to make other programs that interact with a database too. It's also more powerful - doing large calculations, generating custom reports and manipulating or mining the data is all better done using SQL than Excel. The price we pay for this though is that it's not as user-friendly. So there is a time and place for both.

##Getting started with SQL syntax
_syntax is the term we use to describe the rules that a programming language has to follow, invalid syntax will cause a syntax error and your query won't run._

Interacting with a database can be broken down fundamentally into two different activities: *reading* and *writing*. Reading data means that you are purely consuming data from the database - anything you are doing will not change the database. Writing means you are changing something on the database - you could be creating/updating or deleting information from the tables.

In general, most people start with learning to read data - being able to retrieve data is usually immediately useful to the user and it's also more user-friendly as making mistakes are not costly - so you can and should feel free to experiment! This is absolutely the fastest way to learn any new language.

Most read queries will comprise of three keywords: `SELECT` `FROM` `WHERE`.

#SELECT
All read queries start with the term `SELECT`. A `SELECT` statement is actually enough for a total query.

E.g.
```sql
SELECT 1;
```

When you write a `SELECT` clause, the words that follow the `SELECT` are referring to the columns you are selecting and will determine the width of your output data. To specify more columns, you simply write more words, _delimiting_ them with commas.

E.g.
```sql
SELECT 1,2,3,4;


SELECT 'abc', 'def';
```

SQL also allows you to to run calculations:
```sql
SELECT 1, 1+1, 9/3, 2*2, 10-5;
```

On it's own writing queries like this wouldn't be that helpful. That's because we're currently only selecting values. This is where the next keyword comes in:

#FROM

The `FROM` keyword allows us to extract data from a table. This is where the value of SQL comes from. To `SELECT` data `FROM` a table, we do two things:
*1 `SELECT` the, column, names, you, want
*2 `FROM` the.table_holding_the_data

In short, when a `FROM` keyword appears in the query, SQL will read the words in the `SELECT` clause and try to match column names in the `FROM` table. If it succeeds, the query will execute and return all the data in the table held in those columns.

The `FROM` clause should follow after the columns targets in your `SELECT`
_make sure there are no trailing commas at the end of your list of column names_
####Examples
```sql
SELECT title, release_date, actors, directors
FROM   united_kingdom.movies;
```

```sql
SELECT date, ticket_sales, region
FROM   united_kingdom.cinema_data
```

Using just `SELECT` and `FROM` we can pull out entire datasets from our database, but often datasets can be large and cumbersome. Additionally, we often have specific requirements of our data in mind and want to filter datasets by specific contraints...

#WHERE

This is where the `WHERE` clause comes in handy. Suppose from our previous example we wanted to find all titles that released last December:

```sql
SELECT title, release_date, actors, directors
FROM   united_kingdom.moves
WHERE  release_date BETWEEN DATE '2015 12 01' AND DATE '2015 12 31'
```
After your `SELECT` clause and your `FROM` clause, SQL will look for a `WHERE` clause _(no commas after the `FROM`)_

Following the `WHERE` you can add a series of conditional statements, separated by the keywords `AND` or `OR`. Using `AND`, *all* the conditions must be true and when using `OR` *any* of the the conditions can be true.

Examples of conditions:


Suppose we wanted a query that would: `SELECT` all the `ticket_sales`, showing us the `title`, `sales_date` and `cinema` these `ticket_sales` relate to `FROM` our table containing `cinemas.sales`, `WHERE` the filmes belong to the Harry Potter franchise *except* Hary Potter 5 (which obviously was rubbish).

To keep our data less noisy, we'll also drop cinemas with `ticket_sales` less than 1000 and we only want sales `BETWEEN` the noughties.

Here is what that query might look like:

```sql
SELECT title, sales_date, cinema, ticket_sales
FROM   cinemas.sales
WHERE  lower(title) like '%harry potter%'
   AND region = 'LONDON'
   AND sales_date BETWEEN DATE '2000-01-01' AND DATE '2009-12-31'
   AND title != 'Harry Potter and the Order of the Phoenix'
   AND ticket_sales > 1000;
```

Notes about some of those conditions:
   `lower(<text>)` is a function in PostgreSQL, it converts and text to only lowercase text, this makes matching text case-insensitive and simpler.  
   `like` is similar to `=` but for text matching, it gives some additional options, `%` being one of them: this is a wildcard symbol and so `%harry potter%` means "...harry potter..." or any string of text which features the substring 'harry potter' within it. This means that any film title which only has `harry` (like _When Sally met Harry_) or `potter` (like the Aussie parody _Potter_) alone will not match, neither will a title with words between harry and potter match.  
   `BETWEEN` allows you to specify a range for a value to fall between, it's *inclusive* so `BETWEEN 1 AND 10` is `1, 2... 9, 10`  

There are a whole bunch of conditions and operators, resources like [techonthenet](http://www.techonthenet.com/postgresql/) are good look up references for finding new conditions.
##Data Types
TODO
##Tips
TODO
##Logic
TODO
