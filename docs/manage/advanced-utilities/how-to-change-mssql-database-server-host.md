{% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}  
* Close OM4ADO application before execution of the utility.
{% endif %}  
{% if "OpsHub Integration Manager" === space.vars.SITENAME %}
* Stop OpsHub Server Service before execution of the utility.
{% endif %} 
* Go to <code class="expression">space.vars.SITENAME</code>'s `<Installation Folder>/Other_Resources/Resources` 
* Unzip `HostChange.zip`  
{% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}  
* Open Command Prompt with administrator privileges and go to <code class="expression">space.vars.SITENAME</code>'s directory `<Installation Folder or OM4ADO>/Other_Resources/Resources/HostChange` using command  **`cd <Installation Folder or OM4ADO>/Other_Resources/Resources/HostChange`**
{% endif %}
{% if "OpsHub Integration Manager" === space.vars.SITENAME %}
* Open Command Prompt with administrator privileges and go to <code class="expression">space.vars.SITENAME</code>'s directory `<Installation Folder or OpsHub>/Other_Resources/Resources/HostChange` using command  **`cd <Installation Folder or OpsHub>/Other_Resources/Resources/HostChange`**
{% endif %}
* Run `HostChange.bat` for Windows system. {% if "OpsHub Integration Manager" === space.vars.SITENAME %} In case of linux system, run HostChange.sh {% endif %}

* Enter the path for {% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %} OM4ADO{% endif %} {% if "OpsHub Integration Manager" === space.vars.SITENAME %} OpsHub {% endif %} Installation Directory

<p align="center">
  <img src="../../assets/initial.png">
</p>

## HostChange with MYSQL

* Enter the new Host Name for MYSQL: 

<p align="center">
  <img src="../../assets/Mysql1.png">
</p>

* If the Host Name input is not entered in the above step, then user will get the notification mentioned in the screen shot below. As the Host Name is a mandatory input that defines the new Host Name you want <code class="expression">space.vars.SITENAME</code> database to refer to: 

<p align="center">
  <img src="../../assets/Mysql2.png">
</p>

* Enter the Port for MYSQL:

<p align="center">
  <img src="../../assets/Mysql3.png">
</p>

* If the Port input is not entered in the above step, then utility will use the existing Port [entered at a time of <code class="expression">space.vars.SITENAME</code> installation]. If that is not the case, then enter the Port here:

<p align="center">
  <img src="../../assets/Mysql4.png">
</p>

* Utility will check the connection with new Host Name: 

<p align="center">
  <img src="../../assets/Mysql5.png">
</p>

## HostChange with ORACLE

* Enter the new Host Name for ORACLE:

<p align="center">
  <img src="../../assets/Oracle21.png">
</p>

* If the Host Name input is not entered in the above step, then user will get the notification mentioned in the screen shot below. As the Host Name is a mandatory input that defines the new Host Name you want <code class="expression">space.vars.SITENAME</code> database to refer to:  

<p align="center">
  <img src="../../assets/Oracle22.png">
</p>

* Enter the Port for ORACLE:

<p align="center">
  <img src="../../assets/Oracle33.png">
</p>

* If the Port input is not entered in the above step, then utility will use the existing Port [entered at the time of <code class="expression">space.vars.SITENAME</code> installation]. If that is not the case, then enter the Port here:

<p align="center">
  <img src="../../assets/Oracle44.png">
</p>

* Utility will check the connection with new Host Name:   

<p align="center">
  <img src="../../assets/Oracle55.png">
</p>

## HostChange with MSSQL Server

* **Note**: If <code class="expression">space.vars.SITENAME</code> is installed with Windows Authentication mode, then before running the utility, the user needs to make sure that the user who is logged into the Windows [where the <code class="expression">space.vars.SITENAME</code> is installed] also logs into the new host's MSSQL instance with the same credentials.

* Enter the new Host Name for MSSQL Server: 

<p align="center">
  <img src="../../assets/MssqlSer1.png">
</p>

* If the Host Name input is not entered in the above step, then user will get the notification mentioned in the screen shot below. As the Host Name is a mandatory input that defines the new Host Name you want <code class="expression">space.vars.SITENAME</code> database to refer to: 

<p align="center">
  <img src="../../assets/MssqlSer2.png">
</p>

* If the new Host Name is a named instance, then there is no input required for the Port. Hence, after entering the Host Name, utility will check the connection with the new Host:

<p align="center">
  <img src="../../assets/MssqlSer3.png">
</p>

* If the new Host Name is a non-named instance, then enter the Port for MSSQL:

<p align="center">
  <img src="../../assets/MssqlSer4.png">
</p>

* If the Port input is not entered in the above step, then utility will use the existing Port [entered at the time of <code class="expression">space.vars.SITENAME</code> installation]. If that is not the case, then enter the Port here:

<p align="center">
  <img src="../../assets/MssqlSer5.png">
</p>

* Utility will check the connection with new Host Name [In the case of SQL Authentication]:

<p align="center">
  <img src="../../assets/MssqlSer6.png">
</p>

* Utility will check the connection with new Host Name [In the case of Windows Authentication]:

<p align="center">
  <img src="../../assets/MssqlSer7.png">
</p>

## HostChange with PostgreSQL

* Enter the new Host Name for PostgreSQL:

<p align="center">
  <img src="../assets/postgresql1.png">
</p>

* If the Host Name input is not entered in the above step, then user will get the notification mentioned in the screenshot below. The Host Name is a mandatory input that defines the new Host Name user wants <code class="expression">space.vars.SITENAME</code> database to refer to:

<p align="center">
  <img src="../assets/postgresql2.png">
</p>

* Enter the Port for PostgreSQL:

<p align="center">
  <img src="../assets/postgresql3.png">
</p>

* If the Port's input is not entered in the above step, then the utility will use the existing Port [entered at the time of <code class="expression">space.vars.SITENAME</code> installation]. If that is not the case, enter the Port as shown in the screenshot below:

<p align="center">
  <img src="../assets/postgresql4.png">
</p>

* Utility will check the connection with the new Host Name:

<p align="center">
  <img src="../assets/postgresql5.png">
</p>




