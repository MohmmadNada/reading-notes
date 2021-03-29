## Introduction to SQL
**SQL**, or Structured Query Language, is a language designed to allow both technical and non-technical users query, manipulate, and transform data from a relational database. And due to its simplicity, SQL databases provide safe and scalable storage for millions of websites and mobile applications.

### Relational databases
relational database actually is. A relational database represents a collection of related (two-dimensional) tables

### SQL Lesson 1: SELECT queries 101
SELECT :To retrieve data from a SQL database
. A query in itself is just a statement which declares what data we are looking for, where to find it in the database, and optionally, how to transform it before it is returned.

    SELECT * (or column)
    FROM mytable;

### SQL Lesson 2: Queries with constraints (Pt. 1)
WHERE : filter certain results from being returned

    SELECT column, another_column, …
    FROM mytable
    WHERE condition
        AND/OR another_condition
        AND/OR …;


![Image 1](imges/read8-1.PNG)


### SQL Lesson 3: Queries with constraints (Pt. 2)

![Image 1](imges/read8.PNG)
>note : As you might have noticed by now, SQL doesn't require you to write the keywords all capitalized, but as a convention, it helps people distinguish SQL keywords from column and tables names, and makes the query easier to read.


### SQL Lesson 3: Queries with constraints (Pt. 2)
![Image 1](imges/read8.PNG)

### SQL Lesson 4: Filtering and sorting Query results
by DISTINCT :blindly remove duplicate rows
by ORDER BY: sort your results



    SELECT DISTINCT column, another_column, …
    FROM mytable
    WHERE condition(s);


    SELECT column, another_column, …
    FROM mytable
    WHERE condition(s)
    ORDER BY column ASC/DESC;


### SQL Lesson 13: Inserting rows
What is a Schema?
the structure of each table, and the datatypes 

#### insert data by INSERT 

    INSERT INTO mytable
    VALUES (value_or_expr, another_value_or_expr, …),
           (value_or_expr_2, another_value_or_expr_2, …),
           …;


### SQL Lesson 14: Updating rows


by UPDATE  statment UPDATE mytable
        SET column = value_or_expr, 
            other_column = another_value_or_expr, 
    …
        WHERE condition;


### SQL Lesson 15: Deleting rows
by DELETE statement,

    DELETE FROM mytable
    WHERE condition;

#### SQL Lesson 16: Creating tables

by CREATE TABLE statement.

```
CREATE TABLE IF NOT EXISTS mytable (
    column DataType TableConstraint DEFAULT default_value,
    another_column DataType TableConstraint DEFAULT default_value,
    …
);
```

#### SQL Lesson 17: Altering tables
by   ALTER TABLE statement to add, remove, or modify columns and table constraints.
Adding columns

        ALTER TABLE mytable
        ADD column DataType OptionalTableConstraint 
            DEFAULT default_value;

        Removing columns


        ALTER TABLE mytable
        DROP column_to_be_deleted;
        Renaming the table

        ALTER TABLE mytable
        RENAME TO new_table_name;


### SQL Lesson 18: Dropping tables
 by DROP TABLE statement  remove an entire table including all of its data and metadata

        DROP TABLE IF EXISTS mytable;
