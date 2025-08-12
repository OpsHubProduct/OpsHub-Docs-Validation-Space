
* If {{SITENAME}} database password has been modified by a user, then this utility would update the new password in **{{SITENAME}}** application.

Follow the steps given below for updating database password in OpsHub:

{{#if product == "OIM"}}
* Stop OpsHub Server/ Service before execution of this utility.
{{/if}}

{{#if product == "OM4ADO"}}
* Close OM4ADO application before execution of the utility.
{{/if}}

* Go to `<{{SITENAME}} Installation Folder>/Other_Resources/Resources`.
* Unzip `OpsHub Database Management utility.zip`.
* Run `OpsHubDatabaseManagementUtility.bat` for Windows system.  
  {{#if product == "OIM"}}In case of Linux system, run `OpsHubDatabaseManagementUtility.sh`.{{/if}}
* Enter path for OpsHub Installation Directory.

<p align="center">
  <img src="../../assets/Updating_Database_Password_Image_1.png">
</p>


* Enter the new database password.

<p align="center">
  <img src="../../assets/Updating_Database_Password_Image_2.png">
</p>


* This would update database password in OpsHub application.

<p align="center">
  <img src="../../assets/Updating_Database_Password_Image_3.png">
</p>



