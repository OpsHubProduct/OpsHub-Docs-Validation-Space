* {{#ifeq: {{SITENAME}} | OpsHub Migrator for Microsoft Azure DevOps | Close OM4ADO application before execution of the utility |Stop OpsHub Server Service before execution of the utility  }}
* Go to `<{{SITENAME}} Installation Folder>/Other_Resources/Resources` 
* Unzip `HostChange.zip` 
* Open Command Prompt with administrator privileges and go to directory `<{{#ifeq: {{SITENAME}} | OpsHub Migrator for Microsoft Azure DevOps | OM4ADO | OpsHub}} Installation Folder>/Other_Resources/Resources/HostChange` using command  **`cd <{{#ifeq: {{SITENAME}} | OpsHub Migrator for Microsoft Azure DevOps | OM4ADO | OpsHub}} Installation Folder>/Other_Resources/Resources/HostChange`**
* Run `HostChange.bat` for Windows system. {{#ifeq: {{SITENAME}} | OpsHub Migrator for Microsoft Azure DevOps ||In case of linux system, run HostChange.sh }}

* Enter the path for {{#ifeq: {{SITENAME}} | OpsHub Migrator for Microsoft Azure DevOps | OM4ADO | OpsHub}} Installation Directory

<p align="center">
  <img src="../assets/initial.PNG">
</p>

## HostChange with MYSQL

* Enter the new Host Name for MYSQL: 

<p align="center">
  <img src="../assets/mysql1.PNG">
</p>

* If the Host Name input is not entered in the above step, then user will get the notification mentioned in the screen shot below. As the Host Name is a mandatory input that defines the new Host Name you want {{SITENAME}} database to refer to: 

<p align="center">
  <img src="../assets/mysql2.PNG">
</p>

* Enter the Port for MYSQL:

<p align="center">
  <img src="../assets/mysql3.PNG">
</p>

* If the Port input is not entered in the above step, then utility will use the existing Port [entered at a time of {{SITENAME}} installation]. If that is not the case, then enter the Port here:

<p align="center">
  <img src="../assets/mysql4.PNG">
</p>

* Utility will check the connection with new Host Name: 

<p align="center">
  <img src="../assets/mysql5.PNG">
</p>

## HostChange with ORACLE

* Enter the new Host Name for ORACLE:

<p align="center">
  <img src="../assets/oracle21.PNG">
</p>

* If the Host Name input is not entered in the above step, then user will get the notification mentioned in the screen shot below. As the Host Name is a mandatory input that defines the new Host Name you want {{SITENAME}} database to refer to:  

<p align="center">
  <img src="../assets/oracle22.PNG">
</p>

* Enter the Port for ORACLE:

<p align="center">
  <img src="../assets/oracle33.PNG">
</p>

* If the Port input is not entered in the above step, then utility will use the existing Port [entered at the time of {{SITENAME}} installation]. If that is not the case, then enter the Port here:

<p align="center">
  <img src="../assets/oracle44.PNG">
</p>

* Utility will check the connection with new Host Name:   

<p align="center">
  <img src="../assets/oracle55.PNG">
</p>

## HostChange with MSSQL Server

* **Note**: If {{SITENAME}} is installed with Windows Authentication mode, then before running the utility, the user needs to make sure that the user who is logged into the Windows [where the {{SITENAME}} is installed] also logs into the new host's MSSQL instance with the same credentials.

* Enter the new Host Name for MSSQL Server: 

<p align="center">
  <img src="../assets/mssqlSer1.PNG">
</p>

* If the Host Name input is not entered in the above step, then user will get the notification mentioned in the screen shot below. As the Host Name is a mandatory input that defines the new Host Name you want {{SITENAME}} database to refer to: 

<p align="center">
  <img src="../assets/mssqlSer2.PNG">
</p>

* If the new Host Name is a named instance, then there is no input required for the Port. Hence, after entering the Host Name, utility will check the connection with the new Host:

<p align="center">
  <img src="../assets/mssqlSer3.PNG">
</p>

* If the new Host Name is a non-named instance, then enter the Port for MSSQL:

<p align="center">
  <img src="../assets/mssqlSer4.PNG">
</p>

* If the Port input is not entered in the above step, then utility will use the existing Port [entered at the time of {{SITENAME}} installation]. If that is not the case, then enter the Port here:

<p align="center">
  <img src="../assets/mssqlSer5.PNG">
</p>

* Utility will check the connection with new Host Name [In the case of SQL Authentication]:

<p align="center">
  <img src="../assets/mssqlSer6.PNG">
</p>

* Utility will check the connection with new Host Name [In the case of Windows Authentication]:

<p align="center">
  <img src="../assets/mssqlSer7.PNG">
</p>

## HostChange with PostgreSQL

* Enter the new Host Name for PostgreSQL:

<p align="center">
  <img src="../assets/postgresql1.PNG">
</p>

* If the Host Name input is not entered in the above step, then user will get the notification mentioned in the screenshot below. The Host Name is a mandatory input that defines the new Host Name user wants {{SITENAME}} database to refer to:

<p align="center">
  <img src="../assets/postgresql2.PNG">
</p>

* Enter the Port for PostgreSQL:

<p align="center">
  <img src="../assets/postgresql3.PNG">
</p>

* If the Port's input is not entered in the above step, then the utility will use the existing Port [entered at the time of {{SITENAME}} installation]. If that is not the case, enter the Port as shown in the screenshot below:

<p align="center">
  <img src="../assets/postgresql4.PNG">
</p>

* Utility will check the connection with the new Host Name:

<p align="center">
  <img src="../assets/postgresql5.PNG">
</p>
