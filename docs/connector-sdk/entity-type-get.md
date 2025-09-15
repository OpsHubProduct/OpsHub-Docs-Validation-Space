## Overview
This API describes the entity type in detail for OpsHub to be able to integrate various basic and complex data for a given entity type.  
>**Note**: It is important to return a correct response for this API as OpsHub relies heavily on these inputs to handle multiple connector tasks automatically.

## API URI
This is the URI OpsHub will execute to call this API:

```bash
GET: /entity-types/{entityTypeId}?projectId=<projectId>
```

## URI Parameters

| Name | In | Required | Type | Description |
|------|----|----------|------|-------------|
| entityTypeId | path | True | String | ‘id’ of entity type returned as response of Entity Type – List API |
| projectId | query | True | String | Project id for which entity type details need to be returned. ProjectId here will be the same as ‘id’ sent as part of `/projects` |

## Response Payload
```json

{

  "multiStepUpdate": "NO_SUB_STEPS, STATIC_SUB_STEPS, DYNAMIC_SUB_STEPS",

  "recovery": {

    "type": "FIELD_BASED, COMPARISON_BASED, HISTORY_BASED",

    "fieldName": "// If FIELD_BASED, then id of the field to store last update date"

  },

  "history": {

    "type": "FIELD_BASED, FULL_STATE_BASED",

    "revisionDateFormat": "dd/MM/YYYY’T’hh:mm:ss.SSSz",

    "isRevisionIdNumeric": "true/false | datatype: boolean",

    "revisionUserDataType": "USERNAME_AS_USER, EMAIL_AS_USER",

    "separateHistoryApis": "ATTACHMENTS, COMMENTS, LINKS",

    "sortableFields":"CREATED_UPDATED_TIME, ENTITY_ID, REVISION_ID"

  },

  "enitytScope": {

    "additionalScopeFieldName": "field id used as additional scope"

  },

  "entityWebUrl": {

    "baseUrl": "https://example.com/",

    "trailingTemplate": "browse/{0}/{1}",

    "substitutes": {

      "0": "field id of the field whose value need to be first replacement",

      "1": "field name of second replacement field"

    }

  },

  "isFieldIdConstantAcrossProjects": "true/false | datatype: boolean",

  "isInternalValueExistForLookupField": "true/false | datatype: boolean",

  "isUpdateAvailable": "true/false | datatype: boolean",

  "waitTimeInMillisIfApiResponseDelayed": "Max delay in API response in milli seconds. | datatype: number",

  "searchEntityInfo": {

    "sortableFields": "CREATED_UPDATED_TIME, ENTITY_ID, REVISION_ID",

    "isGroupingSupported": "true / false",

    "isSearchPossibleOnAnyField": "true / false",

    "isCriteriaInSystemNativeFormat": "true / false",

    "dateTimeFormat": "dd/MM/YYYY’T’hh:mm:ss.SSSz",

    "queryFieldNameInfo": {

      "entityIdFieldName": "entity id field id",

      "entityTypeIdFieldName": "entity type field id",

      "projectIdFieldName": "project id’s field id",

      "createdDateFieldName": "created date’s field id",

      "updatedDateFieldName": "updated date’s field id",

      "createdByFieldName": "created By’s field id"

    },

    "batchSizeForInQuery": "number of entities that can be passed in 'IN' or 'OR' query"

  },

  "fieldNameInfo": {

    "entityIdFieldName": "field id of unique and uneditable entity primary id field",

    "entityTitleFieldName": "field id for entity title",

    "entityDisplayIdFieldName": "field id of field that has entity display id (id any)",

    "entityTypeIdFieldName": "field id for entity type",

    "projectIdFieldName": "field id of field that contains project info for entity",

    "createdDateFieldName": "field id of Created date field",

    "updatedDateFieldName": "field id of updated date field",

    "createdByFieldName": "field id of created By field",

    "updatedByFieldName": "field id of updated By field",

    "archiveMetadata" : {
	
	"archivedByFieldName": "field id of archived By field",

	"isArchivedFieldName": "field id of is Archived field"

     }
	

  },

  "fields": [

    {

      "id": "unique id or key for each field",

      "name": "Field name",

      "dataType": "TEXT, HTML, WIKI, LOOKUP, DATE, DATE_TIME, DATE_STRING, BOOLEAN, NUMBER, USERNAME_AS_USER, TIME_UNIT, EMAIL_AS_USER, RTF, HYPERLINK, TEST_STEP, PARAMETER, REFERENCE, IMAGE, HIERARCHY",

      "isMandatory": "true/false | datatype: boolean",

      "isMultiSelect": "true/false | datatype: boolean",

      "isReadOnly": "true/false | datatype: boolean",

      "isHistorySupported": "true/false | datatype: boolean",

      "userMentionSupported": "true/false | datatype: boolean",

      "entityMentionSupported": "true/false | datatype: boolean",

      "timeUnit": "MILLISECOND, SECOND, MINUTE, HOUR, DAY",

      "dateFormat": " yyyy-MM-dd or yyyy-MM-dd’T’HH:mm:ss.SSSz",

      "canBeSetAtEntityCreateTime": "true/false | datatype:boolean",

      "updateStepNumber": "// Number starting with 1,2,3",
  
      "referenceFieldMetadata": {
	
		"referencedEntityTypeId: "id of the entity type which is referenced through field"

		"idFieldName": "id field name which stores id or URL of the referenced entity in Entity - GET API and History - List API for base entity"

		"referenceUrl": {

			 "baseUrl": "https://example.com/",

			 "trailingTemplate": "browse/{0}/{1}",

   			 "substitutes": {

     	 			"0": "field id of the field whose value need to be first replacement",

      				"1": "field id of the field whose value need to be second replacement"

    			}

		}

		"titleFieldName": "title field name which stores title or equivalent field of the referenced entity in the Entity - GET API and History - List API for base entity"        

       }

    },

    {

      "id": "unique id or key for each field",

      "name": "Field name",

      "dataType": "TEXT, HTML, WIKI, LOOKUP, DATE, DATE_TIME, DATE_STRING, BOOLEAN, NUMBER, USERNAME_AS_USER, TIME_UNIT, EMAIL_AS_USER, RTF, HYPERLINK, TEST_STEP, PARAMETER, REFERENCE, IMAGE, HIERARCHY",

      "isMandatory": "true/false | datatype: boolean",

      "isMultiSelect": "true/false | datatype: boolean",

      "isReadOnly": "true/false | datatype: boolean",

      "isHistorySupported": "true/false | datatype: boolean",

      "userMentionSupported": "true/false | datatype: boolean",

      "timeUnit": "MILLISECOND, SECOND, MINUTE, HOUR, DAY",

      "dateFormat": "yyyy-MM-dd or yyyy-MM-dd’T’HH:mm:ss.SSSz",

      "canBeSetAtEntityCreateTime": "true/false | datatype:boolean",

      "updateStepNumber": "// Number starting with 1,2,3",
  
      "referenceFieldMetadata": {
	
		"referencedEntityTypeId: "id of the entity type which is referenced through field"

		"idFieldName": "id field name which stores id or URL of the referenced entity in Entity - GET API and History - List API for base entity"

		"referenceUrl": {

			 "baseUrl": "https://example.com/"

			 "trailingTemplate": "browse/{0}/{1}",

   			 "substitutes": {

     	 			"0": "field id of the field whose value need to be first replacement",

      				"1": "field id of the field whose value need to be second replacement"

    			}

		}

		"titleFieldName": "title field name which stores title or equivalent field of the referenced entity in the Entity - GET API and History - List API for base entity"        

       }


    }

  ],

  "comments": {

    "userMentionSupported": "true/false | datatype: boolean",

    "entityMentionSupported": "true/false | datatype: boolean",

    "commentBodyDataType": "TEXT, HTML, WIKI",

    "commentIdDataType": "NUMBER, TEXT",

    "createdUpdatedByFieldDataType": "USERNAME_AS_USER, EMAIL_AS_USER"

    "htmlReplacementForNewLine": "<br/> or \n or null",

    "delayInCommentUpdateTimeInMillis": 2000,

    "createUpdateDateFormat": "yyyy-MM-dd'T'HH:mm:ss.SSSZ",

    "typesOfComments": [

      "Private",

      "Public",

      "etc."

    ],

    "fieldNameInfo": {

      "idFieldName": "Field name of comment id as it is received in API by end system",

      "titleFieldName": " Field name of comment title as it is received in API by end system ",

      "bodyFieldName": " Field name of comment body as it is received in API by end system ",

      "createdDateFieldName": " Field name of comment created date as it is received in API by end system ",

      "updatedDateFieldName": " Field name of comment updated date as it is received in API by end system ",

      "createdByFieldName": " Field name of comment created by as it is received in API by end system ",

      "updatedByFieldName": " Field name of comment updated by as it is received in API by end system ",

      "commentTypeFieldName": " Field name of comment type as it is received in API by end system "

    }

  },

  "attachments": {

    "updateSupported": "true/false | datatype: boolean",

    "deleteSupported": "true/false | datatype: boolean",

    "historySupported": "true/false | datatype: boolean",

    "createUpdateDateFormat": "yyyy-MM-dd'T'HH:mm:ss.SSSZ",

    "typesOfAttachments": [

      "Internal",

      "External",

      "etc."

    ],

    "fieldNameInfo": {

      "idFieldName": " Field name of attachment id as it is received in API by end system ",

      "contentUriFieldName": " Field name of attachment content URI as it is received in API by end system ",

      "renderUriFieldName": " Field name of attachment render URI as it is received in API by end system ",

      "fileNameFieldName": " Field name of attachment file name as it is received in API by end system ",

      "contentTypeFieldName": " Field name of attachment content type as it is received in API by end system ",

      "contentLengthFieldName": " Field name of attachment length as it is received in API by end system ",

      "createdOrUpdatedDateFieldName": " Field name of attachment updated as it is received in API by end system ",

      "createdByFieldName": " Field name of attachment created by as it is received in API by end system ",

      "attachmentTypeFieldName": " Field name of attachment type as it is received in API by end system ",

      "fileCommentFieldName": " Field name of the attachment file comment as it is received in API by end system "

    }

  },

  "inlineFiles": {

    "deleteSupported": "true/false | datatype: boolean",

    "inlineFileStorageType": "ENTITY_LEVEL_STORAGE | EXTERNAL_STORAGE",

    "inlineFileUrlPrefix": ""

  },

  "links": {

    "deleteSupported": "true/false | datatype: boolean",

    "historySupported": "true/false | datatype: boolean",

    "createUpdateDateFormat": "yyyy-MM-dd'T'HH:mm:ss.SSSZ",

    "rank": {

        "rankType": "FLAT_SINGLE | FLAT_MULTIPLE | HIERARCHY_SINGLE | HIERARCHY_MULTIPLE",

        "supportedRankOperations": [

            "MOVE_BEFORE",

            "MOVE_AFTER",

            "LAST_IN_LIST",

            "MOVE_BULK_AFTER"
        ],

        "rankFieldName": "If entity stores the rank info in a field, provide that field name.",

        "rankScope": {

            "template": "{0}::{1}",

            "substitutes": {

                "0": "field name of the field whose value needs to be replacement for 0",

                "1": "field name of the field whose value needs to be replacement for 1"

            }

        }

    },

    "linkTypes": [

      {

        "linkType": "",

        "reverseLinkType": "",

        "isMultiLinkAllowed": "true/false | datatype: boolean",

        "isLinkMandatory": "true/false | datatype: boolean",

        "isBulkLinkingSupported": "true/false | datatype: boolean",

        "isExternalLink": "true/false | datatype: boolean"

      }

    ],

    "fieldNameinfo": {

      "linkTypeFieldName": " Field name of link type (parent, child, related etc.) as it is received in API by end system ",

      "linkedEntityIdFieldName": " Field name of linked entity id as it is received in API by end system ",

      "linkedEntityTypeFieldName": " Field name of linked entity type as it is received in API by end system ",

      "linkedEntityScopeIdFieldName": "linkedEntityScopeId | TODO: Revisit this",

      "createdDateFieldName": " Field name of link created date as it is received in API by end system ",

      "createdByFieldName": " Field name of link created by user as it is received in API by end system ",

      "linkCommentFieldName": " Field name of link comment as it is received in API by end system ",

      "externalLinkUrlFieldName": " Field name of link external URL as it is received in API by end system ",

      "isExternalLinkFieldName": " Field name of field which says if it’s an external link or not, as it is received in API by end system "

    }

  },

"userMention": {

    "userMentionDataType": "USERNAME_AS_USER / EMAIL_AS_USER",

    "mentionDetails": [

      {

        "fieldDataType": "HTML",

        "selectorOrRegex": ["Example: a[href]"],

        "mentionTemplate": "Example: <a href=\"https://example.com/users/${username}\" rel=\"${username}\"> ${displayName} </a>",

        "userDataRegex": "",

        "userDataAttributeName": "Example: href / rel / data-mention"

      },

      {

        "fieldDataType": "WIKI",

        "selectorOrRegex": "Example: [~ohusermention:(.*?)]",

        "mentionTemplate": "Example: [~accountId:${username}]"

      },

      {

        "fieldDataType": "TEXT",

        "selectorOrRegex": "Example: @OH_USER@ohusermention:(.*?)@OH_USER@",

        "mentionTemplate": "Example: ${username} <${email}>"

      }

    ]

  },

  "entityMention": {

      "mentionDetails": [

        {

          "fieldDataType": "HTML",

          "selectorOrRegex": ["Example: a[href]"],

          "mentionTemplate": "Example: <a href=\"https://example.com/users/${username}\" rel=\"${username}\"> ${displayName} </a>",

          "entityIdAttribute": {

            "dataAttributeName": "href",

            "dataRegEx": "/browse/([A-Z_a-z0-9-]+)"
          },

          "entityTypeAttribute": {

            "dataAttributeName": "href",

            "dataRegEx": ".*\\?detail=/(.*?)(?=/\\d+)"
          },

          "entityProjectAttribute": {

            "dataAttributeName": "href",

            "dataRegEx": ".*([a-f0-9]{8}-[a-f0-9]{4}-[a-f0-9]{4}-[a-f0-9]{4}-[a-f0-9]{12})/_workitems/edit/.*"
          }

        }

      ],
      "entityURLDetails": [

       {
          "entityWebURLMatcher": "a[href~=/browse/[A-Z_a-z0-9-]+-\\d+]",

          "entityIdDataSelector": ".*\\/browse/([A-Za-z0-9-]+-\\d+)]"
       }

      ]

    }

}

// Internal note: For attachment, comment, link: readSupported, writeSupported can be derived from sync direction of entityType.

```


