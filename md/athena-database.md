# Creating Athena Tables

## Databases and Schemas in Athena
* In Athena, databases and schemas are essentially interchangeable terms.
* They both refer to a logical namespace that groups tables together.
* Databases and schemas do not store data themselves; instead, they provide a way to organize and manage the metadata that defines the schema of your data.
* This metadata includes information about the tables in the database, such as the table name, column names, data types, and partitions.

### Creating Databases and Schemas
* In Amazon Athena, when you create a database, you have the option to specify an S3 location where Athena will store metadata for tables within that database.
* However, it's not mandatory to provide an S3 location during database creation. If you don't specify an S3 location, Athena will use a default location for storing metadata.
```sql
CREATE DATABASE [IF NOT EXISTS] database_name
[COMMENT 'database_comment']
[WITH DBPROPERTIES ('key1'='value1', 'key2'='value2', ...)];
```
* In the above syntax:
* IF NOT EXISTS: This optional clause ensures that the database is created only if it does not already exist. If the database already exists, the query won't produce an error.
* COMMENT: This optional clause allows you to add a comment or description to the database.
* WITH DBPROPERTIES: This optional clause allows you to set custom properties for the database using key-value pairs.

* **Creating databases** and schemas in Athena using the CREATE DATABASE statement. The statement takes the following syntax:
```sql
CREATE DATABASE tinitiate_athena
COMMENT 'Tinitiate Athena'
LOCATION 's3://ti-instructor-data/athena-db';
```
* The database_name parameter is required and specifies the name of the database or schema you want to create.
* The COMMENT parameter is optional and allows you to add a comment to the database or schema.
* The LOCATION parameter is also optional and specifies the location of the data catalog where the metadata for the database or schema will be stored.

## Drop Database
```sql
DROP DATABASE [IF EXISTS] database_name [CASCADE | RESTRICT];
```
* IF EXISTS: This optional clause ensures that the database is dropped only if it exists. If the database doesn't exist, the query won't produce an error.
* CASCADE | RESTRICT: These options specify how to handle dropping the database if it contains tables or other objects.
* CASCADE: This option drops the database and all objects that depend on it. Use this if you're sure you want to remove everything associated with the database.
* RESTRICT: This option prevents dropping the database if it contains any objects. It's a safer option if you want to avoid accidentally dropping tables or other objects.

* Example
```sql
DROP DATABASE IF EXISTS tinitiate_athena CASCADE;
```