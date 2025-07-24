# Description

When you encounter OH-Migrator-0002, then following error message will appear:

The following error occurred while executing this line: `<lines>`

OH-Migrator-0002: Upgradation failed.

For upgradation logs, please refer Migration.log file located at `<installation path\AppData\logs>`  
To restore the application to the previous state [i.e. the state before upgradation], please restore the application folder and database backup that was taken before the upgrade started.

# Cause

This error occurs when the migration process fails to complete successfully.

# Solution

Following are the steps to recover from the failure, actual solution will be provided by OpsHub Integration Manager support team.

**Send error details to OpsHub Integration Manager Support**

These error details will be needed by support team to investigate the failure and provide solution.

1. Copy the data from OpsHub Integration Manager installation folder to another location.  
2. Share Migration.log file with OpsHub Integration Manager support. This file will be located at `<installation_path>/logs` folder.

**Restore the application to earlier state**

Since the migration has failed, OpsHub Integration Manager may not be in proper state to function. If you want to restore  
the previous state of the application till the solution is provided, follow the steps mentioned in section [How to Restore](../manage/upgrade/taking-application-backup.md#how-to-restore).
