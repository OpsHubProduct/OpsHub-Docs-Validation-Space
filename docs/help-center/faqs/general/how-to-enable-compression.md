## Description

* If the data size is too large for any table in the database, then the compression technique can be used to reduce the table size. This process increases the CPU's load. Hence the compression technique must be used wisely.  
* In <code class="expression">space.vars.SITENAME</code>, the OHMT_EAI_ENTITY_HISTORY_STATE table contains more storage than its utilization. Hence, compression can be applied here if the table size is too large at your end.

## Solution

### MSSQL
* **Prerequisites:**
  * Enterprise/Developer edition is needed to enable compression in MSSQL.

* **Query:**
```sql
ALTER TABLE table_name REBUILD PARTITION = ALL WITH (DATA_COMPRESSION = ROW);
```

### MYSQL
* **Query:**
```sql
ALTER TABLE table_name ROW_FORMAT = COMPRESSED;
```
### Oracle
* **Query:**
  - ```sql
    ALTER TABLE table_name COMPRESS;
    ```
    The above mentioned query will compress the new data only. It will not compress the existing data of the table. If you want to compress the existing data, then run the below mentioned queries. These will move data from the source table to a temporary table. Hence, the data will get compressed during the copy operation.  

    ```sql
    ALTER TABLE table_name MOVE NOCOMPRESS;
    ALTER TABLE table_name MOVE COMPRESS;
    ```

  - When you perform a move operation, you will have two copies of the table for a period of time. Here, it will compress the decompressed data in the temporary table and sync it back to the source table. Make sure you have enough storage to perform the compression operation.  

  - For more details please refer [here](https://oracle-base.com/articles/9i/compressed-tables-9i).  


