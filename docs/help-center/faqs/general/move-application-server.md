# Description

I have <code class="expression">space.vars.SITENAME</code> installed on one machine. Now, I want to move <code class="expression">space.vars.SITENAME</code> from that machine to other machine. How can I do this migration?

# Solution

## Assumptions

1. Username and password of old and new database instances is known to you.  
2. You have the password of systems users configured in <code class="expression">space.vars.SITENAME</code>.  
3. These steps are applicable for same database type, for example, if your <code class="expression">space.vars.SITENAME</code> database is on MySQL, then you can move it to other instance of MySQL (not to any other database type).  
4. Make sure your old and new database versions are also same. For example, if your <code class="expression">space.vars.SITENAME</code> is installed on MySQL 5.6, then your new database MySQL instance should also have that same version.  
5. Database name of older and newer server is same.  

## Steps

{% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}  
1. Stop all migrations.  
{% endif %}   
{% if "OpsHub Integration Manager" === space.vars.SITENAME %}  
1. Inactivate all integrations.  
{% endif %}  
{% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}
2. Close <code class="expression">space.vars.SITENAME</code>.  
{% endif %}
{% if "OpsHub Integration Manager" === space.vars.SITENAME %}
2. Stop the <code class="expression">space.vars.SITENAME</code> server.  
{% endif %}
3. Take application and database backup:
   * Take Application backup. For more information on how to take application backup, refer [Application Backup](../../../manage/upgrade/taking-application-backup.md#application-backup).
   * Take Database backup. For more information on how to take database backup, refer [Database Backup](../../../manage/upgrade/taking-application-backup.md#database-backup). 
   * Make sure you have taken application and database backup properly. If you miss this backup and any of the subsequent steps fail, then you won't be able to restore the application.
4. Remove the data of the old instance:
   * After taking database backup, drop the database.
   * Uninstall <code class="expression">space.vars.SITENAME</code> from the older instance.
5. Install the same <code class="expression">space.vars.SITENAME</code> version on the machine where you want to move <code class="expression">space.vars.SITENAME</code> server. During installation, select the database server where you want your <code class="expression">space.vars.SITENAME</code> database. While configuring installation, make sure database name is same as old installation. If your old <code class="expression">space.vars.SITENAME</code> instance database name is custom (other than 'opshub' and 'reportsdb'), then make sure in this new installation the database name remains the same.
{% if "OpsHub Integration Manager" === space.vars.SITENAME %}  
   * You can refer [OpsHub Database Custom Configuration](../../../getting-started/installation.md#opshub-database-custom-configuration)  documentation for selecting database name during installation time. 
{% endif %}
6. If for any reason, installation failed, follow the steps below:  
   * See installation fail error and try to resolve it. You can also refer logs to get more error information on this error. Navigate `<Install_Folder>/logs` folder and see `install.log` file.  
   * Once you find the error and resolve it, re-install the application. First clean the installation folder on which installation failed and then re-install it on the same folder.  
   * If you are not able to resolve this error, then send the `<Install_Folder>/logs` folder to <code class="expression">space.vars.SITENAME</code> support team. Restore application to earlier state until this issue is fixed:
   * Restore applicable folder by following [Application Restore](../../../manage/upgrade/taking-application-backup.md#application-restore) documentation.
   * Restore database by following [Database Restore](../../../manage/upgrade/taking-application-backup.md#database-restore) documentation.  
7. If installation finished successfully, follow the steps below:  
{% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}  
   * Close <code class="expression">space.vars.SITENAME</code>.
{% endif %}  
{% if "OpsHub Integration Manager" === space.vars.SITENAME %}  
   * Stop the <code class="expression">space.vars.SITENAME</code>.
{% endif %}
   * Restore the database(s) from the backup taken from old <code class="expression">space.vars.SITENAME</code> instance/server into the new <code class="expression">space.vars.SITENAME</code> database instance/server. For more information, refer [Database Restore](../../../manage/upgrade/taking-application-backup.md#database-restore).
   * Start new <code class="expression">space.vars.SITENAME</code> server. 
   * Re-enter the password for sync user configured in systems
{% if "OpsHub Integration Manager" === space.vars.SITENAME %}
and integration {% endif %}
   {% if "OpsHub Integration Manager" === space.vars.SITENAME %}  
   * Load field mapping and integration to validate connectivity.
   {% endif %}
{% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}  
8. Now you can start migrations  as per your requirement.
{% endif %}  
{% if "OpsHub Integration Manager" === space.vars.SITENAME %}
8. Now you can activate integrations as per your requirement.
{% endif %}