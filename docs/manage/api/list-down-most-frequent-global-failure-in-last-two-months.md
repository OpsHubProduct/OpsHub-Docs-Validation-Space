# Description

- Let’s say the {{SITENAME}} is installed on 10.13.27.211 instance on HTTP and user credentials for this instance is “admin” and “password”
- A user wants to retrieve the basic details of the most frequent 20 global failures of last two months from all integrations.
- The basic details of global failure including the id of the failure, failure message, failure code and failure count, corresponding integration group id.

# API Details

- If we want to retrieve these details with the API client, then:

  **Request Method Type: GET**  
  **Request URL:**  
  `http://10.13.27.211:8989/OpsHubWS/queryNode/execute?query=query%7BglobalFailureList(pagination%3A%7BpageSize%3A20%2CstartAt%3A0%7D%2CfilterList%3A%5B%7Bkey%3A%22executionType%22%2Cvalue%3A%22LAST_MONTHS%22%2Coperator%3A%22EQUAL%22%7D%2C%7Bkey%3A%22executionValue%22%2Cvalue%3A%222%22%2Coperator%3A%22EQUAL%22%7D%5D%2CsortBy%3A%7BorderType%3A%22DESCENDING%22%2CsortBy%3A%22failureCount%22%7D)%7Blist%7Bid%2CfailureMessage%2CfailureCode%2CfailureCount%2CintegrationId%7D%7D%7D`  

  **Authentication Data:**  
  Type: Basic Authentication  
  User Name: admin  
  Password: password  

  **Headers:**  
  `api_version:1`, `Content-Type: application/json`

- If we want to retrieve these details with the curl command, then:

  ```bash
  curl -X GET --header "Accept: application/json" --header "api_version: 1" --header "Content-Type: application/json" -u admin:password "http://10.13.27.211:8989/OpsHubWS/queryNode/execute?query=query%7BglobalFailureList(pagination%3A%7BpageSize%3A20%2CstartAt%3A0%7D%2CfilterList%3A%5B%7Bkey%3A%22executionType%22%2Cvalue%3A%22LAST_MONTHS%22%2Coperator%3A%22EQUAL%22%7D%2C%7Bkey%3A%22executionValue%22%2Cvalue%3A%222%22%2Coperator%3A%22EQUAL%22%7D%5D%2CsortBy%3A%7BorderType%3A%22DESCENDING%22%2CsortBy%3A%22failureCount%22%7D)%7Blist%7Bid%2CfailureMessage%2CfailureCode%2CfailureCount%2CintegrationId%7D%7D%7D"
  ```

**Decoded Query Structure** in the above case will be:

```graphql
query {
  [globalFailureList](objects_and_enums#globalfailurelist)(
    [pagination](objects_and_enums#pagination): { pageSize: 20, startAt: 0 },
    [filterList](objects_and_enums#filter): [
      { key: "executionType", value: "LAST_MONTHS", operator: "EQUAL" },
      { key: "executionValue", value: "2", operator: "EQUAL" }
    ],
    [sortBy](objects_and_enums#sortorder): { orderType: "DESCENDING", sortBy: "failureCount" }
  ) {
    list {
      id
      failureMessage
      failureCode
      failureCount
      integrationId
    }
  }
}
```

The above script will fetch the details (Id of the failure, failure message, failure code, failure count, integration id) of all integrations.

