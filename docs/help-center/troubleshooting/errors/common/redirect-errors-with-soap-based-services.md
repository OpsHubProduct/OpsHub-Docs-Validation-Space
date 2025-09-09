## Description

* Redirect request error code **301/302/303/307/308** can occur for the connectors using **SOAP based API**.  
* The below mentioned is an example of such error in Windchill RV&S.  
  * Error message: (302) OH-Windchill-0001: Exception while creating entity. Error : return code:  302

## Cause

* Apache Axis CommonsHTTPSender (which is used to connect the Soap Server) does not handle automatic redirection of POST requests. Hence, it throws the error.

## Solution

* To allow POST requests with redirects, user needs to change the default HTTP handler with custom HTTP handler (based on Apache Axis HTTPSender). The below mentioned steps can be performed to achieve redirects:  
* Open the file `<OIM Installed Directory>\OpsHubServer\conf\client-config.wsdd` with any text editor.  
* Replace the line  
  `<transport name="http" pivot="java:org.apache.axis.transport.http.CommonsHTTPSender">`  
  with  
  `<transport name="http" pivot="java:com.opshub.axis.transporthandler.HttpRedirectHandler">`

> **Note**: User should use this solution with caution, as it allows **redirects with POST requests**.
