## Description

[Registration](../../../../getting-started/installtion.md#registration) is one of the steps in installation. At the time of registration, user is required to provide the verification code which was sent to his/her business email address. This error may be encountered during the validation of verification code. 

## Solution

Verification Code is unique for each machine and installation path. The code generated for one machine or path won't work for a different machine or path.  
For e.x, during registration process of installation, the verification code is generated for System A and later the same verification code is used on System B for validation. In this case {{SITENAME}} will throw an error: "Please provide the correct verification code".  

This error will also occur if for the same machine the verification code is generated for some installation path (`folder A\folder B`) and later used for installing {{SITENAME}} at another path (`folder C\folder D`).  

So make sure that the verification code is generated for the same machine and path where {{SITENAME}} is to be installed.
