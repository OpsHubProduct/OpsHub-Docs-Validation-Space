
# Updating UserInput.json ==
Unzip the InsightsPreConfiguration.zip provided along with the Docker image.

For creating any SCM and ALM systems' integrations, that system name has to be added in the '''UserInput.json''' file in '''userjsons''' folder of InsightsPreConfiguration.

* A sample of '''UserInput.json''' is given below:

```json
{
 "listOfAnalyses":
 [
   {
     "scmSystem" : "Git_systemUserProperties.json",
     "entitySystem" : "ADO_systemUserProperties.json",
     "endSystemsAnalyses" :
     {
       "CommitAnalysis" : "CommitAnalysis.json",
       "EntityAnalysis" : "EntityAnalysis.json",
       "EntityHistoryAnalysis" : "EntityHistoryAnalysis.json"
     },
     "activateExtractions" : 1
   }
 ]
}
```
## Configuring System Integrations in UserInput.json

Instead of **Git**, if the SCM system is **GitHub**, in the above-given sample, change the file name of **Git_systemUserProperties.json** to **GitHub_systemUserProperties.json**, and for the ALM system, instead of **ADO**, if it is **Jira**, change the file name of **ADO_systemUserProperties.json** to **Jira_systemUserProperties.json** (any other name can be given if a new file with its template is created).

For creating another SCM/ALM system with different configurations, create a copy of that systemUserProperties.json file and rename the file. This filename should be added in **UserInput.json** for creating integration.

- For example, if another Jira system needs to be created for **self-hosted/On-Premise** Jira instance, create a copy of **Jira_systemUserProperties.json** and rename it as **JiraOnPrem_systemUserProperties.json**. Add it in *entitySystem* in **UserInput.json** file.

For any ALM/SCM system, update the file name in the **UserInput.json**. For creating additional integrations for any ALM/SCM system, add one more pair of analysis in the list as shown below:

```json
{
  "listOfAnalyses": [
    {
      "scmSystem": "Git_systemUserProperties.json",
      "entitySystem": "ADO_systemUserProperties.json",
      "endSystemsAnalyses": {
        "CommitAnalysis": "CommitAnalysis.json",
        "EntityAnalysis": "EntityAnalysis.json",
        "EntityHistoryAnalysis": "EntityHistoryAnalysis.json"
      },
      "activateExtractions": 1
    },
    {
      "scmSystem": "GitHub_systemUserProperties.json",
      "entitySystem": "ADO2_systemUserProperties.json",
      "endSystemsAnalyses": {
        "CommitAnalysis": "CommitAnalysis.json",
        "EntityAnalysis": "EntityAnalysis.json",
        "EntityHistoryAnalysis": "EntityHistoryAnalysis.json"
      },
      "activateExtractions": 1
    }
  ]
}
```

Instead of creating SCM and ALM systems' integrations, an additional integration for either system can also be created by adding the below sample snippets in *listOfAnalyses* in **UserInput.json**.

- For **SCM** system:
```json
{
  "scmSystem": "GitHub_systemUserProperties.json",
  "endSystemsAnalyses": {
    "CommitAnalysis": "CommitAnalysis.json"
  },
  "activateExtractions": 1
}
```

- For **ALM** system:
```json
{
  "entitySystem": "Jira_systemUserProperties.json",
  "endSystemsAnalyses": {
    "EntityAnalysis": "EntityAnalysis.json",
    "EntityHistoryAnalysis": "EntityHistoryAnalysis.json"
  },
  "activateExtractions": 1
}
```

Set the value of *"activateExtractions"* to 1 to activate the integrations; or else set it to 0. Integrations can also be activated using OIM's UI later on.

## Configuring System User Properties jsons

For all the systemUserProperties mentioned in the **UserInput.json**, system configuration details like username, accessToken, applicationURL, Project, etc. are required.

### For Git System

Here is the template of **Git_systemUserProperties.json**:
```json
{
  "userDetails": {
    "identifierName": "Git",
    "authType": 1,
    "username": "",
    "password": "",
    "gitRepositoryPath": "/home/repo",
    "regex": "",
    "systemProperties": "Git_systemNativeProperties.json"
  },
  "additionalProperties": [
    {
      "key": "Start Processing Event Id",
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

For configuring **Git** system, all the above-mentioned details must be provided in the json file.

- *identifierName* is the unique system name given to the newly created system.
- *authType* can be **1** for **Basic Authentication** and **2** for **RSA Authentication**.

  - If your *authType* is **Basic Authentication**, add username and password/Personal Access Token of an authorized dedicated user.
  - If your *authType* is **RSA Authentication**, instead of username and password, it will be passPhrase and rsaKeyPath as shown below:

```json
{
  "userDetails": {
    "identifierName": "Git",
    "authType": 2,
    "passPhrase": "",
    "rsaKeyPath": "",
    "gitRepositoryPath": "/home/repo",
    "regex": "",
    "systemProperties": "Git_systemNativeProperties.json"
  },
  "additionalProperties": [
    {
      "key": "Start Processing Event Id",
      "value": ""
    }
  ],
  "coverageFile": [
    {
      "files": [
        {
          "coverageFile": "",
          "coverageReportType": "",
          "fileTag": ""
        }
      ],
      "startTag": "",
      "endTag": "",
      "language": "",
      "branchName": "",
      "repoName": ""
    }
  ]
}
```

- *gitRepositoryPath* will be the path which you will be providing for mounting the Git repo in the docker container.
- In *regex*, it will be the regular expression with which you can extract the related workitem Id from commit message. Based on the regex, it will associate entity Id for each commit which will be used to relate commits to workitems.

  - If ALM system is **Azure DevOps**, the regex will be `([0-9]{4,6})`
  - If ALM system is **Jira**, the regex will be `((?<!([A-Z0-9]{1,10})-?)[A-Z0-9]+-\d+).`

> ![Note](../assets/Note.jpg) `.` is part of regex for Jira.

- *Start Processing Event Id* will be the commit Id from which data needs to be polled.

> ![Note](../assets/Note.jpg) **coverageFile** section is not required to be filled. Its values can be empty or can be kept as already provided.

### For Jira System

Here is the template of **Jira_systemUserProperties.json**:
```json
{
  "userDetails": {
    "identifierName": "Jira",
    "version": "8.3.4",
    "deploymentType": 2,
    "authType": 1,
    "username": "",
    "password": "",
    "apiURL": "",
    "ProjectsDisplayName": "",
    "sprintBoards": "",
    "systemProperties": "Jira_systemNativeProperties.json"
  }
}
```

For configuring **Jira** system, all the above-mentioned details must be provided in the json file.

- *identifierName* is the unique system name given to the newly created system.
- *version* will be the supported version of your Jira instance.
- *deploymentType* can be **1** for **self-hosted/On-Premise** or **2** for **Cloud instance**.
  - If *deploymentType* is **Cloud**, *authType* will be **1**.
  - If *deploymentType* is **self-hosted/On-Premise**, *authType* can be **1** for **Basic Authentication**, **2** for **Cookie-based Authentication** and **3** for **API Token**.
- In *username* and *password*, provide username and password/Personal Access Token of an authorized user for polling workitems.
- *apiURL* will be the Jira instance URL.
- *ProjectsDisplayName* will be the Project(s) for which you want to poll workitems.
  - For polling data from more than one project, provide project’s display names in comma separated format, i.e., `"Project1, DummyProject2"`.
- *sprintBoards* are the boards from which sprints will be polled.
  - For polling data from more than one board, provide board names in comma separated format, i.e., `"Board2, DummyBoard"`.
  - For polling data from all the boards, set *sprintBoards* as `" - All Boards -"`.

> ![Note](../assets/Note.jpg) There is a space before *hyphen (-)* which is required.

---

### For AzureDevOps/ADO/TFS System

Here is the template of **ADO_systemUserProperties.json**:
```json
{
  "userDetails": {
    "identifierName": "Azure DevOps",
    "version": 2015,
    "tfsDeploymentType": 2,
    "authType": 2,
    "applicationURL": "",
    "username": "",
    "accessToken": "",
    "apiURL": "",
    "tfsCollectionName": null,
    "ProjectsDisplayName": "",
    "systemProperties": "ADO_systemNativeProperties.json"
  }
}
```

For configuring **AzureDevOps/ADO/TFS** system, all the above-mentioned details must be provided in the json file.

- *identifierName* is the unique system name given to the newly created system.
- *version* will be the version of your AzureDevOps/ADO/TFS instance.
- *tfsDeploymentType* can be **1** for **self-hosted/On-Premise** or **2** for **Cloud instance**.
  - If *tfsDeploymentType* is **self-hosted/On-Premise**, *tfsCollectionName* needs to be provided instead of null for accessing the collection for polling workitems.
  - If *tfsDeploymentType* is **cloud**, *tfsCollectionName* will be **null**.
- *authType* can be **1** for **Basic Authentication** and **2** for **Personal Access Token**.
  - If your *authType* is **Personal Access Token**, provide *username* and *accessToken* of an authorized user.
  - If your *authType* is **Basic Authentication**, instead of *accessToken*, it will be *password* as shown below.
  - In *username* and *password*, provide username and password/Personal Access Token of an authorized user for polling workitems.

```json
{
  "userDetails": {
    "identifierName": "Azure DevOps",
    "version": 2015,
    "tfsDeploymentType": 2,
    "authType": 2,
    "applicationURL": "",
    "username": "",
    "password": "",
    "apiURL": "",
    "tfsCollectionName": null,
    "ProjectsDisplayName": "",
    "systemProperties": "ADO_systemNativeProperties.json"
  }
}
```

- *applicationURL* will be the Server URL of your AzureDevOps/ADO/TFS instance.
- *apiURL* will be the URL of the TFSService.  
  For example: `http://<hostname>:9090/TFSService`.  
  Here, the `<hostname>` signifies the hostname of the VM where the TFS service has been registered.

  - **OpsHubTFSService** should be registered on any Windows machine before starting the Docker’s installation.  
    `OpsHubTFSService.zip` can be found in the `OpsHub_Resource.zip` along with the docker image.
  - Refer to [How to register OpsHubTFSService?](../register/opsHubTFSService) page for steps to register OpsHubTFSService.

- *ProjectsDisplayName* will be the Project(s) for which you want to poll workitems.
  - For polling the data from more than one project, provide project’s display names in comma separated format, i.e., `"Project1, DummyProject2"`.




