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

### Collation Considerations

#### For Multiple Language Systems

If your end systems support multiple language characters, it's essential to choose a collation that supports **UTF** characters.

To enable UTF character support in **OpsHub Integration Manager**, install it on **Microsoft SQL Server 2019 or above**.

Select a collation with a `UTF` postfix, for example:

- `Latin1_General_100_CS_AS_SC_UTF8`

#### For Single Language Systems

If your end systems use a single language and your selected collation includes all necessary characters and is supported in **SQL Server versions below 2019**, you can install on SQL Server below 2019.

Select an appropriate collation that suits your end systems (which will be configured in **OpsHub Integration Manager**).

This guide may help you decide the right collation.

> **Note:**  
> We need **1 database** and **2 schemas** to be created manually.  
> The **database and schema name must be the same** for the OpsHub database, and another schema should be created for **reportsdb**.

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

### Notes

- Ensure both `db1` and `reportsdb` users have the required privileges.
- For system and object privileges, refer to [Database Prerequisites](prerequisites.md#database-prerequisites).
- `db1` and `reportsdb` must be created on the same server.
- Passwords for `db1` and `reportsdb` must match the Oracle server password.

### To change the tablespace quota for `db1`:

```sql
ALTER USER db1 QUOTA <size_of_tablespace> ON users;
```
> **Note:** `"db1"` and `"reportsdb"` are the database/schema/database user names used in the above queries.  
> You can name them differently as per your requirements.

## Queries for PostgreSQL Database

- In case of manual database creation for a PostgreSQL Server database, **database and schema names must be in lowercase** only.
- You need to manually create **1 database and 2 schemas**:
  - The **database and one schema** must have the **same name** (used for OpsHub database).
  - The second schema is used for `reportsdb`.

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

> The above query will create a database with **Collate: United States, UTF-8**.  
> To create the database with a different collation, update the `LC_COLLATE` and `LC_CTYPE` values as per your requirement.

```sql
db1 schema: create schema db1;
Reports schema: create schema <schema_name>;
```

Here <schema_name> will be the schema name of reportsdb.