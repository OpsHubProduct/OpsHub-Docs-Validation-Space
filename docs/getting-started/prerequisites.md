# prerequisites

## Deployment Options

* **On Premise**: Can be deployed on local virtual machine or local server
* **On OpsHub Cloud**: Can be deployed on Azure environment provided by OpsHub. This will come at an additional cost, which can be discussed with your point of contact in the support or sales team.
* **On Customer Cloud**: Can be deployed on cloud service hosted by customer. Supported cloud service on which it can be deployed are:
  * Amazon EC2
  * Azure

Following are the Operating System (OS) and hardware pre-requisites for server or VM where OpsHub Integration Manager is installed.

## Supported Operating Systems

### Windows

* Windows Server 2008 R2 and above (64 bit)
* For Windows specific configuration, refer [Windows specific configuration](prerequisites.md#windows-specific-configuration)

### Linux

* RHEL 5.2 and above (64 bit)
  * RHEL includes Cent OS and Fedora
* Ubuntu 22.04 and above

## Hardware Prerequisites

1. RAM - 8 GB & above
2. Disk space - 50 GB (Recommended)
3. Database Disk Space - 15 GB (Recommended)
4. Cores - Quadcore (Recommended)

## Database Prerequisites

OpsHub Integration Manager can be deployed with an embedded database; however, for production deployment or anything other than functional testing, our experts highly recommend using an external database. OpsHub Integration Manager supports the following database.

### 1. MySQL Server

{% include "../.gitbook/includes/mysql-preq.md" %}

### 2. MS SQL/Azure SQL Server

{% include "../.gitbook/includes/mssql-preq.md" %}

### 3. Oracle

{% include "../.gitbook/includes/oracle-preq.md" %}

### 4. PostgreSQL Server

{% include "../.gitbook/includes/posgres-preq.md" %}

> **Note**: If default connection timeout parameter is changed for any database server, then it must be confirmed that sufficient connection timeout has been set.\
> For example, for MySQL the default server-side connection timeout is 8 hours.\
> If it is changed and set to, say, 5 minutes, then the default server-side connection timeout must be updated accordingly.

**OpsHub Integration Manager** maintains connection pools that keep connections alive for 8 hours.\
Based on the need, this parameter can be tuned at both the application and database-server levels.\
**Generally, the recommended timeout is between 6–8 hours.**

## Download Database Connector jar

| Database Type  | Database Version | Download Link                                                                                                               |
| -------------- | ---------------- | --------------------------------------------------------------------------------------------------------------------------- |
| **MySQL**      | All              | [MySQL Connector/J](https://dev.mysql.com/downloads/connector/j)                                                            |
| **MS SQL**     | 2012 and lower   | [Download Link](https://www.microsoft.com/en-in/download/details.aspx?id=11774)                                             |
|                | 2014 onward      | [Release Notes](https://learn.microsoft.com/en-us/sql/connect/jdbc/release-notes-for-the-jdbc-driver?view=sql-server-ver16) |
| **Oracle**     | 11g              | [Oracle JDBC 11g](https://www.oracle.com/jp/technical-resources/articles/features/jdbc/jdbc.html)                           |
|                | 12c              | [Oracle JDBC 12c](https://www.oracle.com/technetwork/database/features/jdbc/jdbc-drivers-12c-download-1958347.html)         |
|                | 19c              | [Oracle JDBC 19c](https://www.oracle.com/database/technologies/appdev/jdbc-ucp-19c-downloads.html)                          |
| **PostgreSQL** | All              | [PostgreSQL JDBC](https://jdbc.postgresql.org/download/)                                                                    |

## HostName for OpsHub Integration Manager

* If machine/instance where OpsHub Integration Manager deployed is binded with any hostname (Net, Host, Gateway, or Domain name) then please make sure the hostname (Net, Host, Gateway, or Domain name) is a text string up to 24 characters drawn from the alphabet (A-Z), digits (0-9), minus sign (-), and period (.).\
  Note that periods are only allowed when they serve to delimit components of "domain style names". For more details, read the memo [RFC-921](https://tools.ietf.org/html/rfc921) and [RFC-952](https://tools.ietf.org/html/rfc952).

Once you have downloaded the application and configured the pre-requisite, click [Installation Steps](installation.md) to see how to get started.

## Port Prerequisites

For successful installation/upgradation of OpsHub Integration Manager, following ports are required to be available as per the chosen configuration and database.

### Http Port

* **8989**: If you are installing OpsHub Integration Manager with HTTP.
* **8443**: If you are installing OpsHub Integration Manager with HTTPS.

### Database Port

* **9001**: If you are installing OpsHub Integration Manager with HSQL database.

> **Note**: Apart from the above ports, some connectors require certain ports to be available. Please refer the [Connectors](../connectors/connectors.md) section to check ports used by specific connectors.

## Appendix

### Windows specific configuration

{% include "../.gitbook/includes/windows-specific-configuration.md" %}
