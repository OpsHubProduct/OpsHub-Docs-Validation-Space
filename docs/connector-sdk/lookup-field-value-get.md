# lookup-field-value-get

\# Overview

OpsHub will call this API for fields of type LOOKUP. Implementation of this API should return valid values that the user can set in a given lookup field.

\# API URI

```http

GET: /metadata/fields/{fieldId}/values?projectId=<projectId>\&entityTypeId=<entityTypeId>\&fieldScope=<FieldScope>

```

\# URI Parameters

\| Name | In | Required | Type | Description |

\|--------------|------|----------|--------|-------------|

\| entityTypeId | path | True | String | ‘id’ of entity type returned as response of \*\*Entity Type – List\*\* API |

\| fieldId | path | True | String | Id of the field, as sent by Connector SDK from `/entity-types/{entityTypeId}` API |

\| projectId | query| True | String | Project id for which the list of entity types is available. ProjectId here will be the same as ‘id’ sent as part of `/projects` |

\| FieldScope | query| True | ENUM | Scope where Lookup values for a field are to be displayed.\
\- \*\*ENTITY\_FIELD\*\*: Provide 'ENTITY\_FIELD' when lookup values are to be displayed at mapping level.\
\- \*\*CONFIG\_FIELD\*\*: Provide 'CONFIG\_FIELD' when lookup values are to be displayed at advanced integration configuration level in entity-level mandatory settings screen. |

\# Response Payload

```json

\[

&nbsp; {

&nbsp;   "id": "<id1>",

&nbsp;   "value": "<value1>"

&nbsp; },

&nbsp; {

&nbsp;   "id": "<id2>",

&nbsp;   "value": "<value2>"

&nbsp; },

&nbsp; {

&nbsp;   "id": "<id3>",

&nbsp;   "value": "<value3>"

&nbsp; }

]

```

\# Response Parameters

\| Name | Required | Type | Description |

\|-------|----------|--------|-------------|

\| id | True | String | Internal value of the field. For example, for priority field: "low", "medium", "high". If the end system does not have a different internal name for a field value, pass the display name here as well. |

\| value | True | String | Display value of the field. For example, for priority field: "Low", "Medium", "High". |

\# Examples

1\) Sample response for priority field:

```json

\[

&nbsp; {

&nbsp;   "id": "1",

&nbsp;   "value": "High"

&nbsp; },

&nbsp; {

&nbsp;   "id": "2",

&nbsp;   "value": "Medium"

&nbsp; },

&nbsp; {

&nbsp;   "id": "3",

&nbsp;   "value": "Low"

&nbsp; }

]

```

2\) Sample response for priority field with same id and value:

\[

&#x20; {

&#x20; "id": "High",

&#x20; "value": "High"

&#x20; },

&#x20; {

&#x20; "id": "Medium",

&#x20; "value": "Medium"

&#x20; },

&#x20; {

&#x20; "id": "Low",

&#x20; "value": "Low"

&#x20; }

]

```
```
