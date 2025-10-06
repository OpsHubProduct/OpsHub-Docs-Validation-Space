# How to switch to Windows Authentication Mode for MSSQL Server

Please go through the section [Installation Prerequisites](../../getting-started/prerequisites.md#windows) for Windows Authentication mode before executing steps given below.

Please ensure the Windows user (who is used in MS SQL Windows Authentication) has **Read** and **Write** privileges before executing `databaseManagementUtlity`. You can grant the **Read** and **Write** privileges by executing the steps given below.

- Open properties window of <code class="expression">space.vars.SITENAME</code> installation folder (directory in which you have installed <code class="expression">space.vars.SITENAME</code> i.e. `c:\Program Files\OpsHub`), it will show you the dialogue box shown below.  
- Select the user (to whom you want to grant privileges) from the Security tab and check Read and Write checkbox.  
- Click OK after checking the Read and Write checkbox.

<p align="center">
  <img src="../../assets/Switching_Image_1.png">
</p>

If the database is on MSSQL SQL Authentication mode and you need to switch to Windows Authentication mode, then follow the steps given below:

- Go to `<Installation Folder>/Other_Resources/Resources`.  
- Unzip `OpsHub Database Management utility.zip`.  
- Run `DatabaseManagementUtility.bat` for Windows system.  
  {% if "OpsHub Integration Manager" === space.vars.SITENAME %}
- In case of Linux system, run `DatabaseManagementUtility.sh`.*
  {% endif %}

- Enter path for the installation directory.

<p align="center">
  <img src="../../assets/Switching_Image_2.png">
</p>


- Press `2` to switch to Windows authentication mode.

<p align="center">
  <img src="../../assets/Switching_Image_3.png">
</p>

- Provide Microsoft JDBC Driver 4.0 (`tar.gz`) File Path.

<p align="center">
  <img src="../../assets/Switching_Image_4.png">
</p>


- Provide Windows Service Credentials.
<p align="center">
  <img src="../../assets/Switching_Image_5.png">
</p>

> **Note:**  
> If Windows credentials are not added correctly during switching, the OpsHub Server service will not be started.  
> To avoid such an occurrence, the user will have to manually set the service log-on credentials for OpsHub Server Service in case wrong Windows credentials are added at the time of switching.

## Follow the below mentioned steps to set the credentials in the OpsHub Server Services:

1. Open the services application and search for `OpsHub Server Service`.  
2. Right-click on the service, select **Properties** and go to the **Log On** Tab.  
3. Enter Windows credentials in **This account**.  

> If the user is registered with a domain, the username format will be "{username}@{domain}" or "{domain}\{username}". Otherwise, the username format will be ".\username".

<p align="center">
  <img src="../../assets/OpshubServerServiceCredentials.png">
</p>




