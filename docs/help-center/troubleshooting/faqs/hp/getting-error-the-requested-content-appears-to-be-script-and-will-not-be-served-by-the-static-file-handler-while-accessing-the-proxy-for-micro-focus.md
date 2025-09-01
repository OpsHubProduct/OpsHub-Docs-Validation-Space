## Description

While accessing the proxy that is configured by performing the steps mentioned for [Proxy Configuration](../../../connectors/micro-focus-alm-qc.md#proxy-configuration-steps) in the product documentation for Micro Focus QC/ALM, the user receives an error **The requested content appears to be script and will not be served by the static file handler**.

## Cause

Probable cause behind this error could be:  
a) ASP.NET is not configured properly on the machine on which the user is configuring a proxy or  
b) the application pool added with the website is not able to deploy the proxy.

## Solution

* To solve this error, you need to make sure that the machine on which you are configuring the proxy satisfies the pre-requisites for [proxy configuration](../../../connectors/micro-focus-alm-qc.md#proxy-configuration).  
* However, if all the prerequisites are satisfied and you are still getting this error, then the application pool added with the website in the Internet Information Server Manager (IIS) is not able to deploy the proxy. In this case, you shall change the application pool for that added website to **.NET v4.5 Classic** (It is the default application pool based on the configured ASP.NET with IIS) with the changes mentioned in the product documentation for an application pool.  
* Please refer [Proxy Configuration](../../../connectors/micro-focus-alm-qc.md#proxy-configuration-steps) to change the application pool for the added website.

