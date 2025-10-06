# Description

- Let us say the <code class="expression">space.vars.SITENAME</code> is installed on 10.13.27.211 instance on HTTP and user credentials for this instance is “admin” and “password”.
- A user wants to retrieve the basic details [like] of the most recently updated top 50 active integrations configured in the folder with the folder id 3 and its parent folders.
- The basic details of integration include the id of the integration, integration name, projects and entities configured in the integration and status of the integration.

# API Details

- If we want to retrieve these details with the API client, then:

  **Request Method Type:** GET  
  **Request URL:**  
  `http://10.13.27.211:8989/OpsHubWS/queryNode/execute?query=query%7BintegrationList(fetchAllAccessibleObjects%3Atrue%2Cpagination%3A%7BstartAt%3A0%2CpageSize%3A2%7D%2CfilterList%3A%5B%7Bkey%3A%22status%22%2C%20value%3A%22ACTIVE%22%2Coperator%3A%22EQUAL%22%7D%2C%7Bkey%3A%22folderId%22%2C%20value%3A%221%22%2Coperator%3A%22EQUAL%22%7D%5D%2C%20%20%20%20%20%20%20%20sortBy%3A%7BorderType%3A%22DESCENDING%22%2CsortBy%3A%22lastUpdatedTime%22%7D)%7Blist%7Bid%2Cname%2Csystem1%2Csystem2%2CprojectConfiguration%7BprojectPairs%7BprojectForSystem1%7BinternalName%2CdisplayName%7D%2Cdirection%2CprojectForSystem2%7BinternalName%2CdisplayName%7D%7D%7D%2CentityPairs%7Bid%2CentityTypeForSystem1%7BinternalName%2CdisplayName%7D%2Cdirection%2CentityTypeForSystem2%7BinternalName%2CdisplayName%7D%2CmappingId%2Csettings%7Bforward%7Bstatus%7D%2Cbackward%7Bstatus%7D%7D%7D%2CfolderId%2CcreatedTime%2ClastUpdatedTime%7D%2Cpagination%7BpageSize%2CstartAt%2CtotalNumberOfRecords%7D%7D%7D`

  **Authentication Data:**  
  Type: Basic Authentication  
  User Name: admin  
  Password: password

  **Headers:**  
  - api_version: 1  
  - Content-Type: application/json

- If we want to retrieve these details with the curl command, then:

```bash
curl -X GET --header "api_version: 1" --header "Content-Type: application/json" -u admin:password "http://10.13.27.211:8989/OpsHubWS/queryNode/execute?query=query%7BintegrationList(fetchAllAccessibleObjects%3Atrue%2Cpagination%3A%7BstartAt%3A0%2CpageSize%3A2%7D%2CfilterList%3A%5B%7Bkey%3A%22status%22%2C%20value%3A%22ACTIVE%22%2Coperator%3A%22EQUAL%22%7D%2C%7Bkey%3A%22folderId%22%2C%20value%3A%221%22%2Coperator%3A%22EQUAL%22%7D%5D%2C%20%20%20%20%20%20%20%20sortBy%3A%7BorderType%3A%22DESCENDING%22%2CsortBy%3A%22lastUpdatedTime%22%7D)%7Blist%7Bid%2Cname%2Csystem1%2Csystem2%2CprojectConfiguration%7BprojectPairs%7BprojectForSystem1%7BinternalName%2CdisplayName%7D%2Cdirection%2CprojectForSystem2%7BinternalName%2CdisplayName%7D%7D%7D%2CentityPairs%7Bid%2CentityTypeForSystem1%7BinternalName%2CdisplayName%7D%2Cdirection%2CentityTypeForSystem2%7BinternalName%2CdisplayName%7D%2CmappingId%2Csettings%7Bforward%7Bstatus%7D%2Cbackward%7Bstatus%7D%7D%7D%2CfolderId%2CcreatedTime%2ClastUpdatedTime%7D%2Cpagination%7BpageSize%2CstartAt%2CtotalNumberOfRecords%7D%7D%7D"

