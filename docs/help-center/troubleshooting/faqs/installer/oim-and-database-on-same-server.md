## Description

<code class="expression">space.vars.SITENAME</code> supports 4 types of databases: HSQL, MYSQL, MSSQL, ORACLE, PostgreSQL. Among these, HSQL is the in-built database provided with <code class="expression">space.vars.SITENAME</code>.  
However, you can use one of the other external databases like MYSQL, MSSQL, ORACLE, or PostgreSQL. So in such case, is it necessary to install the <code class="expression">space.vars.SITENAME</code> on the same machine where the database is hosted?

## Solution

It is not mandatory to have the database on the same machine where <code class="expression">space.vars.SITENAME</code> is installed. They can reside on different machines as long as  [database pre-requisites](../../../getting-started/prerequisites.md#database-prerequisites) and  [hardware pre-requisites](../../../getting-started/prerequisites.md#hardware-prerequisites) are fulfilled for them. The machine on which <code class="expression">space.vars.SITENAME</code> is installed should be able to access the machine on which the database has been placed.  
It is better to have strong connectivity to the database machine to ensure smooth performance of <code class="expression">space.vars.SITENAME</code>.

> **Note**: Installation of <code class="expression">space.vars.SITENAME</code> with HSQL database will automatically create the database on the same machine, as HSQL is the default embedded database of <code class="expression">space.vars.SITENAME</code>.





