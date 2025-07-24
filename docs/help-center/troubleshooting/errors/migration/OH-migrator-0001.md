# Description

When you encounter OH-Migrator-0001, then following error message will appear:

The following error occurred while executing this line: `<lines>`

OH-Migrator-0001: Upgradation failed.

For upgradation logs, please refer Migration.log file located at `<installation path\AppData\logs>`  
To restore the application to the previous state [i.e. the state before upgradation], please restore the application folder and database backup that was taken before the upgrade started.

# Cause

This error primarily occurs when OpsHub Integration Manager is not able to establish connection to the database that was used to configure  
database connection details. Following are some of the cases in which this error can occur:

1. If the database user password has expired.  
2. If the database user does not have permission to access the database.

# Solution

Please check the Migration.log file located under the logs folder in the OpsHub Integration Manager installation path. This file contains all the step wise details of migration process. The exact cause of the failure should be found at the end of the file.

In case the password has expired, reset the same password which was used during installation.

In case the error is due to some permission issue, make sure you have provided the appropriate permissions on the database. Please refer [Database Prerequisites](../getting-started/prerequisites.md#database-prerequisites).
