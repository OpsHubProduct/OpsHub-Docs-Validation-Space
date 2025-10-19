# Connector SDK APIs
The following table describes:  
- The list of SDK APIs and the mandatory APIs.  
- The "Order of Implementation" column to check the order of the APIs to be implemented. Empty columns represent optional APIs.  
- Overview of how OpsHub will call each API and its expected response.

| Sections | API Name | Required (Yes/No) | Order of Implementation | Overview |
|----------|---------|-----------------|------------------------|---------|
| **Introduction** | | | | This section will help you understand key concepts of SDK API and help you get started with it. |
| | [SDK API URI Structure](sdk-api-uri-structure.md) | | | |
| | [Error Handling](error-handling.md) | | | |
| | [Pagination](pagination.md) | | | |
| | [Passing the Configuration Parameters to SDK APIs](passing-the-configuration-parameters-to-sdk-apis.md) | | | |
| **Session APIs** | | Yes | 1 | API to manage sessions with the end system. |
| | [Session – Initialize](session-initialize.md) | | | API to initiate SDK. In this API, SDK can connect to the end system, initialize memory cache, etc. |
| | [Session - Logout](session-logout.md) | | | API to cleanup / logout |
| **Registration API** | | Yes | 2 | |
| | [Connector Metadata – Get](connector-metadata-get.md) | | | API to get connector metadata. |
| | [Discovery API - Get](discovery-api-get.md) | | | API to get connector discovery details. |
| **Configuration Information APIs** | | Yes | 3 | These APIs are one of the most crucial APIs for the whole SDK to function as expected. OpsHub heavily relies on data sent as part of configuration info APIs to support multiple sync features. |
| | [Server-Info](server-info.md) | | | This API needs to return basic server related information like max page size, time zone, etc. |
| | [Projects – List](projects-list.md) | | | This API needs to return all the projects that exist in the end system. |
| | [Entity Types – List](entity-types-list.md) | | | Returns all the entity types for a given project. |
| | [Entity Type – Get](entity-type-get.md) | | | Returns detailed configuration information for a given entity type and project. |
| | [Lookup Field Values-Get](lookup-field-value-get.md) | | | Returns lookup values for a given field, a given entity type. |
| **Entity APIs** | | Yes | 4 | Entity CRUD APIs. |
| | [Entity – Get](entity-get.md) | | | Gets information for a given entity id. |
| | [Entity – Create](entity-create.md) | | | Creates a single entity in the end system. |
| | [Entity – Update](entity-update.md) | | | Updates a single entity in the end system. |
| | [Entity – List](entity-list.md) | | | Searches API on entities. |
| | [Entity – Delete](entity-delete.md) | | | Soft-deletes a single entity in the end system. |
| **Substeps** | | No | | Returns steps in which a given update needs to be broken. |
| | [Dynamic Substeps – Get](dynamic-substeps-get.md) | | | |
| **User APIs** | | No | | Search API on users. |
| | [Users – List](users-list.md) | | | Returns list of users matching a given search criteria. |
| **Comments API** | | No | | Implement these set of APIs to integrate comments. |
| | [Add Comments](add-comments.md) | | | Adds a single comment in the end system. |
| | [Get Comments](get-comments.md) | | | Gets all comments for a given entity. |
| **Attachment APIs** | | No | | Implement these set of APIs to integrate attachments. |
| | [Attachment Content – Get](attachment-content-get.md) | | | Returns attachment content in base64 format. |
| | [Attachment – Create](attachment-create.md) | | | Adds a single attachment in the end system. |
| | [Attachment - Update](attachment-update.md) | | | Updates an attachment in the end system. |
| | [Attachment – Delete](attachment-delete.md) | | | Deletes an attachment in the end system. |
| | [File Name – Get](file-name-get.md) | | | Parses and returns file name in given HREF or imgsrc. |
| **Links** | | No | | Implement these set of APIs to integrate links. |
| | [Link – Create or Update](link-create-or-update.md) | | | Adds or updates a link. |
| | [Link – Delete](link-delete.md) | | | Deletes a link. |
| | [Get Siblings Under Parent Order By Rank](get-siblings-under-parent-order-by-rank.md) | | | Gets siblings under parent ordered by rank. |
| **History APIs** | | No | | Implement these set of APIs to integrate history. |
| | [History – List](history-list.md) | | | This API is mandatory to implement if recovery.type is 'HISTORY_BASED' in entitytype - get API of configuration info category. The API should return matching history records as per the given search criteria. |
| | [Attachment History – List](attachment-history-list.md) | | | Implement this API if your end system has a separate API for getting attachment history. |
| | [Comment History – List](comment-history-list.md) | | | Implement this API if your end system has a separate API for getting comments history. |
| | [Link History – List](link-history-list.md) | | | Implement this API if your end system has a separate API for getting links history. |

## Some Useful SDK Pages
- [APIs Required for Each Feature](apis-required-for-each-feature.md)
- [SDK Best Practices](sdk-best-practices.md)


