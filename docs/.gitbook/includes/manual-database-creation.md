For manual creation of databases, you can use the following queries:

## Queries for MySQL database

Let's name the database as `db1`:

```sql
DROP DATABASE IF EXISTS db1;
CREATE DATABASE db1 CHARACTER SET utf8mb4 COLLATE utf8mb4_bin;
```

Let's name the reports database as reportsdb:

```sql
DROP DATABASE IF EXISTS reportsdb;
CREATE DATABASE reportsdb CHARACTER SET latin1 COLLATE latin1_general_cs; 
```

## Queries for MS SQL/Azure SQL Database

**Collation Considerations**

* For Multiple Language Systems:
  * If your end systems support multiple language characters, it's essential to choose a collation that supports **UTF** characters.
  * To enable UTF character support in **<code class="expression">space.vars.SITENAME</code>**, install it on **Microsoft SQL Server 2019 or above**.
  * Select a collation with a `UTF` postfix, for example: `Latin1_General_100_CS_AS_SC_UTF8`
* For Single Language Systems:
  * If your end systems utilize a single language and your selected collation includes all the necessary characters and is supported in SQL Server versions below 2019, you can proceed with the installation on SQL Server version below 2019. Select an appropriate collation that suits your end systems [which are going to be configured in <code class="expression">space.vars.SITENAME</code>].
  * Select an appropriate collation that suits your end systems (which will be configured in **<code class="expression">space.vars.SITENAME</code>**).
  * Here is [guide](https://learn.microsoft.com/en-us/sql/relational-databases/collations/collation-and-unicode-support?view=sql-server-ver16) that may help you decide the right collation for your database.

> **Note:**  
> We need **1 database** and **2 schemas** to be created manually, out of which The **database and schema name must be the same** for the OpsHub database, and another schema should be created for **reportsdb**.

```sql
drop database IF EXISTS db1
db1 database: create database db1 COLLATE Latin1_General_CS_AS;
db1 schema: create schema db1;
Reports schema: create schema reportsdb;
```

## Queries for Oracle Database

> **Note:** Replace `<<SERVER_PASSWORD>>` with the actual password.

Let's name the database as `db1`:

```sql
drop user db1 CASCADE;
CREATE USER db1 IDENTIFIED BY <<SERVER_PASSWORD>> DEFAULT TABLESPACE users QUOTA 500M ON users TEMPORARY TABLESPACE temp PROFILE DEFAULT ACCOUNT UNLOCK
```

Let's name the reports database as reportsdb:

```sql
drop user reportsdb CASCADE;
CREATE USER reportsdb IDENTIFIED BY <<SERVER_PASSWORD>> DEFAULT TABLESPACE users QUOTA 2048M ON users TEMPORARY TABLESPACE temp PROFILE DEFAULT ACCOUNT UNLOCK
```

>**Note**:  Ensure both `db1` and `reportsdb` users have the required privileges. For system and object privileges, refer to [Database Prerequisites](prerequisites.md#database-prerequisites).

* Note, in case of manual database creation with Oracle database, OpsHub database user ("db1") and OpsHub reports database user ("reportsdb") shall be created on the same server. At the time of installation, you need to provide the username and password for the database server.
* In case of Oracle database, passwords for the database users ("db1" and "reportsdb") shall be the same as the password of the server on which they are created.
* If you want to change the tablespace quota for OpsHub database "db1", following query can be used: 

```sql
ALTER USER db1 QUOTA <size_of_tablespace> ON users;
```
> **Note:** `"db1"` and `"reportsdb"` are the database/schema/database user names used in the above queries. You can name them differently as per your requirements.

## Queries for PostgreSQL Database

* In case of manual database creation for PostgreSQL Server database, database and schema should be in lowercase only.
  * We need 1 database and 2 schemas to be created manually, out of which database and schema's names must be same for opshub database. The other schema will be created for reportsdb.

Let's say the name of the database is `db1`:
```sql
drop database IF EXISTS db1
db1 database: CREATE DATABASE db1
WITH
ENCODING = 'UTF8'
LC_COLLATE = 'en_US.UTF-8'
LC_CTYPE = 'en_US.UTF-8'
TEMPLATE = template0;
```

>**Note**: The above query will create database with Collate United States, UTF-8. For creating database with desired collate, update `LC_COLLATE` and `LC_CTYPE` as per the requirement.

```sql
db1 schema: create schema db1;
Reports schema: create schema <schema_name>;
```

Here <schema_name> will be the schema name of reportsdb.