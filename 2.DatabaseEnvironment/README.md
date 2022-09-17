# Database

In this lesson we will setup a docker container to isolate a database from our global environment and open the connection to access it and train SQL later on.

## Docker

Docker is a container technology. The goal of a container is to isolate the resources dedicated for the container from the resources of the host machine. It works like a virtual machine (a tinier computer inside your computer).

## Database

A database is a storage system which manage for you the persistency (hard drive storage) and retrial of the data through some query language (SQL is the most known query language).
There are several mainstream databases, we will focus on relational databases as they are the most used and are queried through SQL. The most used relational Database Management Systems (DBMS) are:
- Oracle
- MySQL
- Postgres
Now, all cloud platform are launching their own DBMS (such as BigQuery for Google) but they offer more than relational storage thus we will focus on a simpler one.

## Postgres Setup

We will choose postgres as it is an open-source DBMS and is one of the most used in the modern data architectures.

### Install Docker

In itself, docker is just a set of command lines exposed to your command terminal.

https://docs.docker.com/desktop/install/windows-install/

### Postgres Container

We have to create a docker container with postgres inside. This container will only contain essentials of postgres. We will not explain how docker works here, it's not important for this lesson.

1. Create a new folder to create a postgres project
2. In this folder, copy-past the docker-compose file provided in this lesson folder
3. Open the terminal and navigate to your project folder
4. Execute the following command. It will create or execute the container:
```
docker compose up
```
5. Before leaving, you need to stop the container by using the following command:
```
docker compose down
```

### Postgres Connection

Using VScode or any other tool, create a connection to your running, the following information are needed:
- hostname: localhost
- port: 5432
- user: admin
- password: admin
- database: postgres

You postgres container can contain multiple database, this the default name created is "postgres". We also have to create users associated with each database, you can create / delete users but you need a default admin user which in this case has been named "admin" with password "admin".

### Creating a Table

SQL is a language which allows you to get control over everything in the database, the most common tasks are:
- Query / Fetch results from tables
- Create / Update tables
- Create users
- Manage the database: rights, roles etc..

We want to create a table with simple data so that we can get started with SQL. In your IDE (VSCode), create a script with the following query:

```
CREATE TABLE orders (
    id integer,
    name text,
    amount double precision,
    state text,
    customer name
);
```

This table is now created but is now empty, we want to insert some data inside so we can query them, execute the following query:

```
INSERT INTO orders (id, name, amount, state,customer)
VALUES 
	(1, 'SO001', 12.00, 'done', 'customer1'),
	(2, 'SO002', 20.00, 'done', 'customer1'),
	(3, 'SO003', 21.00, 'done', 'customer2'),
	(4, 'SO004', 18.00, 'cancel', 'customer2'),
	(5, 'SO005', 15.00, 'done', 'customer3'),
	(6, 'SO006', 30.00, 'done', 'customer3'),
	(7, 'SO007', 15.00, 'done', 'customer3'),
	(8, 'SO008', 8.00, 'done', 'customer2'),
	(9, 'SO009', 31.00, 'done', 'customer4'),
	(10, 'SO010', 17.00, 'cancel', 'customer5');
```

Now, you are ready to perform your first queries to the data.

### Simple Queries

To retrieve data, you have to construct the query statements in a certain order, let's see those statements

1. SELECT: The select statement indicates that you want to get an output, it is followed by the column names you want to see in your output. If you want all the column, you write: "SELECT *", or you can also list all the columns by their name: "SELECT id"

2. FROM: The from statement indicates the table you are queriying, without this, the DBMS doesn't know which table you want to access. A more complete query thus become: "SELECT id FROM orders". Try this query, it will return the full table:
```
SELECT *
FROM orders;
```

3. WHERE: The where statement allows filtering of data to eliminate from your input unwanted data. The following should be of a filtering form, for instance a query can become: "SELECT id FROM orders WHERE id = 1". Be careful of your data types while filtering as the type of the column you filter should be the same type as the provided filtered value. There are a lot of operators to perform equality / inequality / comparison / inclusion etc. Knowing them is very important. You can chain filter conditions with OR and AND statements. Try the following query:
```
SELECT *
FROM orders
WHERE state = 'done' AND id >= 2;
```

### Simple Exercices

1. Select all the column for the orders of "customer1"
2. Select all the column for the orders above 20 euros / dollar, whatever the currency is here.
3. Select all the ids of orders