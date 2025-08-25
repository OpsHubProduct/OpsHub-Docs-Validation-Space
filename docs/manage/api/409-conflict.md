# Description
When you receive **409** status code with the description **Conflict**, Error code: **OH-API-0200**, and the Error Message:  
The `<object>` you are trying to update has been modified by some other user. Kindly refresh the page to get the latest changes and try to update again.

# Cause
The reason behind this error is the conflicting modifications on the same objects, i.e., simultaneous updates are done on the same persistence state of the object version.

# Solution
Please get the latest state of the object using [queries](forming-calls-with-api.md#queries-read) and then update the object.
