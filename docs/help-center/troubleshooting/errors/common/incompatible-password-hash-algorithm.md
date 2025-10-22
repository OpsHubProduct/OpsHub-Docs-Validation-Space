## Description

This issue occurs when an application or connector requires the use of the MD5 hashing algorithm for password handling, but the operating system has **FIPS (Federal Information Processing Standards)** enforcement enabled.

Since FIPS restricts the use of certain cryptographic algorithms such as MD5, the system blocks the application from converting plain text passwords into MD5 hashes. As a result, authentication or connection attempts that rely on MD5 hashing fail.

## Cause
* This issue occurs when the machine where <code class="expression">space.vars.SITENAME</code> or the end system is running has **FIPS (Federal Information Processing Standards)** enabled in the Local Security Policy.
* FIPS prevents applications from using certain cryptographic algorithms such as MD5.
* If the program (e.g., a connector instance or service) attempts to convert plain text into an MD5 hash, FIPS enforcement blocks this operation, resulting in the error.

## Solution
You can resolve this issue in one of the following ways:

1. **Disable FIPS** from the Local Security Policy on the machine where <code class="expression">space.vars.SITENAME</code> or the end system is running.  
2. **Provide the password in an already MD5-encrypted format**.  
   > For example, some connectors (such as Aras) accept passwords in MD5 hash form. If you provide the password as plain text, the connector tries to convert it to MD5 internally, which fails due to FIPS restrictions. Supplying the password already encrypted in MD5 bypasses this issue.
