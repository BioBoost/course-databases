# SQL

SQL can be pronounced as:

* Letters: S-Q-L
* Or as `sequel`

SQL is an acronym for Structured Query Language. It is a domain-specific language that is designed specifically for communicating with databases. Unlike other languages, either spoken or programming languages such as Java or C++, SQL has very few keywords. This is deliberate. SQL is designed to do one thing, and do it very well. SQL provides you with a simple and efficient way to read and write data from a database.

SQL uses a relational database model. A relational database organizes sets of data in relations to eachother. This has some advantages:

- These relations allow the reduce the data storage footprint and better performance.
- It has a strong data integrity through ACID. ACID is an acronym for **A**tomicity, **C**onsistency, **I**solation, and **D**urability. 
- SQL provides an abstraction over how the data is represented on disk.

Unfortunately SQL also has some limitations:

- Its data model is best carefully designed up-front. Changing a schema results in downtime.
- SQL databases have been developed before distributed computing. It does no scale to multiple computer systems out-of-the-box. There are good examples of systems which use SQL databases in a distributed way.

## Standard database query language

SQL is not proprietary. It is not used by specific database vendors. Almost every major DBMS system supports SQL. This enables you to interact with just about every database you’ll run into.

SQL is easy to learn. The statements are all made up of descriptive English words, and there aren’t many of them. Despite its apparent simplicity, SQL is actually very powerful. Cleverly using its language elements, you can perform very complex and sophisticated database operations.

### MariaDB

::: tip ℹ️ MySQL vs MariaDB
MySQL is maintained by Oracle. MySQL is free to use but not entirely open source. Some parts are closed source. This was not the vision of the original developers, who felt there was a conflict of interest between MySQL and Oracle Database Server. Therefor they created a fork that replaces the closed source parts with open source alternatives. This fork is called **MariaDB**, and guarantees to stay open source.

MariaDB and MySQL are therefor compatible. All MySQL command are compatible with MariaDB and vice versa.
:::

![MariaDB and MySQL logo](./img/mariadb_vs_mysql.jpg)

MySQL has become one of the most popular database management systems in the world. It can be used for small development projects to large and prestigious sites on the web, an example is Facebook. MySQL has proven itself to be solid, reliable, fast and trusted to all sorts of data storage needs.

MySQL and MariaDB are open source and free to use. This makes it one of the most popular databases. It is also the best supported and best documented database for web based projects. A popular *stack* is LAMP. This consists of **L**inux operating system, **A**pache webserver, **M**ariaDB database and **P**HP programming language. On Windows a management tool called XAMPP contains these elements, except for Linux of course.

There are also other SQL databases, such as:

- PostgreSQL
- Oracle
- SQL Server
- ...

## NoSQL

SQL has been the industry standard since the late 1970's. However, in a distributed computing environment, SQL's consistency has been replaced with *eventual consistency* in favor of more speed, availability and partition tolerance, this is to distribute the database over multiple computer systems more easily. NoSQL is a term which refers to all database systems which are not SQL. More specifically, the data structures used in a NoSQL database are different from the relational model of SQL. These can be:

- key-value, e.g. Dynamo
- wide column, e.g. Cassandra
- graph, e.g. Neo4J
- document, e.g. MongoDB
- time series, e.g. InfluxDB

::: tip ℹ️ Most popular databases
There is a ranking of [most popular databases](https://db-engines.com/en/ranking). Just keep in mind that most popular does not always mean the best.
:::

In this course we are only going to study SQL databases and more specifically MariaDB.

## DDL vs DML

SQL statements can be divided into two categories:

* **Data definition language \(DDL\)** statements are used for creating tables, relationships and other structures.
* **Data manipulation language \(DML\)** statements are used for queries and data modification.

## CRUD

In computer programming, **create**, **read**, **update**, and **delete** (CRUD) are the four basic functions of persistent storage.

* **C**reate: Adding new data
* **R**ead: Requesting data
* **U**pdate: Changing data
* **D**elete: Removing data

Virtualy any software application makes use of this CRUD functionality.

For relational databases we can even apply this to the data definition and data manipulation languages.

Action | DDL | DML
---|---|---
C | `CREATE TABLE` | `INSERT INTO`
R | `SHOW COLUMNS` | `SELECT`
U | `ALTER TABLE` | `UPDATE`
D | `DROP TABLE` | `DELETE FROM`

The query statements mentioned above will be explained thoroughly in the next chapters.
