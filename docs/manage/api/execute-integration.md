# Description

* Let's say the OpsHub Integration Manager is installed on 10.13.27.211 instance on HTTP and user credentials for this instance is “admin” and “password”.
* A user has configured the integration on the OpsHub Integration Manager, which is having id 2 and this integration is in the Active mode.
* User wants to execute this integration.

# API Details

* If we want to retrieve these details with the API client, then:

**Request Method Type:** PUT  
**Request URL:** `http://10.13.27.211:8989/OpsHubWS/queryNode/execute`  
**Request Body:**

```json
{
  "query":"mutation{integration(id:1,name:\"Jira_HP_Integration\",system1:2,system2:3,projectConfiguration:{projectPairs:[{projectForSystem1:{internalName:\"10104\"},direction:\"BIDIRECTIONAL\",projectForSystem2:{internalName:\"DEFAULT:: System2_Project1\"}}, {projectForSystem1:{internalName:\"10105\"},direction:\"BIDIRECTIONAL\",projectForSystem2:{internalName:\"DEFAULT:: System2_Project2\"}}]},entityPairs:[{entityTypeForSystem1:{internalName:\"10004\"},direction:\"BIDIRECTIONAL\",entityTypeForSystem2:{internalName:\"defects\"},mappingId:5,settings:{forward:{status:\"EXECUTE\",startPollingTime:\"Mon Dec 30 2019 09:18:26\",advanced:{criteria: {query:\"id>0\",storageType:\"DATABASE\"},maximumRetryCount:8,scheduleId:0,synchronizationType:\"BOTH\",workflow:{integration:{id:1,eventTypesToSynchronize:[\"CREATE\",\"UPDATE\",\"DELETE\"]}}}},backward:{status:\"EXECUTE\",startPollingTime:\"Mon Dec 30 2019 09:18:26\",advanced:{maximumRetryCount:8,scheduleId:0,synchronizationType:\"BOTH\",workflow:{integration:{id:1,eventTypesToSynchronize:[\"CREATE\",\"UPDATE\"]}}}}}}],folderId:0,objectVersion:0){id,name,folderId,createdTime,lastUpdatedTime}}"
}
```

**Authentication Data:**  
Type: Basic Authentication  
User Name: `admin`  
Password: `password`  

**Headers:**  
`api_version: 1`, `Content-Type: application/json`

* If we want to retrieve these details with the curl command, then:

```bash
curl -i -X PUT "http://10.13.27.211:8989/OpsHubWS/queryNode/execute" \
--header "Content-Type: application/json" \
--header "api_version: 1" \
-u admin:password \
-d "{\"query\":\"mutation{integration(id:1,name:\\\"Jira_HP_Integration\\\",system1:2,system2:3,projectConfiguration:{projectPairs:[{projectForSystem1:{internalName:\\\"10104\\\"},direction:\\\"BIDIRECTIONAL\\\",projectForSystem2:{internalName:\\\"DEFAULT:: System2_Project1\\\"}}, {projectForSystem1:{internalName:\\\"10105\\\"},direction:\\\"BIDIRECTIONAL\\\",projectForSystem2:{internalName:\\\"DEFAULT:: System2_Project2\\\"}}]},entityPairs:[{entityTypeForSystem1:{internalName:\\\"10004\\\"},direction:\\\"BIDIRECTIONAL\\\",entityTypeForSystem2:{internalName:\\\"defects\\\"},mappingId:5,settings:{forward:{status:\\\"EXECUTE\\\",startPollingTime:\\\"Mon Dec 30 2019 09:18:26\\\",advanced:{criteria: {query:\\\"id>0\\\",storageType:\\\"DATABASE\\\"},maximumRetryCount:8,scheduleId:0,synchronizationType:\\\"BOTH\\\",workflow:{integration:{id:1,eventTypesToSynchronize:[\\\"CREATE\\\",\\\"UPDATE\\\",\\\"DELETE\\\"]}}}},backward:{status:\\\"EXECUTE\\\",startPollingTime:\\\"Mon Dec 30 2019 09:18:26\\\",advanced:{maximumRetryCount:8,scheduleId:0,synchronizationType:\\\"BOTH\\\",workflow:{integration:{id:1,eventTypesToSynchronize:[\\\"CREATE\\\",\\\"UPDATE\\\"]}}}}}}],folderId:0,objectVersion:0){id,name,folderId,createdTime,lastUpdatedTime}}\"}"
```

# Decoded Query Structure

```graphql
mutation {
  integration(
    id: 1,
    name: "Jira_HP_Integration",
    system1: 2,
    system2: 3,
    projectConfiguration: {
      projectPairs: [
        {
          projectForSystem1: { internalName: "10104" },
          direction: "BIDIRECTIONAL",
          projectForSystem2: { internalName: "DEFAULT:: System2_Project1" }
        },
        {
          projectForSystem1: { internalName: "10105" },
          direction: "BIDIRECTIONAL",
          projectForSystem2: { internalName: "DEFAULT:: System2_Project2" }
        }
      ]
    },
    entityPairs: [
      {
        entityTypeForSystem1: { internalName: "10004" },
        direction: "BIDIRECTIONAL",
        entityTypeForSystem2: { internalName: "defects" },
        mappingId: 5,
        settings: {
          forward: {
            status: "EXECUTE",
            startPollingTime: "Mon Dec 30 2019 09:18:26",
            advanced: {
              criteria: {
                query: "id>0",
                storageType: "DATABASE"
              },
              maximumRetryCount: 8,
              scheduleId: 0,
              synchronizationType: "BOTH",
              workflow: {
                integration: {
                  id: 1,
                  eventTypesToSynchronize: ["CREATE", "UPDATE", "DELETE"]
                }
              }
            }
          },
          backward: {
            status: "EXECUTE",
            startPollingTime: "Mon Dec 30 2019 09:18:26",
            advanced: {
              maximumRetryCount: 8,
              scheduleId: 0,
              synchronizationType: "BOTH",
              workflow: {
                integration: {
                  id: 1,
                  eventTypesToSynchronize: ["CREATE", "UPDATE"]
                }
              }
            }
          }
        }
      }
    ],
    folderId: 0,
    objectVersion: 0
  ) {
    id,
    name,
    folderId,
    createdTime,
    lastUpdatedTime
  }
}
```

To form the above request for executing the integration, we need the details for the integration.  
To retrieve the details of the integration, query given in **Retrieve the global failure with the ID:1** in [example 1](forming-calls-with-api.md#examples) can be used in which ID is 1 and the object to be retrieved is [Integration](objects-and-enums#integration).
