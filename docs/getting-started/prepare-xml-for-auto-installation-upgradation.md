Here is the process of getting and customizing OpsHubAutoInstall/OpsHubAutoMigrator XML file.  

# <div id="download-xml-file"> 1 - Download XML file </div>  

Below are the sample templates for OpsHubAutoInstall/OpsHubAutoMigrator XML. You need to customize the template downloaded as described below for configuring your own file for installing or migrating <code class="expression">space.vars.SITENAME</code>.


* If you are installing <code class="expression">space.vars.SITENAME</code> then download file [here](https://opshubtrial-my.sharepoint.com/:u:/g/personal/support_opshub_com/EdwkmbjVf5RNpjHmsqi8dE4BaSfch1pFlGQhPsixpGnHEw?e=VJclvQ)
    * To customize the file as per your configuration, follow steps from section [step 3 - Configure Installation path](#id-3-configure-installation-path).
* If you are upgrading the existing <code class="expression">space.vars.SITENAME</code> then download file [OpsHubAutoMigrator.xml](https://opshubtrial-my.sharepoint.com/:u:/g/personal/support_opshub_com/EW_r0v_m5RtPoQp-jGLitoMBfWzZDdB0zdpJxflswG4a2Q).  
    * To customize the file as per your configuration, follow steps **step 3 and step 4**.  

>**Note**: Refer to [step 2](#customized-example-of-xml-file-with-mysql-database) for example of an already customized file for **installation with MySQL database**.
  

>**Note**: It is always recommended to have a secured environment for OIM installation. The purpose of Silent installation is to have no manual intervention, and so the user needs to have a secured VM installation as the autoinstall.xml file contains the password in plain text.  

# <div id="customized-example-of-xml-file-with-mysql-database"> 2 - Customized example of xml file with MySQL database </div>

* Here are the examples of XML file after all modifications.  
   * Installation with MySQL Database : [Installer Example file](https://opshubtrial-my.sharepoint.com/:u:/g/personal/support_opshub_com/ETH4fCuE0VBBvBucTLI8DtIBl9MlETKWMF3Y1eup2XjuGQ?e=c9TvS4) 
   * Upgrade : [Migrator example file](https://opshubtrial-my.sharepoint.com/:u:/g/personal/support_opshub_com/EY22j0v_TdFGsCLzrxWEy1IBb8mZXapO2a8po-mPix1R8A?e=N8oyFe)


# <div id="configure-installation-path"> 3 - Configure Installation Path </div>

* Find `com.izforge.izpack.panels.TargetPanel` and replace the input mentioned below:  
    * Replace **@INSTALLATION_PATH@** with actual installation directory which you mentioned in **Registration_Input.properties** during [Silent Registration](registration#silent-registration-for-linux).  


# <div id="configure-registration-type-and-verification-code"> 4 - Configure Registration Type & Verification Code </div>

For the next panel:
```xml
<com.izforge.izpack.panels.UserInputPanel id="UserInputPanel.RegistrationTypeSelection">
```
There are two possible Registration Types, and the required input for the verification code will differ based on your choice. We have listed both scenarios below, along with the inputs you need to provide:

1. Existing Registration (during installation)
By default, OpsHub uses Existing Registration as the registration type. If you want to continue with this option, you need to provide the following inputs:

```xml
<com.izforge.izpack.panels.UserInputPanel id="UserInputPanel.RegistrationTypeSelection">
<userInput> <entry key="RegistrationType" value="ExistingRegistration"/>
</userInput> </com.izforge.izpack.panels.UserInputPanel>

<com.izforge.izpack.panels.UserInputPanel id="UserInputPanel.EmailIdVerificationForExistingCode">
<userInput> <entry key="VerificationCode" value="@VERIFICATION_CODE@"/>
</userInput> </com.izforge.izpack.panels.UserInputPanel>
```
>**Note**: Replace @VERIFICATION_CODE@ with the verification code that you received on your registered business email address

2. Post Registration (after installation)
For Post-Installation Registration, set the input value of "RegistrationType" to PostInstallRegistration.

```xml
 <com.izforge.izpack.panels.UserInputPanel id="UserInputPanel.RegistrationTypeSelection">
<userInput> <entry key="RegistrationType" value="PostInstallRegistration"/> </userInput>
</com.izforge.izpack.panels.UserInputPanel>
```

>**Note**: Complete the installation first, and after the server starts, you will be prompted to fill out the registration form. You will receive the verification code only after completing the registration form.

# <div id="configure-base-parameter"> 5 - Configure Base Parameter </div> 

Find all parameters below under panel `id="UserInputPanel.installationflow"`.  
1. Find **@COMPANY_NAME@** parameter in the OpsHubAutoInstall.xml file and replace with your company name.  
2. Find **@DB_TYPE@** and replace database type as below:  
   * Replace with "MySQL" for configuring MySQL database. Refer to [MySQL Database configuration](#mysql-database-configuration) for detailed steps.  
   * Replace with "MS SQL Server" for configuring MS SQL database. Refer to [MSSQL Database configuration](#mssql-database-configuration) for detailed steps.  
   * Replace with "ORACLE" for configuring Oracle database. Refer to [Oracle Database configuration](#oracle-database-configuration) for detailed steps.  
   * Replace with "HSQLDB" for configuring HSQL database. Refer to [HSQL Database configuration](#hsql-database-configuration) for detailed steps.  
   * Replace with "PostgreSQL" for configuring PostgreSQL database. Refer to [PostgreSQL Database configuration](#postgresql-database-configuration) for detailed steps.  
3. Find **@ADVANCE_CONFIG_FLAG@** and replace with either "1" if you want to configure advance parameter or "0" if you don't want to configure advance parameters.  
   >**Note**: Advance configuration allows to change default database name, Http/Https configuration, Advanced Security Options.  
   - If you are setting above flag as "0" then advance configuration parameters will be set with default values.  

# <div id="database-configuration"> 6 - Database configuration </div>  

## MySQL Database configuration  

1. Find panel with id **"UserInputPanel.mysqldb"**.  
2. Remove comment from parameters.  
3. Go to [Common Database configuration parameters](#common-database-configuration-parameters) and follow the steps.  

## Common Database Configuration Parameters

1. Find and replace **@DB_HOST@** with the host name of your database.  
2. Find and replace **@DB_PORT@** with the port of your database.  
3. Find and replace **@DB_USER@** with the username of your database.  
4. Find and replace **@DB_PASSWORD@** with the password of your database.  
5. Find and replace **@DB_CONNECTOR_JAR_PATH@** with the jar file path of your database connector. Find the jar file name according to the database you are using.  
   * For MySQL, refer section [Installation with MySQL Server](installation.md#installation-with-mysql-server) 
   * For MS SQL, refer section [Installation with MSSQL Server](installation.md#installation-with-mssql-server)  
   * For ORACLE, refer section [Installation with Oracle](installation.md#installation-with-oracle)  
   * For HSQL, no external connector jar file is required.  
   * For PostgreSQL, refer section [Installation with PostgreSQL](installation.md#installation-with-postgresql)  
   >**Note**: The user who is running the installer should have 'Read' access to the jar file of your database connector.  

## MSSQL Database configuration  

### Installation on Windows  

#### With Windows authentication  

1. Find panel with id **"UserInputPanel.mssqlAuthModeOnWindows"**.  
2. Remove comment from parameters.  
3. Find **@DB_AUTH_TYPE@** in the same panel.  
4. Replace variable value with "Windows Authentication" if you are configuring MSSQL with Windows Authentication.  
5. Find panel with id **"UserInputPanel.mssqldbOnWindowsAuth"**.  
6. Remove comment from parameters.  
7. Go to [Common Database configuration parameters](#common-database-configuration-parameters) and follow the steps to replace **@DB_HOST@, @DB_PORT@, @DB_CONNECTOR_JAR_PATH@** with your input.  
8. Find and replace **@DB_NAME_TO_TEST_CONNECT@** with the database name to which database user has access to.  
   >**Note**: Go to [MS SQL/Azure SQL Server Database Name Input](installation.md#installation-with-ms-sql2fazure-sql-server) to find the usage.  

#### With SQL authentication  

1. Find panel with id **"UserInputPanel.mssqlAuthModeOnWindows"**.  
2. Remove comment from parameters.  
3. Find **@DB_AUTH_TYPE@** in the same panel.  
4. Replace variable value with "SQL Authentication" if you are configuring MSSQL with SQL Authentication.  
5. Find panel with id **"UserInputPanel.mssqldbOnSQLAuth"**.  
6. Go to [Common Database configuration parameters](#common-database-configuration-parameters) and follow the steps.  
7. Find and replace **@DB_NAME_TO_TEST_CONNECT@** with the database name to which database user has access to.  
   >**Note**: Go to [MS SQL/Azure SQL Server Database Name Input](installation.md#installation-with-ms-sql2fazure-sql-server)** to find the usage.  

#### Installation on Linux  

1. Find panel with id **"UserInputPanel.mssqlAuthModeOnLinux"**.  
2. Remove comment from parameters.  
3. Find **@DB_AUTH_TYPE@** in the same panel.  
4. Replace variable value with "SQL Authentication" if you are configuring MSSQL with SQL Authentication.  
5. Find panel with id **"UserInputPanel.mssqldbOnSQLAuth"**.  
6. Go to [Common Database configuration parameters](#common-database-configuration-parameters) and follow the steps.  
7. Find and replace **@DB_NAME_TO_TEST_CONNECT@** with the database name to which database user has access to.  
   >**Note**: Go to [MS SQL/Azure SQL Server Database Name Input](installation.md#installation-with-ms-sql2fazure-sql-server) to find the usage.  

## Oracle Database configuration  

1. Remove comment from panel id **"UserInputPanel.oracleDatabaseType"**.  
2. Find and replace **@ORACLE_DB_TYPE@** from the same panel with CDB or Non CDB depending upon your oracle database type. For reference follow section[Installation with Oracle](installation.md#installation-with-oracle).  
3. Find and replace **@ORACLE_CONNECTION_TYPE@** from the same panel with Service or SID depending upon your oracle configuration. For reference follow section [Installation with Oracle](installation.md#installation-with-oracle).  
4. Now, remove comment from panel id "UserInputPanel.oracledb".  
5. Find and replace **@ORC_INSTANCE@** with oracle database instance name from the same panel.  
6. Go to [Common Database configuration parameters](#common-database-configuration-parameters) and follow the steps.  

## HSQL Database configuration  

For HSQL you can move to next step for further configuration.  

## PostgreSQL Database configuration  

1. Find panel with id **"UserInputPanel.postgresqldb"**.  
2. Remove comment from parameters.  
3. Go to [Common Database configuration parameters](#common-database-configuration-parameters) and follow the steps.  

# <div id="enable-advance-configuration"> 7 - Enable Advance Configuration  </div>

If you are doing advance configuration then only follow the below step.  
- Make sure you have **@ADVANCE_CONFIG_FLAG@** flag is 1 as specified [here](#configure-base-parameter).  

## Enabling advance configuration with HSQL, then follow below steps  

1. Remove comment from panel id "UserInputPanel.advancedOptionsHSQL" and add comment in panel id **"UserInputPanel.advancedOptions"**.  
2. Find **@ADV_HTTP_CONFIG@** and replace it with "HTTP" if you want to configure <code class="expression">space.vars.SITENAME</code> with HTTP or replace it with "HTTPS" if you want to configure <code class="expression">space.vars.SITENAME</code> with https.  
   * Make sure you are following step no 8 if you configure <code class="expression">space.vars.SITENAME</code> with https.  
3. Find **@ADV_ISSERVICE@** and replace with 1 if you want to configure <code class="expression">space.vars.SITENAME</code> as a service else replace it with 0.  
4. Find **@ADV_SEC_CONFIG@** and replace with 1 if you want to configure advance Security configuration else replace it with 0.  

## Enabling advance configuration other than HSQL, then follow below steps  

1. Remove comment from id "UserInputPanel.advancedOptions".  
2. Find **@ADV_HTTP_CONFIG@** and replace it with "HTTP" if you want to configure <code class="expression">space.vars.SITENAME</code> with HTTP or replace it with "HTTPS" if you want to configure <code class="expression">space.vars.SITENAME</code> with https.  
   * Make sure you are following step no 8 if you configure <code class="expression">space.vars.SITENAME</code> with https.  
3. Find **@ADV_ISDBFLAG@** and replace with 1 if you will create <code class="expression">space.vars.SITENAME</code> database manually else set it as 0.  
4. Find **@ADV_OPSHUBDBMAME@** and replace it with your <code class="expression">space.vars.SITENAME</code> database name else remove that entry from the panel.  
5. Find **@ADV_REPORT_DBNAME@** and replace it with your <code class="expression">space.vars.SITENAME</code> report database name else remove that entry from the panel.  
6. Find **@ADV_ISSERVICE@** and replace with 1 if you want to configure <code class="expression">space.vars.SITENAME</code> as a service else replace it with 0.  
7. Find **@ADV_SEC_CONFIG@** and replace with 1 if you want to configure advance Security configuration else replace it with 0.  

# <div id="https-configuration"> 8 - HTTPS configuration </div>  

1. Make sure you have configure **@ADV_HTTP_CONFIG@** with "HTTPS" value.  
2. Find panel with id "UserInputPanel.certInfo" remove comment from parameters.  
3. Find **@CERT_SERVER_HOST@** and replace it with IP Address/hostname of Machine on which you install <code class="expression">space.vars.SITENAME</code>.  
4. Find **@CERT_COMP_UNIT@** and replace it with your Organization's Unit like Manufacturing, Sales etc.  
5. Find **@CERT_COMP_NAME@** and replace it with your Organization Name.  
6. Find **@CERT_COMP_CITY@** and replace it with your Organization's City.  
7. Find **@CERT_COMP_STATE@** and replace it with your Organization's State or Province.  
8. Find **@CERT_COMP_COUNTRY@** and replace it with your Organization's Country.  
9. Find **@CERT_VALIDITY@** and replace it with number of days for which the certificate should be considered valid.  

# <div id="advance-security-configuration"> 9 - Advance Security Configuration </div>  

1. Make sure you have configure ADV_SEC_CONFIG with "1" value in step 5.  
2. Find panel with id "UserInputPanel.securityConfig" remove comment from parameters.  
3. Find **@SEC_KEYMODE@** replace with "newSecretKey".  
4. Find **@SEC_KEY_PATH@** and replace with your secret key installation path.  
5. Find **@SEC_ALGO@** and replace with either "AES-256" or "DES-56 or "DESede-168" as per your need.  
6. Note do not copy your secret file once its generated after <code class="expression">space.vars.SITENAME</code> installation process.  
