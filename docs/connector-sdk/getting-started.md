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
- Refer to **[Build Your Own Connector](sdk-connector-apis.md)** page for the list of APIs to implement a connector.

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
| [1.17.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/EkEI6J-uYJFKv7_ePKrgqlEB9J9-oPTIo7D6r73Y2WG2oA?e=lROoA9)    | >= 7.198                   | Added support for bulk linking and link ordering |
| [1.16.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/EvOnIixsygdIjhvfCa7vWS0BVG2vyovUYG4lzaRL1bN2UA?e=kIBnIn)    | >= 7.197 and < 7.198       | Added support for systemId to store system-specific cache and `cleanupGlobalCache` flag to control cache cleanup. <br> Added support for adding multiple inline URL prefixes. |
| [1.15.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/EvvyUofLAjxHk-N5W0YnH_sBD6JEYO2grFg9FjWcycR0qg?e=a3RdTs)    | >= 7.189 and < 7.197       | Added support for Rank synchronization |
| [1.14.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/EpAJjYhkvjlMqInjTb8nnzsBvaBfdz935gW6Bbk-6snAkQ?e=AUW9cC)    | >= 7.188 and < 7.189       | Added support for attachment file comment |
| [1.13.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/EhjGCtTDvpZBnqQ5Q1o-0DwBIhd_SH4YQyPgv6_g_NRKLg?e=QRWLbV)    | >= 7.184 and < 7.188       | Added support for forming Remote Link using different base URL |
| [1.12.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/Eifg-bj_zBZJu0bDMeSeEmwBOzQGivZn7uSiMnlkgT4-MQ?e=r8KcUC)    | >= 7.182 and < 7.184       | Added support for 'fetch mapped data only' feature |
| [1.11.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/Elb-oBAzBfZFlQlx0vyP3pQBe3vJkKSxzPg3mm-kSu5CGQ?e=yl98Sy)    | >= 7.179 and < 7.182       | Added support for entity type and project movement. <br> Added provision for filtering comments after specified time. |
| [1.10.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/EviqliwYNMhFssMKncO0cfgBiHnM0VmWCKMigMttta5xxw?e=fuysA4)    | >= 7.177 and < 7.179       | Optimized Entity-List API |
| [1.9.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/Ev8AGbZNxfNCp-fFrXE1sdYB66pZBJ8si3kZ2fdfpkNoNg?e=km0rN0)     | >= 7.174 and < 7.177       | Added support for UserMention and EntityMention for Markdown datatype, and introduced support for `subStepNumber` in `updateEntity`. |
| [1.8.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/EkZXYx2GibtIifkfi-1UXqYBVUSTNPIlhqKKZGDqBbT6gA)     | >= 7.168 and < 7.174       | Added support for dynamic retrieval of lookup fields in integration advanced setting screens |
| [1.7.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/EtK34ZC39XVLjP9qGJXZXaYBmEKYi86_tgc011M-vSjfQA?e=a9PlEw)     | >= 7.165 and < 7.168       | Added support for searching Entity Mention and User Mention in fields or comments of HTML type using regex |
| [1.6.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/EjkO9ZHLFu1MifQbGzQ_gckBZbGKXIHWVQi_HBwIP64Rgg?e=k7zk6F)     | >= 7.162 and < 7.165       | Added support for reference fields and upgraded Spring Boot version to 3.2.3 |
| [1.5.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/ErdGKjtXHFJLmbQepsO9JoMB5_mYwWDexyqnsuYj8tD6YA?e=h0LjHw)     | >= 7.158 and < 7.162       | Project structure change with respect to code organization |
| [1.4.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/ErlFZKgz_HlGl3yyeN1w3HEBjoX0X0nxV0ge6Mvl5nQGyw?e=G39xkC)     | >= 7.156 and < 7.158       | Added support for comment author impersonation |
| [1.3.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/Ej_3PQP_CrNHqZkXSGlOLXsBIke4XoXhp0T6e5vFfZT38g?e=WedC61)     | >= 7.153 and < 7.156       | Added support for next page–based pagination |
| [1.2.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/Eub-SAMZhS9Brl_sppkIlN4BsNmN-zh1Ligf7q5s1yUucQ?e=ZlzvBf)     | >= 7.147                   | Added support for non–timestamp-based poller and Entity-Mention synchronization |
| [1.1.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/EpQXywvHUFtMqzUgo-9v4R4Bxrz0G9xk90q0Y3QwIvN7fA?e=aaoX9M)     | >= 7.140 and < 7.147       | Added support for delete sync |
| [1.0.0](https://opshubtrial-my.sharepoint.com/:f:/g/personal/support_opshub_com/EvJdBwrcg49MmUBujzlJsN8BTQfy-ZwVjwQz-S0vP8PvcQ?e=7dg12z)     | >= 7.129 and < 7.140       | Initial version. <br> OIM supports SDK connector registration from 7.129 onwards. |


# Some Useful SDK Pages
- **[APIs Required for Each Feature](apis-required-for-each-feature.md)**
- **[SDK Best Practices](sdk-best-practices.md)**

