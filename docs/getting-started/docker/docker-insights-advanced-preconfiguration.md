# Docker OpsHub Insights Pre-Configuration for Coverage

## Updating UserInput.json

Refer to [Docker Insights PreConfiguration](../getting-started/docker/docker-insights-preconfiguration.md) for detailed steps on configuring SCM and ALM systems' integrations.

For creating database system integration along with SCM and ALM systems' integrations, modify the **UserInput.json** file by adding the highlighted lines in **userjsons** folder of InsightsPreConfiguration as given below:

```json
{
  "listOfAnalyses": [
    {
      "scmSystem": "Git_systemUserProperties.json",
      "entitySystem": "ADO_systemUserProperties.json",
      "databaseSystem": "Database_systemUserProperties.json",
      "endSystemsAnalyses": {
        "CommitAnalysis": "CommitAnalysis.json",
        "ChangeImpactAnalysis": "ChangeImpactAnalysis.json",
        "EntityAnalysis": "EntityAnalysis.json",
        "EntityHistoryAnalysis": "EntityHistoryAnalysis.json",
        "DccAnalysis": "DccAnalysis.json",
        "DeltaImpactAnalysis": "DeltaImpactAnalysis.json"
      },
      "activateExtractions": 1
    }
  ]
}
```

---

## Configuring Database system User Properties json

Connection details like database username, password, database, schema, etc., are needed for configuring the Database system in **Database_systemUserProperties.json** file in **userjsons** folder of InsightsPreConfiguration.

Here is the template of **Database_systemUserProperties.json**:

```json
{
  "userDetails": {
    "databaseTypeName": "MySQL",
    "hostName": "",
    "dbName": "",
    "dbSchemaName": "",
    "dbUserName": "",
    "dbPassword": "",
    "port": 3306,
    "systemProperties": "Database_systemNativeProperties.json"
  }
}
```

For configuring **Database** system, all the above-mentioned details must be provided in the json file.

- *databaseTypeName* is the name of the database for which system will be created.
  - Its value can be **MySQL**, **MS_SQL_Server**, **ORACLE**, or **PostgreSQL**.
- *hostName* will be the server or machine where a database management system (DBMS) is installed.
- *dbName* will be the name of the database.
- *dbSchemaName* will be the name of the schema.
- *dbUserName* will be the username that can be used to connect with the database.
- *dbPassword* will be the password for the given user.
- *port* will be the port used for database connection.

---

## Configuring SCM system User Properties json for coverageFile

To upload a coverage file at the time of creating the integration, some inputs for coverage file are required in the SCM system user properties json.  
Here is the template of **GitHub_systemUserProperties.json**:

```json
{
  "userDetails": {
    "identifierName": "GitHub",
    "version": 2.20,
    "authType": 1,
    "username": "",
    "accessToken": "https://api.github.com",
    "apiURL": "",
    "ProjectsDisplayName": "",
    "regex": "",
    "systemProperties": "GitHub_systemNativeProperties.json"
  },
  "additionalProperties": [
    {
      "key": "Regex",
      "value": ""
    }
  ],
  "coverageFile": [
    {
      "files": [
        {
          "coverageFile": "jacoco_1085.xml",
          "coverageReportType": "jacoco",
          "fileTag": "merged"
        }
      ],
      "startTag": "2022Q3PH19_7_115_00_B000",
      "endTag": "726f826c14eafea8cf497af73d1beddf630e3f71",
      "language": "java",
      "branchName": "master",
      "repoName": "OIM-OAM"
    }
  ]
}
```

Similarly, **coverageFile** section is present in **GitHub_systemUserProperties.json** as well.

All the coverage files that are needed to be uploaded should be saved in **coveragefiles** folder of InsightsPreConfiguration.

For configuring **coverageFile** for any SCM system, all the below-mentioned details must be provided in the json file.

- In *files*, details for all the coverage files and their types need to be provided.  
  Multiple files can also be uploaded by adding more objects in *files* as shown below:

```json
"coverageFile": [
  {
    "files": [
      {
        "coverageFile": "jacoco_1085.xml",
        "coverageReportType": "jacoco",
        "fileTag": "merged"
      },
      {
        "coverageFile": "jacoco_1085.xml",
        "coverageReportType": "jacoco",
        "fileTag": "merged"
      }
    ],
    "startTag": "2022Q3PH19_7_115_00_B000",
    "endTag": "726f826c14eafea8cf497af73d1beddf630e3f71",
    "language": "java",
    "branchName": "master",
    "repoName": "OIM-OAM"
  }
]
```

- *coverageFile* will be the name of the coverage file to be uploaded.
- *coverageReportType* will be the format of coverage file to be uploaded, i.e., **jacoco** or **cobertura**.
- *fileTag* will be the file type of the coverage file to be uploaded, i.e., **unit**, **integrated**, etc.
  - This will merge all the mentioned coverage files.  
    If you want to upload a single file, make sure the file type is **merged**.
- *startTag* will be the commit tag/commit SHA, from which commit onwards changed code coverage needs to be calculated.
- *endTag* will be the commit tag/commit SHA, up to which changed code coverage needs to be calculated.  
  If nothing is specified, then it will take the latest commit SHA.
- *language* will be the programming language for which the coverage file is to be uploaded, i.e., **java**, **angular**, **python**, or **dotnet**.
- *branchName* will be the name of the branch of your repository.
- *repoName* will be the name of the repository of the SCM system.

> ![Note](../assets/Note.jpg) If coverage file is not required to be uploaded while creating the integration for Database, then provide *coverageFile* as empty `""`.

---
