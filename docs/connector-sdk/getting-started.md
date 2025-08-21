# Overview
SDK REST APIs are used by OpsHub to interact with connector SDK to read and write data in the end system.  
These APIs can be written in any language and hosted anywhere, as long as the OpsHub integration server can access them.

# Gathering the Requirements and Integration Modelling

- Refer to the following document to check the required APIs in the end system for implementing a connector:  
  **[API Recommendation for Connector](https://opshubtrial-my.sharepoint.com/:w:/g/personal/support_opshub_com/EcI_EH7thh1Mh6Qf9c7ry28BqgMe-6Y5zrVDNYDH35iVkA?e=YuIOnx)**

- Refer to the following document and fill in all the details.  
  These details will help you implement a connector based on Connector SDK:  
  **[SDK Technical Analysis Document](https://opshubtrial-my.sharepoint.com/:w:/g/personal/support_opshub_com/Efx9aSynlVJIi0DiO2wObLkB0_tvgddwudtcRKXDHE1Gaw?e=uZH56V)**

# Start Connector Development

## SDK APIs
- Refer to **[Build Your Own Connector](build-your-own-connector.md)** page for the list of APIs to implement a connector.

### SDK Bootstrap Package
If an SDK Connector is going to be developed in **Java**,  
a quick start package is available with:
- Basic skeleton of all the APIs to be implemented
- Request and response Java objects for each API
- Sample REST client
- Various utilities

Click **[here](https://opshubtrial-my.sharepoint.com/:b:/g/personal/support_opshub_com/EVms9TRc3Y5Kgby0NIsEvTkBGFnaKbNVUnae2I9fR9EXFA?e=GlNQaH)** to download the documentation for the Connector SDK Bootstrap Package.

The bootstrap package can be downloaded from the table below.


## SDK Server Bootstrap Package vs OIM Version Compatibility Matrix

| SDK Server  | OIM Version Range          | Remarks |
|-------------|----------------------------|---------|
| [1.17.0]    | >= 7.198                   | Added support for bulk linking and link ordering |
| [1.16.0]    | >= 7.197 and < 7.198       | Added support for systemId to store system-specific cache and `cleanupGlobalCache` flag to control cache cleanup. <br> Added support for adding multiple inline URL prefixes. |
| [1.15.0]    | >= 7.189 and < 7.197       | Added support for Rank synchronization |
| [1.14.0]    | >= 7.188 and < 7.189       | Added support for attachment file comment |
| [1.13.0]    | >= 7.184 and < 7.188       | Added support for forming Remote Link using different base URL |
| [1.12.0]    | >= 7.182 and < 7.184       | Added support for 'fetch mapped data only' feature |
| [1.11.0]    | >= 7.179 and < 7.182       | Added support for entity type and project movement. <br> Added provision for filtering comments after specified time. |
| [1.10.0]    | >= 7.177 and < 7.179       | Optimized Entity-List API |
| [1.9.0]     | >= 7.174 and < 7.177       | Added support for UserMention and EntityMention for Markdown datatype, and introduced support for `subStepNumber` in `updateEntity`. |
| [1.8.0]     | >= 7.168 and < 7.174       | Added support for dynamic retrieval of lookup fields in integration advanced setting screens |
| [1.7.0]     | >= 7.165 and < 7.168       | Added support for searching Entity Mention and User Mention in fields or comments of HTML type using regex |
| [1.6.0]     | >= 7.162 and < 7.165       | Added support for reference fields and upgraded Spring Boot version to 3.2.3 |
| [1.5.0]     | >= 7.158 and < 7.162       | Project structure change with respect to code organization |
| [1.4.0]     | >= 7.156 and < 7.158       | Added support for comment author impersonation |
| [1.3.0]     | >= 7.153 and < 7.156       | Added support for next page–based pagination |
| [1.2.0]     | >= 7.147                   | Added support for non–timestamp-based poller and Entity-Mention synchronization |
| [1.1.0]     | >= 7.140 and < 7.147       | Added support for delete sync |
| [1.0.0]     | >= 7.129 and < 7.140       | Initial version. <br> OIM supports SDK connector registration from 7.129 onwards. |


# Some Useful SDK Pages
- **[APIs Required for Each Feature](apis-required-for-each-feature.md)**
- **[SDK Best Practices](sdk-best-practices.md)**
