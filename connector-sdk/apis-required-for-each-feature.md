### List of APIs required for implementing the features

>**Note**: The mandatory APIs are required to integrate any system through SDK.

| Feature | APIs to be Implemented |
|---------|----------------------|
| Basic Entity Sync | **Entity APIs:**<br>* Get<br>* Create<br>* Update<br>* List |
| Soft-Delete | **Entity APIs:**<br>* Soft-Delete |
| Comment | **Comment APIs:**<br>* Add<br>* Get<br><br>**Entity Type Get API:**<br>* Provide metadata for comments |
| Attachment | **Attachment APIs:**<br>* Get<br>* Create<br>* Update<br>* Delete<br><br>Entity Get and List APIs should also provide attachments<br><br>**Entity Type Get API:**<br>* Provide metadata for attachments |
| Link | **Link APIs:**<br>* Create or Update<br>* Delete<br><br>Entity Get and List APIs should also provide links<br><br>**Entity Type Get API:**<br>* Provide metadata for links |
| History | **History APIs:**<br>* List<br>* Attachment<br>* Comment<br>* Link<br><br>**Entity Type Get API:**<br>* Provide metadata for history |
| User Mention | **User APIs:**<br>* List<br><br>**Entity Type Get API:**<br>* Provide metadata for userMention |
| Inline Files / Images | **Attachment APIs:**<br>* Get<br>* Create<br>* Update<br>* Delete<br>* File Name - Get<br><br>**Entity Type Get API:**<br>* Provide metadata for inlineFiles |
| Remote Entity Link | **Entity Type Get API:**<br>* Provide metadata for entityWebUrl |
| Comment with Attachment | All the Comment and Attachment APIs |
| Link with Comment | All the link APIs<br><br>**Entity Type Get API:**<br>* Provide link comment field name in link field name info. |
| Criteria | **Entity Type Get API:**<br>* Provide details in searchEntityInfo |
| Target lookup | **Entity Type Get API:**<br>* Provide details in searchEntityInfo |
| Recovery | **Entity Type Get API:**<br>* Provide metadata for Recovery |
| Workflow Transition | User need to configure workflow XML from mapping screen.<br><br>Depending on the workflow XML, OpsHub will calculate the path from one state to another and call the update API accordingly. |
| Comment Author Impersonation | Comments feature should be supported.<br><br>**Entity Type Get API:**<br>* Provide metadata for createdUpdatedByFieldDataType |
| Reference Field Synchronization | Reference entity type metadata should be provided.<br><br>**Entity Type Get API:**<br>* In fields, provide input for referenceFieldMetadata<br>* In fieldNameInfo, provide input for entityNameFieldName |
| Entity Type and Project Movement | **Entity Types List API:**<br>* Provide metadata for belongsToCategories and projectMovementSupported.<br><br>**Entity Type Get API:**<br>* Provide the fields updateStepNumber for entityTypeFieldName and projectIdFieldName as "-3" and "-2" respectively if the end system has different API for the update of the entityType and project. Provide updateStepNumber as "-6" for both the fields if the end system has same API for update of entityType and project.<br><br>By default, if no updateStepNumber for entityTypeFieldName and projectIdFieldName is given, it will be treated as having different API for entityType and project change.<br><br>**Entity Get API:**<br>* If entityTypeId or projectId is passed as "null", the API should return field values for the given entityId by searching it across the given scope without having the filtering on entityTypeId, projectId or both, depending on which one is "null".<br><br>**Entity-Update API:**<br>* Handle the update for entityType and project in case the updateSubStepNumber received is either of "-2","-3" or "-6", depending on the fields metadata given in the Entity-Get fields metadata for entityTypeIdFieldName and projectIdFieldName. |
| Get Entity Revisions using Utility | **History – List API:**<br>* Get history filtered for a specific entity.<br><br>**Getting history description instead of old and new values:**<br>* If an end system returns complex history data and parsing the old and new field values is not feasible, the full history description can be returned instead. For more details, refer to the [History – List API](history-list.md#response-body). |
