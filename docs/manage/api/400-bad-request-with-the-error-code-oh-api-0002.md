# Description
**400 Bad Request** with the Error code: **OH-API-0002** can be received with the error messages given below: 

# Invalid Syntax  
* Validation error of type FieldUndefined: Field `<fieldName>` is undefined.  
* Validation error of type WrongType: argument value `<Type>Value{value=<value>}` has wrong type.

# Cause
The reason behind this error is invalid API request because of:  
* Invalid encoding in the Request URL or Request body.  
* Invalid field passed in the Request URL or Request body.  
* Invalid type of value passed in the Request body.

# Solution
Please provide the correct API request based on the formats explained in the [Forming calls with the <code class="expression">space.vars.SITENAME</code> API](forming-calls-with-api.md).
