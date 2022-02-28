---
title: Tables
---

# Database Tables

<!-- introduction -->

- Listing Tables
- Inspecting Tables
- Managing Tables

MySQL provides some commands to inspect the existing databases, tables, and there structure \(columns and properties of those columns\).

The following features are just some of the available:

* Listing the available databases
* Listing the tables from a specific database
* Listing the columns and there properties from a specific table
* ...

This can be used to explore the existing databases and getting to know what is available.

<!-- use statement -->

## Listing Databases

In order to display all available databases:

```sql
SHOW DATABASES;
```

## Setting The Default Database

```sql
USE [database_name];
```

This query sets *database_name* as its default database. 

:::tip
To refer to a table, you have two choices:

A `fully qualified table` name consists of a database identifier and a table identifier:

```sql
SHOW COLUMNS FROM db_name.tbl_name;
SELECT * FROM db_name.tbl_name;
```

A table identifier by itself refers to a table in the default (current) database. If sampledb is the default database (set using the `USE` statement), the following statements are equivalent:

```sql
SELECT * FROM member;
SELECT * FROM sampledb.member;
```

:::

## Listing Tables

The following query lists all tables in a database.

```sql
SHOW TABLES;
```

### Inspecting Table Structure

```sql
DESCRIBE [table_name];
```

This query describes all columns in a given table.

:::tip
It is possible to use the following shorthand notation.

```sql
DESC [table_name];
```

:::

```sql
SHOW COLUMNS FROM [table_name] [options]
```

The difference between DESCRIBE and SHOW COLUMNS is that with SHOW COLUMNS, you have more options, like showing columns from a specific DB and using LIKE to display a list of columns using wildcards. This is especially useful if you have a table with a lot of columns that have similar names or names that contain prefixes/suffixes. For example,

```sql
SHOW COLUMNS FROM products LIKE '%prod%';
```

## Managing Tables

:::warning There is no Undo
Be very careful with the features and commands explained below. There is no undo functionality in a database. If something went wrong, if did not result in expected behavior, there is no way to get your data back. Always make sure to backup your data before making changes that you are not confident with.
:::

### Creating Tables

```sql
CREATE TABLE [table_name] (
  column_name datatype....
);
```

The CREATE TABLE creates a new table with a given table_name. All columns are desrcribed with their name, datatype and optional attributes.

### Updating Tables

#### Renaming a Table

In order to rename a table:

```sql
ALTER TABLE websites
  RENAME TO sites;
```

#### Add a New Column

Adding a column to a table:

```sql
ALTER TABLE games
  ADD release datetime;
```

You can add multiple columns in a single statement by chaining them with a `,`;

```sql
ALTER TABLE games
  ADD release datetime,
  ADD early_access boolean;
```

#### Renaming Columns

Renaming a column, beware not to change the column datatype, as long as data is present in the table.

```sql
ALTER TABLE table_name
    CHANGE COLUMN old_col_name new_col_name same_data_type;
```

#### Changing a Datatype

Changing datatypes of a column should only be done when the table is empty, or if the new datatype is less restrictive than the current datatype.

```sql
ALTER TABLE games
  MODIFY COLUMN name char(50);
```

#### Remove Existing Column

Beware of deleting columns in a table which contains data.

```sql
ALTER TABLE games
  DROP COLUMN release;
```

### Deleting Tables

:::danger
You wouldn't be the first to drop the production database rather than the test database.
:::

```sql
DROP TABLE [table_name];
```

## Indexing

Database indexes improve the speed to retrieve data from tables, and they are invisible to users.

:::tip
Indexes improve the speed of SELECT queries, but will slow down INSERT and UPDATE queries.
:::

```sql
CREATE UNIQUE INDEX [index_name] ON [table_name] ( [column1], [column2],...);
```

This statement creates an index with a name using the columns as indicated in the list.

To show all available indexes in a table use:

```sql
SHOW INDEX FROM [table_name]\G
```

The **\G** format specifier will put everything in a vertical format. This will improve readability.
