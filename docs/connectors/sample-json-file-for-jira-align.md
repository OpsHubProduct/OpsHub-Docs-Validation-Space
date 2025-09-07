### JSON Metadata Sample for Jira Align

* Below is the sample JSON for Jira Align entities. Based on your use case and Jira Align instance configuration, the JSON needs to be modified.

```json
 {
	"entities": [
		{
			"internalName": "Capabilities",
			"displayName": "Capability",
			"readMechanism": "HISTORY",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "description",
				"projectEntityType": "PROGRAM",
				"projectFieldInternalName": "primaryProgramId"
			},
			"fields": {
				"system": [
					{
						"internalName": "title",
						"displayName": "Title",
						"dataType": "text",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Title"
						}
					},
					{
						"internalName": "state",
						"displayName": "State",
						"dataType": "lookup",
						"mandatory": true,
						"lookUpValues": {
							"1": "1 - Not Started",
							"2": "2 - In Progress",
							"3": "3 - Accepted"
						},
						"systemSpecific": {
							"fieldNameInRevision": "State"
						}
					},
					{
						"internalName": "primaryProgramId",
						"displayName": "Primary Program",
						"dataType": "reference",
						"mandatory": true,
						"systemSpecific": {
							"lookuptype": "Programs",
							"fieldNameInRevision": "Primary Program"
						}
					},
					{
						"internalName": "parentId",
						"displayName": "Portfolio Epic",
						"systemSpecific": {
							"entityType": "Epics",
							"lookuptype": "Epics",
							"fieldNameInRevision": "Parent Portfolio Epic"
						},
						"dataType": "reference",
						"mandatory": true
					},
					{
						"internalName": "tags",
						"displayName": "Tags",
						"dataType": "text",
						"multiselect": true,
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Tags"
						}
					},
					{
						"internalName": "customerIds",
						"displayName": "Customers",
						"dataType": "lookup",
						"mandatory": true,
						"multiselect": true,
						"lookUpValues": {
							"213": "ABC",
							"162": "Big Data",
							"200": "GE"
						},
						"systemSpecific": {
							"fieldNameInRevision": "CustomerIds"
						}
					},
					{
						"internalName": "description",
						"displayName": "Description",
						"dataType": "text",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Description"
						}
					},
					{
						"internalName": "type",
						"displayName": "Type",
						"dataType": "lookup",
						"mandatory": true,
						"lookUpValues": {
							"1": "Business",
							"2": "Enabler",
							"3": "Non Functional",
							"4": "Architectural",
							"5": "Supporting"
						},
						"systemSpecific": {
							"fieldNameInRevision": "Type"
						}
					}
				],
				"custom": [
					{
						"internalName": "customfield_90386",
						"displayName": "Remote Link",
						"dataType": "text",
						"mandatory": false,
						"systemSpecific": {
							"fieldNameInRevision": "Remote Link"
						}
					},
					{
						"internalName": "customfield_90387",
						"displayName": "Remote Id",
						"dataType": "text",
						"mandatory": false,
						"systemSpecific": {
							"fieldNameInRevision": "Remote Id"
						}
					},
					{
						"internalName": "customfield_90764",
						"displayName": "Custom multi dropdown",
						"dataType": "lookup",
						"multiselect": true,
						"mandatory": false,
						"systemSpecific": {
							"fieldNameInRevision": "Custom multi dropdown"
						},
						"lookUpValues": {
							"33": "option1",
							"70": "option2",
							"71": "option3",
							"72": "option4"
						}
					},
					{
						"internalName": "customfield_90389",
						"displayName": "single select drop down",
						"dataType": "lookup",
						"mandatory": false,
						"systemSpecific": {
							"fieldNameInRevision": "single select drop down"
						},
						"lookUpValues": {
							"12": "one",
							"13": "two",
							"14": "New Item"
						}
					},
					{
						"internalName": "customfield_90388",
						"displayName": "Custom Text",
						"dataType": "text",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Custom Text"
						}
					}
				]
			},
			"relationship": {
				"entities": [
					{
						"internalName": "Epics",
						"displayName": "Epics",
						"supportedAsSource": true,
						"supportedAsTarget": true
					},
					{
						"internalName": "Programs",
						"displayName": "Program",
						"supportedAsSource": true,
						"supportedAsTarget": true
					}
				],
				"linkTypes": [
					{
						"linkType": "Portfolio Epic",
						"linkCardinality": "OneToOne",
						"reverseLinkType": null,
						"mandatory": false,
						"supportedAsSource": true,
						"supportedAsTarget": true
					}
				]
			}
		},
		{
			"internalName": "Valuestreams",
			"displayName": "Value Streams",
			"readMechanism": "NON_TIMESTAMP",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "teamDescription",
				"projectEntityType": "ENTERPRISE"
			},
			"fields": {
				"system": [
					{
						"internalName": "name",
						"displayName": "Name",
						"dataType": "text",
						"mandatory": true
					},
					{
						"internalName": "programIds",
						"displayName": "Program",
						"multiselect": true,
						"dataType": "reference",
						"systemSpecific": {
							"lookuptype": "Programs"
						},
						"mandatory": true
					},
					{
						"internalName": "isActive",
						"displayName": "Active",
						"dataType": "numeric",
						"mandatory": true
					},
					{
						"internalName": "mapToState",
						"displayName": "Map To State",
						"dataType": "numeric",
						"mandatory": true
					},
					{
						"internalName": "regionId",
						"displayName": "Region",
						"dataType": "numeric",
						"mandatory": true
					},
					{
						"internalName": "teamDescription",
						"displayName": "Team Description",
						"dataType": "text",
						"mandatory": true
					},
					{
						"internalName": "level",
						"displayName": "Level",
						"dataType": "lookup",
						"mandatory": true,
						"lookUpValues": {
							"1": "Initiative",
							"2": "Epic",
							"3": "Story",
							"4": "Theme",
							"5": "Capability"
						}
					},
					{
						"internalName": "processSteps",
						"displayName": "Process Steps",
						"dataType": "test-step",
						"mandatory": false
					}
				],
				"custom": []
			},
			"relationship": {
				"entities": [],
				"linkTypes": []
			}
		},
		{
			"internalName": "Products",
			"displayName": "Product",
			"readMechanism": "NON_TIMESTAMP",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "shortName",
				"projectEntityType": "ENTERPRISE"
			},
			"fields": {
				"system": [
					{
						"internalName": "title",
						"displayName": "Product",
						"dataType": "text",
						"mandatory": true
					},
					{
						"internalName": "shortName",
						"displayName": "Short Name",
						"dataType": "text",
						"mandatory": true
					},
					{
						"internalName": "divisionId",
						"displayName": "Organization Structure",
						"dataType": "text",
						"mandatory": false
					},
					{
						"internalName": "parentProductId",
						"displayName": "Parent Product",
						"systemSpecific": {
							"entityType": "Product"
						},
						"dataType": "numeric",
						"mandatory": false
					}
				],
				"custom": []
			},
			"relationship": {
				"entities": [
					{
						"internalName": "Products",
						"displayName": "Product",
						"supportedAsSource": true,
						"supportedAsTarget": true
					}
				],
				"linkTypes": [
					{
						"linkType": "Parent Product",
						"linkCardinality": "OneToOne",
						"reverseLinkType": null,
						"mandatory": false,
						"supportedAsSource": true,
						"supportedAsTarget": true
					}
				]
			}
		},
		{
			"internalName": "Customers",
			"displayName": "Customer",
			"readMechanism": "NON_TIMESTAMP",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "name",
				"projectEntityType": "ENTERPRISE"
			},
			"fields": {
				"system": [
					{
						"internalName": "name",
						"displayName": "Name",
						"dataType": "text",
						"mandatory": true
					}
				],
				"custom": []
			},
			"relationship": {
				"entities": [],
				"linkTypes": []
			}
		},
		{
			"internalName": "Epics",
			"displayName": "Portfolio Epic",
			"readMechanism": "HISTORY",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "fieldInternalname",
				"projectEntityType": "PROGRAM",
				"projectFieldInternalName": "primaryProgramId"
			},
			"fields": {
				"system": [
					{
						"internalName": "title",
						"displayName": "Title",
						"systemSpecific": {
							"timeUnitInSystem ": "Hours",
							"fieldNameInRevision": "Name"
						},
						"dataType": "text",
						"mandatory": true
					},
					{
						"internalName": "state",
						"displayName": "State",
						"dataType": "numeric",
						"systemSpecific": {
							"fieldNameInRevision": "State"
						},
						"mandatory": true
					},
					{
						"internalName": "primaryProgramId",
						"displayName": "Primary Program",
						"dataType": "numeric",
						"systemSpecific": {
							"fieldNameInRevision": "Program"
						},
						"mandatory": true
					},
					{
						"internalName": "description",
						"displayName": "Description",
						"dataType": "text",
						"systemSpecific": {
							"fieldNameInRevision": "Description"
						},
						"mandatory": true
					},
					{
						"internalName": "type",
						"displayName": "Type",
						"dataType": "numeric",
						"systemSpecific": {
							"fieldNameInRevision": "Type"
						},
						"mandatory": true
					},
					{
						"internalName": "tags",
						"displayName": "Tags",
						"dataType": "text",
						"multiselect": true,
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Tags"
						}
					},
					{
						"internalName": "customerIds",
						"displayName": "Customers",
						"dataType": "lookup",
						"mandatory": true,
						"multiselect": true,
						"lookUpValues": {
							"213": "ABC",
							"162": "Big Data",
							"200": "GE"
						},
						"systemSpecific": {
							"fieldNameInRevision": "CustomerIds"
						}
					}
				],
				"custom": [
					{
						"internalName": "customfield_90779",
						"displayName": "Remote Link",
						"dataType": "text",
						"mandatory": false,
						"systemSpecific": {
							"fieldNameInRevision": "Remote Link"
						}
					},
					{
						"internalName": "customfield_90768",
						"displayName": "Custom multi dropdown",
						"dataType": "lookup",
						"multiselect": true,
						"mandatory": false,
						"systemSpecific": {
							"fieldNameInRevision": "Custom multi dropdown"
						},
						"lookUpValues": {
							"73": "option1",
							"74": "option2",
							"75": "option3",
							"76": "option4"
						}
					},
					{
						"internalName": "customfield_90687",
						"displayName": "single select drop down",
						"dataType": "lookup",
						"multiselect": true,
						"mandatory": false,
						"systemSpecific": {
							"fieldNameInRevision": "single select drop down"
						},
						"lookUpValues": {
							"81": "one",
							"82": "two",
							"83": "New Item"
						}
					},
					{
						"internalName": "customfield_90968",
						"displayName": "Custom Text",
						"dataType": "text",
						"mandatory": false,
						"systemSpecific": {
							"fieldNameInRevision": "Custom Text"
						}
					},
					{
						"internalName": "customfield_90969",
						"displayName": "Remote Id",
						"dataType": "text",
						"mandatory": false,
						"systemSpecific": {
							"fieldNameInRevision": "Remote Id"
						}
					}
				]
			},
			"relationship": {
				"entities": [],
				"linkTypes": []
			}
		},
		{
			"internalName": "Stories",
			"displayName": "Story",
			"readMechanism": "HISTORY",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"projectEntityType": "PROGRAM"
			},
			"fields": {
				"system": [
					{
						"internalName": "title",
						"displayName": "Title",
						"dataType": "text",
						"systemSpecific": {
							"fieldNameInRevision": "Title"
						},
						"mandatory": true
					},
					{
						"internalName": "ownerId",
						"displayName": "Assigned",
						"dataType": "user",
						"mandatory": false,
						"systemSpecific": {
							"fieldNameInRevision": "Owner"
						}
					},
					{
						"internalName": "state",
						"displayName": "State",
						"dataType": "numeric",
						"systemSpecific": {
							"fieldNameInRevision": "State"
						},
						"mandatory": true
					},
					{
						"internalName": "description",
						"displayName": "Story",
						"dataType": "text",
						"systemSpecific": {
							"fieldNameInRevision": "Description"
						},
						"mandatory": true
					},
					{
						"internalName": "programId",
						"displayName": "Program",
						"dataType": "numeric",
						"systemSpecific": {
							"fieldNameInRevision": "Program"
						},
						"mandatory": true
					},
					{
						"internalName": "featureId",
						"displayName": "Feature",
						"dataType": "numeric",
						"systemSpecific": {
							"entityType": "Feature",
							"fieldNameInRevision": "feature"
						},
						"mandatory": false
					},
					{
						"internalName": "assumption",
						"displayName": "Design/Assumptions/Notes",
						"dataType": "text",
						"systemSpecific": {
							"fieldNameInRevision": "Assumption"
						},
						"mandatory": true
					}
				],
				"custom": []
			},
			"relationship": {
				"entities": [
					{
						"internalName": "Features",
						"displayName": "Feature",
						"supportedAsSource": true,
						"supportedAsTarget": true
					}
				],
				"linkTypes": [
					{
						"linkType": "Feature",
						"linkCardinality": "OneToOne",
						"reverseLinkType": null,
						"mandatory": false,
						"supportedAsSource": true,
						"supportedAsTarget": true
					}
				]
			}
		},
		{
			"internalName": "Features",
			"displayName": "Feature",
			"readMechanism": "HISTORY",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "fieldInternalname",
				"projectEntityType": "PROGRAM",
				"projectFieldInternalName": "primaryProgramId"
			},
			"fields": {
				"system": [
					{
						"internalName": "title",
						"displayName": "Title",
						"dataType": "text",
						"systemSpecific": {
							"fieldNameInRevision": "Title"
						},
						"mandatory": true
					},
					{
						"internalName": "state",
						"displayName": "State",
						"dataType": "lookup",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "State"
						},
						"lookUpValues": {
							"0": "0 - Pending Approval",
							"1": "1 - Ready To Start",
							"2": "2 - In Progress",
							"3": "3 - Dev Complete",
							"4": "4 - Test Complete",
							"5": "5 - Accepted"
						}
					},
					{
						"internalName": "primaryProgramId",
						"displayName": "Primary Program",
						"systemSpecific": {
							"lookuptype": "Programs",
							"fieldNameInRevision": "Program"
						},
						"dataType": "reference",
						"mandatory": true
					},
					{
						"internalName": "productId",
						"displayName": "Product",
						"systemSpecific": {
							"lookuptype": "Products",
							"fieldNameInRevision": "Product"
						},
						"dataType": "reference",
						"mandatory": true
					},
					{
						"internalName": "description",
						"displayName": "Description",
						"dataType": "text",
						"systemSpecific": {
							"fieldNameInRevision": "Description"
						},
						"mandatory": true
					},
					{
						"internalName": "type",
						"displayName": "Type",
						"dataType": "lookup",
						"mandatory": false,
						"systemSpecific": {
							"fieldNameInRevision": "Type"
						},
						"lookUpValues": {
							"1": "Business",
							"2": "Enabler",
							"3": "Non Functional",
							"4": "Architectural",
							"5": "Supporting"
						}
					},
					{
						"internalName": "parentId",
						"displayName": "Portfolio Epic",
						"dataType": "numeric",
						"systemSpecific": {
							"entityType": "Portfolio Epic",
							"fieldNameInRevision": "Parent Portfolio Epic"
						},
						"mandatory": false
					},
					{
						"internalName": "priority",
						"displayName": "Priority",
						"dataType": "lookup",
						"mandatory": false,
						"systemSpecific": {
							"fieldNameInRevision": "Priority"
						},
						"lookUpValues": {
							"1": "Critical",
							"2": "High",
							"3": "Medium",
							"4": "Low"
						}
					},
					{
						"internalName": "startInitiationDate",
						"displayName": "Start / Initiation",
						"dataType": "date_string",
						"systemSpecific": {
							"fieldNameInRevision": "Start / Initiation"
						},
						"mandatory": false
					},
					{
						"internalName": "benefits",
						"displayName": "Benefits",
						"dataType": "text",
						"systemSpecific": {
							"fieldNameInRevision": "Benefits"
						},
						"mandatory": false
					},
					{
						"internalName": "estimateTshirt",
						"displayName": "T-Shirt",
						"dataType": "lookup",
						"mandatory": false,
						"systemSpecific": {
							"fieldNameInRevision": "T-Shirt"
						},
						"lookUpValues": {
							"19": "X-Small",
							"20": "Small",
							"15": "Medium",
							"16": "Large",
							"17": "XL",
							"18": "XXL"
						}
					}
				],
				"custom": []
			},
			"relationship": {
				"entities": [
					{
						"internalName": "Epics",
						"displayName": "Portfolio Epic",
						"supportedAsSource": true,
						"supportedAsTarget": true
					}
				],
				"linkTypes": [
					{
						"linkType": "Portfolio Epic",
						"linkCardinality": "OneToOne",
						"reverseLinkType": null,
						"mandatory": false,
						"supportedAsSource": true,
						"supportedAsTarget": true
					}
				]
			}
		},
		{
			"internalName": "Defects",
			"displayName": "Defect",
			"readMechanism": "HISTORY",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "fieldInternalname",
				"projectEntityType": "PROGRAM"
			},
			"fields": {
				"system": [
					{
						"internalName": "title",
						"displayName": "Title",
						"systemSpecific": {
							"fieldNameInRevision": "Title"
						},
						"dataType": "text",
						"mandatory": true
					},
					{
						"internalName": "state",
						"displayName": "State",
						"dataType": "lookup",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "State"
						},
						"lookUpValues": {
							"1": "Active",
							"2": "In-Work",
							"3": "Pending Test",
							"4": "Verifying",
							"5": "Fixed",
							"6": "Not A Bug",
							"7": "CNR By Design",
							"8": "Postponed",
							"9": "Duplicate"
						}
					},
					{
						"internalName": "priority",
						"displayName": "Priority",
						"dataType": "lookup",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Priority"
						},
						"lookUpValues": {
							"1": "1 Resolve Immediately",
							"2": "2 High Attention",
							"3": "3 Normal",
							"4": "4 Low"
						}
					},
					{
						"internalName": "severity",
						"displayName": "Severity",
						"dataType": "lookup",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Severity"
						},
						"lookUpValues": {
							"1": "1 Crash / Data Loss",
							"2": "2 Major Problem",
							"3": "3 Minor Problem",
							"4": "4 Cosmetic"
						}
					},
					{
						"internalName": "programId",
						"displayName": "ProgramId",
						"dataType": "reference",
						"systemSpecific": {
							"lookuptype": "Programs",
							"fieldNameInRevision": "Program"
						},
						"mandatory": true
					},
					{
						"internalName": "isStatusOpen",
						"displayName": "isStatusOpen",
						"dataType": "text",
						"systemSpecific": {
							"fieldNameInRevision": "Status"
						},
						"mandatory": true
					},
					{
						"internalName": "stepsToReproduce",
						"displayName": "Steps To Reproduce",
						"dataType": "text",
						"systemSpecific": {
							"fieldNameInRevision": "Steps to Reproduce"
						},
						"mandatory": true
					},
					{
						"internalName": "fixResults",
						"displayName": "Fix Results",
						"dataType": "text",
						"systemSpecific": {
							"fieldNameInRevision": "Fix Results"
						},
						"mandatory": false
					},
					{
						"internalName": "description",
						"displayName": "Description",
						"dataType": "text",
						"systemSpecific": {
							"fieldNameInRevision": "Description"
						},
						"mandatory": true
					}
				],
				"custom": [
					{
						"internalName": "customfield_90719",
						"displayName": "Custom text",
						"dataType": "text",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Custom text"
						}
					},
					{
						"internalName": "customfield_90722",
						"displayName": "custom dropdown",
						"dataType": "lookup",
						"mandatory": true,
						"lookUpValues": {
							"6": "op1",
							"7": "op2",
							"45": "op3"
						},
						"systemSpecific": {
							"fieldNameInRevision": "custom dropdown"
						}
					},
					{
						"internalName": "customfield_90721",
						"displayName": "cust text area",
						"dataType": "text",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "cust text area"
						}
					},
					{
						"internalName": "customfield_90758",
						"displayName": "custom multi dropdown",
						"dataType": "lookup",
						"mandatory": true,
						"multiselect": true,
						"lookUpValues": {
							"2": "option1",
							"3": "option2",
							"4": "option3",
							"15": "option4",
							"16": "option5"
						},
						"systemSpecific": {
							"fieldNameInRevision": "custom multi dropdown"
						}
					}
				]
			},
			"relationship": {
				"entities": [],
				"linkTypes": []
			}
		},
		{
			"internalName": "Regions",
			"displayName": "Region",
			"readMechanism": "NON_TIMESTAMP",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "fieldInternalname",
				"projectEntityType": "ENTERPRISE"
			},
			"fields": {
				"system": [
					{
						"internalName": "title",
						"displayName": "Title",
						"systemSpecific": {
							"timeUnitInSystem ": "Hours"
						},
						"dataType": "text",
						"mandatory": true
					}
				],
				"custom": []
			},
			"relationship": {
				"entities": [],
				"linkTypes": []
			}
		},
		{
			"internalName": "Cities",
			"displayName": "City",
			"readMechanism": "NON_TIMESTAMP",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "fieldInternalname",
				"projectEntityType": "ENTERPRISE"
			},
			"fields": {
				"system": [
					{
						"internalName": "title",
						"displayName": "Title",
						"systemSpecific": {
							"timeUnitInSystem ": "Hours"
						},
						"dataType": "text",
						"mandatory": true
					},
					{
						"internalName": "regionId",
						"displayName": "Region",
						"systemSpecific": {
							"entityType": "regions"
						},
						"dataType": "numeric",
						"mandatory": true
					}
				],
				"custom": []
			},
			"relationship": {
				"entities": [
					{
						"internalName": "regions",
						"displayName": "Region",
						"supportedAsSource": true,
						"supportedAsTarget": true
					}
				],
				"linkTypes": [
					{
						"linkType": "Region",
						"linkCardinality": "OneToOne",
						"reverseLinkType": null,
						"mandatory": true,
						"supportedAsSource": true,
						"supportedAsTarget": true
					}
				]
			}
		},
		{
			"internalName": "Themes",
			"displayName": "Theme",
			"readMechanism": "HISTORY",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "fieldInternalname",
				"projectEntityType": "ENTERPRISE"
			},
			"fields": {
				"system": [
					{
						"internalName": "fieldInternalName1",
						"displayName": "Field Display Name",
						"systemSpecific": {
							"timeUnitInSystem ": "Hours"
						},
						"dataType": "text"
					},
					{
						"internalName": "fieldInternalName1",
						"displayName": "Field Display Name",
						"dataType": "date",
						"dateFormat": "dd/mm/yyyy"
					}
				],
				"custom": []
			},
			"relationship": {
				"entities": [
					{
						"internalName": "supportedEntityInternalName1",
						"displayName": "Supported Entity Display Name1",
						"supportedAsSource": true,
						"supportedAsTarget": true
					},
					{
						"internalName": "supportedEntityInternalName2",
						"displayName": "Supported Entity Display Name2"
					}
				],
				"linkTypes": [
					{
						"linkType": "Link Type Name",
						"linkCardinality": "OneToOne",
						"reverseLinkType": null,
						"mandatory": true,
						"supportedAsSource": true,
						"supportedAsTarget": true
					}
				]
			}
		},
		{
			"internalName": "Objectives",
			"displayName": "Objective",
			"readMechanism": "HISTORY",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "notes",
				"projectEntityType": "PROGRAM"
			},
			"fields": {
				"system": [
					{
						"internalName": "name",
						"displayName": "Name",
						"dataType": "text",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Name"
						}
					},
					{
						"internalName": "tier",
						"displayName": "Tier",
						"dataType": "numeric",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Tier"
						}
					},
					{
						"internalName": "description",
						"displayName": "Description",
						"dataType": "text",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Description"
						}
					},
					{
						"internalName": "programId",
						"displayName": "Program",
						"dataType": "reference",
						"mandatory": true,
						"systemSpecific": {
							"lookuptype": "Programs",
							"fieldNameInRevision": "Programs"
						}
					},
					{
						"internalName": "releaseIds",
						"displayName": "Program Increment",
						"dataType": "lookup",
						"systemSpecific": {
							"lookuptype": "releases",
							"fieldNameInRevision": "Program Increment"
						},
						"multiselect": true,
						"mandatory": true
					},
					{
						"internalName": "targetSyncSprintId",
						"displayName": "Target Sync Sprint",
						"dataType": "numeric",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Target Sync Sprint"
						}
					},
					{
						"internalName": "ownerId",
						"displayName": "Owner",
						"dataType": "user",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "OwnerId"
						}
					}
				],
				"custom": []
			},
			"relationship": {
				"entities": [],
				"linkTypes": []
			}
		},
		{
			"internalName": "Sprints",
			"displayName": "Sprints",
			"readMechanism": "NON_TIMESTAMP",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "description",
				"projectEntityType": "PROGRAM"
			},
			"fields": {
				"system": [
					{
						"internalName": "title",
						"displayName": "Sprint Name",
						"dataType": "text",
						"mandatory": true
					},
					{
						"internalName": "shortName",
						"displayName": "Short Name",
						"dataType": "text",
						"mandatory": true
					},
					{
						"internalName": "relStatus",
						"displayName": "Status",
						"dataType": "lookup",
						"lookUpValues": {
							"1": "Planning",
							"2": "In Progress",
							"3": "Done",
							"4": "Archive"
						},
						"mandatory": true
					},
					{
						"internalName": "releaseId",
						"displayName": "Program Increment",
						"dataType": "lookup",
						"systemSpecific": {
							"lookuptype": "releases"
						},
						"mandatory": true
					},
					{
						"internalName": "teamId",
						"displayName": "Team",
						"dataType": "lookup",
						"systemSpecific": {
							"lookuptype": "teams"
						},
						"mandatory": true
					},
					{
						"internalName": "programId",
						"displayName": "Program",
						"dataType": "lookup",
						"systemSpecific": {
							"lookuptype": "Programs"
						},
						"mandatory": true
					},
					{
						"internalName": "goal",
						"displayName": "Goal",
						"dataType": "text",
						"mandatory": true
					},
					{
						"internalName": "anchorSprintId",
						"displayName": "Sync Date",
						"dataType": "lookup",
						"lookUpValues": {
							"185": "Sprint_AUT_S1: 2021-03-01 - 2021-03-10",
							"186": "Sprint_AUT_T1: 2021-03-01 - 2021-03-10"
						},
						"mandatory": true
					},
					{
						"internalName": "description",
						"displayName": "Description",
						"dataType": "text",
						"mandatory": true
					}
				],
				"custom": []
			},
			"relationship": {
				"entities": [],
				"linkTypes": []
			}
		},
		{
			"internalName": "Programs",
			"displayName": "Program",
			"readMechanism": "HISTORY",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "fieldInternalname",
				"projectEntityType": "PORTFOLIO"
			},
			"fields": {
				"system": [],
				"custom": []
			},
			"relationship": {
				"entities": [
					{
						"internalName": "supportedEntityInternalName1",
						"displayName": "Supported Entity Display Name1",
						"supportedAsSource": true,
						"supportedAsTarget": true
					},
					{
						"internalName": "supportedEntityInternalName2",
						"displayName": "Supported Entity Display Name2"
					}
				],
				"linkTypes": [
					{
						"linkType": "Link Type Name",
						"linkCardinality": "OneToOne",
						"reverseLinkType": null,
						"mandatory": true,
						"supportedAsSource": true,
						"supportedAsTarget": true
					}
				]
			}
		},
		{
			"internalName": "Portfolios",
			"displayName": "Portfolios",
			"readMechanism": "NON_TIMESTAMP",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "fieldInternalname",
				"projectEntityType": "ENTERPRISE"
			},
			"fields": {
				"system": [
					{
						"internalName": "title",
						"displayName": "Portfolio Name",
						"dataType": "text",
						"mandatory": true
					},
					{
						"internalName": "description",
						"displayName": "Description",
						"dataType": "text",
						"mandatory": true
					},
					{
						"internalName": "divisionId",
						"displayName": "Parent Organization",
						"dataType": "lookup",
						"lookUpValues": {
							"31": "111",
							"16": "Mainstream Financial",
							"29": "Org 1",
							"30": "Org 2",
							"18": "Personal Business"
						},
						"mandatory": true
					},
					{
						"internalName": "teamDescription",
						"displayName": "Team Description",
						"dataType": "text",
						"mandatory": true
					},
					{
						"internalName": "regionId",
						"displayName": "Region",
						"dataType": "reference",
						"systemSpecific": {
							"lookuptype": "regions"
						},
						"mandatory": true
					}
				],
				"custom": []
			},
			"relationship": {
				"entities": [
					{
						"internalName": "Programs",
						"displayName": "Programs",
						"supportedAsSource": true,
						"supportedAsTarget": true
					}
				],
				"linkTypes": [
					{
						"linkType": "Programs",
						"linkCardinality": "OneToMany",
						"reverseLinkType": null,
						"supportedAsSource": true,
						"supportedAsTarget": true
					}
				]
			}
		},
		{
			"internalName": "Ideas",
			"displayName": "Ideation",
			"readMechanism": "HISTORY",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "fieldInternalname",
				"projectEntityType": "ENTERPRISE"
			},
			"fields": {
				"system": [
					{
						"internalName": "title",
						"displayName": "Title",
						"dataType": "text",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Title"
						}
					},
					{
						"internalName": "description",
						"displayName": "Description",
						"dataType": "text",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Description"
						}
					},
					{
						"internalName": "groupId",
						"displayName": "Group",
						"dataType": "text",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Group"
						}
					},
					{
						"internalName": "ownerId",
						"displayName": "Owner",
						"dataType": "user",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "OwnerId"
						}
					},
					{
						"internalName": "status",
						"displayName": "Status",
						"dataType": "lookup",
						"lookUpValues": {
							"0": "New",
							"1": "Open",
							"2": "Planned",
							"3": "Completed",
							"4": "Shelved"
						},
						"mandatory": false
					},
					{
						"internalName": "categoryId",
						"displayName": "Category",
						"dataType": "lookup",
						"lookUpValues": {
							"1": "Enhancement",
							"3": "Question",
							"2": "Ticket"
						},
						"mandatory": true
					}
				],
				"custom": []
			},
			"relationship": {
				"entities": [],
				"linkTypes": []
			}
		},
		{
			"internalName": "Tasks",
			"displayName": "Task",
			"readMechanism": "HISTORY",
			"hasReadSupport": true,
			"hasWriteSupport": true,
			"entityScope": "Global",
			"systemSpecific": {
				"OH_LastUpdatedField": "description",
				"projectEntityType": "PROGRAM"
			},
			"fields": {
				"system": [
					{
						"internalName": "title",
						"displayName": "Title",
						"dataType": "text",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Title"
						}
					},
					{
						"internalName": "storyId",
						"displayName": "Story",
						"multiselect": false,
						"dataType": "numeric",
						"systemSpecific": {
							"fieldNameInRevision": "Story"
						},
						"mandatory": true
					},
					{
						"internalName": "state",
						"displayName": "State",
						"dataType": "lookup",
						"lookUpValues": {
							"1": "1 - Not Started",
							"2": "2 - In Progress",
							"3": "3 - Accepted"
						},
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "State"
						}
					},
					{
						"internalName": "description",
						"displayName": "Description",
						"dataType": "text",
						"mandatory": true,
						"systemSpecific": {
							"fieldNameInRevision": "Description"
						}
					},
					{
						"internalName": "ownerId",
						"displayName": "Owner",
						"mandatory": false,
						"dataType": "user",
						"systemSpecific": {
							"fieldNameInRevision": "Owner"
						}
					},
					{
						"internalName": "effortHours",
						"displayName": "Effort",
						"dataType": "numeric",
						"mandatory": true
					}
				],
				"custom": []
			},
			"relationship": {
				"entities": [],
				"linkTypes": []
			}
		}
	],
	"projects": [
		{
			"internalName": "4",
			"displayName": "Legacy Apps",
			"entities": []
		},
		{
			"internalName": "8",
			"displayName": "Digital Services",
			"entities": [
				{
					"internalName": "defects",
					"displayName": "Defect Override",
					"hasReadSupport": true
				}
			]
		},
		{
			"internalName": "9",
			"displayName": "new portfolio",
			"entities": []
		},
		{
			"internalName": "10",
			"displayName": "portfolio 2",
			"entities": []
		},
		{
			"internalName": "11",
			"displayName": "portfolio from api",
			"entities": []
		},
		{
			"internalName": "12",
			"displayName": "Automation_Portfolio_Source",
			"entities": []
		},
		{
			"internalName": "50",
			"displayName": "Automation_Portfolio_S",
			"entities": []
		},
		{
			"internalName": "20",
			"displayName": "Automation_Portfolio_S2",
			"entities": []
		},
		{
			"internalName": "51",
			"displayName": "Automation_Portfolio_T",
			"entities": []
		},
		{
			"internalName": "50",
			"displayName": "Automation_Portfolio_Target",
			"entities": []
		},
		{
			"internalName": "56",
			"displayName": "Automation_Program_S2",
			"entities": []
		},
		{
			"internalName": "80",
			"displayName": "Demo Program",
			"entities": []
		}
	]
}
```