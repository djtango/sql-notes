#SQL

*SQL* (*S*tructured *Q*uery *L*anguage) is a special-purpose programming language designed for managing data held in a relational database management system RDBMS, or for stream processing in a relational data stream management system (RDSMS).
😴

###HUH?

Let's try again... SQL ('_sequel_' for 'muricans) is a programming language we use for interacting with databases. A database being a place we store data. The word 'database' gets thrown around a lot, it's worth bearing in mind that a DB could be a couple of lines of information like a list of phone contacts (where people may have a name, a phone number, home address and email address) to a trillion row table containing every click you've ever made on Facebook in the last two years (known as Clickstream data), or every film ticket sold per film, per day, per cinema, per country (see what I did there 😉).

A '_relational database management system_' is a fancy way of describing a table of data. In an RDBMS database, you'll essentially find all data stored as a table which has rows and columns, with the first row being the column headers. There are other ways of storing data, but that's not important to learning SQL.

So basically SQL is our language to interact with tables of data. Why do it this way, why not use Excel? It's actually simpler this way - storing data on a pure database is smaller and faster than using Excel. It's also easier to make other programs that interact with a database too. It's also more powerful - doing large calculations, generating custom reports and manipulating or mining the data is all better done using SQL than Excel. The price we pay for this though is that it's not as user-friendly. So there is a time and place for both.

##Getting started with SQL syntax

Interacting with a database can be broken down fundamentally into two different activities: *reading* and *writing*. Reading data means that you are purely consuming data from the database - anything you are doing will not change the database. Writing means you are changing something on the database - you could be creating/updating or deleting information from the tables.

In general, most people start with learning to read data - being able to retrieve data is usually immediately useful to the user and it's also more user-friendly as making mistakes are not costly - so you can and should feel free to experiment! This is absolutely the fastest way to learn any new language.

#SELECT
All read queries start with the term *SELECT*. A *SELECT* statement is actually enough for a total query.

E.g.
```sql
SELECT 1;
```

When you write a SELECT statement, the words that follow the SELECT are referring to the columns you are selecting and will determine the width of your output data. To specify more columns, you simply write more words, _delimiting_ them with commas.

E.g.
```sql
SELECT 1,2,3,4;


SELECT 'abc', 'def';
```

##Misc
Remember the shape of the data
data types
logic
