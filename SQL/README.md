# SQL Databases

### Index

* [SQL](#SQL)
* [Concepts](#Concepts)
	* [ACID](#ACID)
	* [Schema](#Schema)
	* [Tables](#Tables)
* [Create DB](#Create-DB)
	* [Create Database](#Create-Database)
	* [Create User](#Create-User)
	* [Permissions](#Permissions)


## SQL

Structure Query Language

Is a language that let us query information from SQL database such as MySql or Oracle.

An example about this language is:

		SELECT * FROM TABLE_NAME;

1. Data uses Schemas.
2. Relations.
3. Data is distributed across multiples tables.
4. Scaling can be hard, only can scale vertical, and vertical scaling has limitations.
5. Limitation for lots of thousand read & write queries per second.

# Concepts.

## ACID

	1. Atomicity --> All or nothing.

	2. Consistency --> Transactions are valid to rules of the BD.

	3. Isolation --> Results of the transaction are as if they were done end to end. (Transactions shouldnt be dirty by external transactions)

	4. Durability --> Once a transaction is committed, it reamins so.

## Schema

Its an strictire described in a formal languague supportted by the database. The terms schema refers to the organization of data as a blueprint of how the database is contructed.

## Tables

The database table is where all the data in a database is stored, and without tables, there would not be much use for relational databases.

A database consists of one or more tables.  Each table is made up of rows and columns.  If you think of a table as a grid, the column go from left to right across the grid and each entry of data is listed down as a row.

Each row in a relational is uniquely  identified by a primary key.  This can be by one or more sets of column values.  In most scenarios it is a single column, such as employeeID.

## DML --> Data Manipulation Language

## DDL --> Data Definition Languague

# Create-DB

For the configuration of our MySql DB we are going to use docker. 

		1. docker run --name mysqldb -p 3306:3306 MYSQL_ALLOW_EMPTY_PASSWORD=yes -d mysql

## Create Database

		1. CREATE DATABASE <name_DB>;		

## Create User

		1. CREATE USER '<user_name>'@'<host>' IDENTIFIED BY '<password>';
			Ex: CREATE USER 'sfg_dev_user'@'localhost' IDENTIFIED BY '1234';
			Ex: CREATE USER 'sfg_dev_user'@'192.168.55.55' IDENTIFIED BY '1234';		
			CREATE USER 'sfg_dev_user'@'%' IDENTIFIED BY '1234';

## Permissions

1. GRANT SELECT ON <db_name>.* to 'sfg_dev_user'@'%';

2. GRANT INSERT ON <db_name>.* to 'sfg_dev_user'@'%';

3. GRANT DELETE ON <db_name>.* to 'sfg_dev_user'@'%';
		
4. GRANT UPDATE ON <db_name>.* to 'sfg_dev_user'@'%';		

With the aboce commands the database know that the user sfg_dev_user will have INSERT, SELECT, DELETE and UPDATE permissions in all the tablas of the DB db_name

		

