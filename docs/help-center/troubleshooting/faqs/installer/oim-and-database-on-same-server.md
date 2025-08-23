## Description

{{SITENAME}} supports 4 types of databases: HSQL, MYSQL, MSSQL, ORACLE, PostgreSQL. Among these, HSQL is the in-built database provided with {{SITENAME}}.  
However, you can use one of the other external databases like MYSQL, MSSQL, ORACLE, or PostgreSQL. So in such case, is it necessary to install the {{SITENAME}} on the same machine where the database is hosted?

## Solution

It is not mandatory to have the database on the same machine where {{SITENAME}} is installed. They can reside on different machines as long as  [database pre-requisites](../../../../getting-started/installation.md#database-prerequisites) and  [hardware pre-requisites](../../../../getting-started/installation.md#hardware-prerequisites) are fulfilled for them. The machine on which {{SITENAME}} is installed should be able to access the machine on which the database has been placed.  
It is better to have strong connectivity to the database machine to ensure smooth performance of {{SITENAME}}.

> **Note**: Installation of {{SITENAME}} with HSQL database will automatically create the database on the same machine, as HSQL is the default embedded database of {{SITENAME}}.



