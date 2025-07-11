If the user needs to change the collation of OpsHub Integration Manager's database, follow the below-mentioned steps:

**Important Note**
* When changing the collation, compare the code pages of the old and new collations to ensure that character representations are consistent and prevent data conversion issues. For example, changing Turkish_CS_AS collation to Latin1_General_CS_AS will convert "ı"(dott-less i) to "i".
* When considering a collation change, it's important to be aware about variations in character encoding and sorting rules between the old and new collation settings. Character conversion will occur during the process of collation change as mentioned in the above example. This conversion can lead to the irreversible loss of the original data.

**Procedure:**
1. **Stop the OpsHub Integration Manager Server**: Ensure the OpsHub Integration Manager server is not running.  
2. **Database Backup**: Take a backup of the database.  
3. **Download Scripts**: Download the provided script by clicking [ here](https://opshubtrial-my.sharepoint.com/:u:/g/personal/support_opshub_com/EeqVoEYk3gVHsQT8Y4_CrRsB_SkllsEiDWv1YrEbLEfbDw?e=VLcoFu).  
4. **SQL Editor**: Open the SQL editor.  
5. **Changing the columns collation**: Open the **Migration Script** file and replace `YOUR_COLLATION_NAME` with the collation name you would like to migrate to as the new collation. Execute the **Migration Script** and copy the generated SQL statements. Open a new window in SQL editor, paste those statements and execute them.  
6. **Database collation change**: Open the **Database Collation Change Script** file and replace `YOUR_COLLATION_NAME` with the collation name you would like to migrate to as the new collation. Also, replace `YOUR_DATABASE_NAME` with the name of the database on which OpsHub Integration Manager is installed. Execute the script file.  
7. **Start OpsHub Integration Manager Server**: Restart the OpsHub Integration Manager server.
