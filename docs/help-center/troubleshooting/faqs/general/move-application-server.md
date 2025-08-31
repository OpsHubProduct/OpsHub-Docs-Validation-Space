# Description

I have {{SITENAME}}installed on one machine. Now, I want to move {{SITENAME}}from that machine to another machine. How can I do this migration?

# Solution

### Assumptions

1. Username and password of old and new database instances are known to you.  
2. You have the password of systems users configured in OpsHub Integration Manager.  
3. These steps are applicable for the same database type. For example, if your {{SITENAME}}database is on MySQL, then you can move it to another instance of MySQL (not to a different database type).  
4. Make sure your old and new database versions are the same. For example, if {{SITENAME}}is installed on MySQL 5.6, then your new database MySQL instance should also be MySQL 5.6.  
5. Database name of old and new server is the same.  

### Steps

1. Inactivate all integrations.  
2. Stop the {{SITENAME}}server.  
3. Take application and database backup.  
   - **Application backup:** For details, refer to [Application Backup](../../../manage/upgrade/taking-application-backup.md#database-backup).  
   - **Database backup:** For details, refer to [Database Backup](../../../manage/upgrade/taking-application-backup.md#application-backup).  
   - Ensure both backups are completed properly. Without backups, failed steps cannot be recovered.  
4. Remove the data of the old instance.  
   - After taking database backup, drop the database.  
   - Uninstall {{SITENAME}}from the old machine.  
5. Install the same version of {{SITENAME}}on the new machine. During installation, select the database server where you want your {{SITENAME}}database.  
   - Ensure the database name matches the old installation.  
   - If your old instance used a custom database name (other than `opshub` or `reportsdb`), make sure to use the same custom name here.  
   - Refer to [Database Custom Configuration](../../../../getting-started/installation.md#opshub-database-custom-configuration) for details on selecting the database name during installation.  
6. If installation fails:  
   - Review the error message in `<Install_Folder>/logs/install.log`.  
   - Resolve the issue, clean the failed installation folder, and reinstall.  
   - If unresolved, send `<Install_Folder>/logs` to OpsHub support and restore the previous instance:  
     - Restore the application folder ([Application Restore](../../../manage/upgrade/taking-application-backup.md#application-restore)).  
     - Restore the database ([Database Restore](../../../manage/upgrade/taking-application-backup.md#database-restore)).  
7. If installation succeeds:  
   - Stop the {{SITENAME}}server.  
   - Restore the database(s) from the backup into the new database instance/server ([Database Restore](../../../manage/upgrade/taking-application-backup.md#database-restore)).  
   - Start the {{SITENAME}}server.  
   - Re-enter the password for sync users configured in systems and integrations.  
   - Load field mapping and integrations to validate connectivity.  
8. Finally, activate integrations as per your requirements.  
