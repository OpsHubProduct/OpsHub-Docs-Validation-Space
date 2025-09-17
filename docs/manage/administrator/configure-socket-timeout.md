- Socket Timeout is the amount of time for which OpsHub Integration Manager will wait for an API response after making an API request.
- Sometimes, the end systems do not respond within the predefined time period, which cause **SocketTimeoutException** failure in the sync. In such cases, it is recommended to update the socket timeout parameter in OpsHub Integration Manager.
  - OpsHub Integration Manager is by default deployed with socket timeout set to 30 minutes. However, if the above mentioned failure is observed in the sync, to change the value of the socket timeout parameter, refer to the section below.

# How to Configure Socket Timeout

1. From services.ms, stop the 'OpsHub Server Service'.
2. Open the command prompt with administrator privileges.
   1. Navigate to "`<OpsHub Integration Manager Installation Path>`/OpsHubServer/bin" directory.
   2. Run **unregisterservice.bat**, to remove the 'OpsHub Server Service'.
3. If user wants to configure the socket timeout for **OpsHubTFSService**:  
   1. From Windows Explorer, go to "`<OpsHub Integration Manager Installation Path>`/OpsHub_Resources/config" and open **TFSProperty.properties.sample** file using any text editor. In this file, there will be default socket timeout settings for the **OpsHubTFSService** as **serviceRequestTimeOutInMinutes=1440**.
   2. The format for socket timeout parameter is **serviceRequestTimeOutInMinutes=**`<Timeout in minutes>`.
   3. Update **TFSProperty.properties.sample** file based on the required parameters and click **Save**.
4. If user wants to configure the socket timeout for any supported systems of OpsHub [except OpsHubTFSService]:
   1. From Windows Explorer, go to "`<OpsHub Integration Manager Installation Path>`/AppData/OpsHubData" directory and open **OIM_Config.properties** file using any text editor. In this file, there will be default socket timeout settings for the server as **http.socket.timeout=1800000**.
   2. The format for socket timeout parameter is, **http.socket.timeout=**`<Timeout in milliseconds>`.
   3. Update **OIM_Config.properties** file based on the required parameters and click **Save**.
5. Switch back to the previously opened command prompt in step #3. If it is closed, you can reopen it with administrator privileges and navigate to "`<OpsHub Integration Manager Installation Path>`/OpsHubServer/bin" directory.
   1. Run **registerservice.bat**, to  register the 'OpsHub Server Service'.
6. From services.ms, start the 'Opshub Server Service'.


