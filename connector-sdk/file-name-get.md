
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