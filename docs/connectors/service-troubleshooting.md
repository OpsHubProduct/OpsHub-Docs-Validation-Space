# Problem

Page loading error when opening URL: `http://<proxyhost>:9090/TFSService` in browser.

# Resolution

* Open run in machine (You can open it by pressing Windows + R button)
* Type **services.msc** and click ok.
* Find service name **OpsHubTFSService** and check the status of service. If service status is not *running* then click on start.
* Test the proxy by opening service URL `http://<proxyhost>:9090/TFSService` in browser.

# registerTFSWCFService.bat fails to install

## Problem

While installing the Service through the bat file, the installation fails with the following error:

* _An exception occurred while trying to find the installers in the C:\Program Files\OpshubPath\opshubtfsservice.exe assembly._
* _System.Reflection.ReflectionTypeLoadException: Unable to load one or more of the requested types. Retrieve the LoaderExceptions property for more information._
* _The Rollback phase of the installation is beginning_

And the service registration is roll backed.

## Resolution

This error usually occurs when you have *TFS Object Model 2013* installed on the machine unless you have **Team Foundation Server 2012** or **Visual Studio 2012** installed on the same machine.

It is strongly recommended that you install *TFS Object Model 2012* and uninstall all other object model installed in machine.

*TFS Object Model 2012* [download link](https://marketplace.visualstudio.com/items?itemName=ErinDormierMSFT.TeamFoundationServer2012Update4ObjectModelInstalle)

# I have TFS Object Model 2013 already installed

## Problem

This is the situation where you have *TFS Object Model 2013* already installed on the machine where you want to setup the service and while trying to install the *TFS Object Model 2012*, the installer stops because it detects a newer version of the Object Model already installed.

## Resolution

To resolve this issue, it is suggested that you uninstall the *TFS Object Model 2013* and then install the *TFS Object Model 2012* (as required by {{SITENAME}} Proxy Service)

Service will **NOT** work with TFS Object Model 2013.

## Problem

Error such as "Error coming was HRESULT E_FAIL has been returned from a call to a COM component".

## Resolution

Perform following steps to resolve the issue.

1. Exit Team Foundation Server. Stop OpsHubTFSService from the local service.
2. Open the command window and navigate to the folder: `%localappdata%\Microsoft\Team Foundation\X.0\Cache`. Here delete all sub-items in cache folder and empty it. Do this for all folders X.0 where X is version number i.e. 3.0, 4.0, etc.

