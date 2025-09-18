# API Name  
File Name – Get  

## Overview  
Extracts and returns file name from source URL or 'alt' attribute of img or href tag:  

* This API can be called for two types of tags which can have inline file:  
  * `<a>` Anchor tag: For inline documents  
    * `fileSourceUrl` will be the value of 'href' attribute of anchor tag  
    * `imageAltAttribute` will be empty  
  * `<img>` Image tag: For inline images  
    * `fileSourceUrl` will be the value of 'src' attribute of img tag  
    * `imageAltAttribute` will be the value of 'alt' attribute of img tag  

* The file source URL can have the entire URL of the image or document. For example, it includes protocol, domain, path, path param, query param, etc. From this URL, get the image or document file name (either from the path or query param, depending on the system). Return the extracted file name.  

* In case of an inline image, if the file name could not be found in the URL, then image alt attribute can be used.  

## API URI  

```bash
GET: /entities/{entityTypeId}/attachments/decoded-inline-file-name?fileSourceUrl=<fileSourceUrl>&imageAltAttribute=<imageAltAttribute>
```

## URI Parameters
| **Name**         | **In** | **Required** | **Type** | **Description** |
|------------------|--------|--------------|----------|-----------------|
| entityTypeId     | path   | True         | String   | `id` of the entity type |
| fileSourceUrl    | query  | True         | String   | **For `<a>` Anchor tag** (inline documents):<br> - `fileSourceUrl` = value of `href` attribute<br> - `imageAltAttribute` = empty<br> **For `<img>` Image tag** (inline images):<br> - `fileSourceUrl` = value of `src` attribute<br> - `imageAltAttribute` = value of `alt` attribute |
| imageAltAttribute| query  | True         | String   | **For `<a>` Anchor tag** (inline documents):<br> - `fileSourceUrl` = value of `href` attribute<br> - `imageAltAttribute` = empty<br> **For `<img>` Image tag** (inline images):<br> - `fileSourceUrl` = value of `src` attribute<br> - `imageAltAttribute` = value of `alt` attribute |

## Request Payload
Only **String**: Extracted file name from `fileSourceUrl` or `imageAltAttribute`  

**Example**:  

"Example decoded file name.txt"
