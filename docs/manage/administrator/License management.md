# Overview

This section covers how to install new licenses, renew licenses and uninstall licenses.

The License Management option will be shown under the Administration drop-down.  

![License Management Dropdown](../../assets/License_Management_Image_5.png)

The License Management section contains your license details and information such as what kind of license you have, how many days are left for your license to expire, etc.

For detail about how to get a license issued, please refer the section [How to Procure and Renew Licenses](#how-to-procure-and-renew-licenses) in appendix.

# Install License

* Navigate to the Administration section and select **License Management** from the drop-down options.  

![License Upload Start](../../assets/License_Management_Image_2F1.png)

* Click the **Upload License** link. It will open install license window.  

![Upload License](../../assets/License_Management_Image_3C.png)

* You can drag & drop the license on **Drop license file here** box or upload the license file using the **Choose File** button.  
* License updates will get populated in the form on the right.  
* Click **Install License** button to install the license. If you want to reset this change, click the **Reset** button.  

After installing, refresh the browser.  

**Note** : You can check the status of license and even delete the license from this window.

# View License

* Navigate to the Administration section and select **License Management** from the drop-down options.  
* You will see the **Licenses** screen.  
* Click the eye icon against the License name for which you want to view the details.  

![View License](../../assets/License_Management_Image_4C.png)

A pop-up with **License Details** will open.  

<p align="center">
  <img src="../../assets/License_Management_Image_6C.png" alt="License Details Popup" style="width:600px;" />
</p>

**Note** See the Version [Example: QAOIMV6.16-U4B002] and Build [Example: QA2018Q1PH19_6_16_004_B002] details in the footer.

# License Expiry Notification

* **OpsHub Integration Manager UI Notifications**
  * On OpsHub Integration Manager, upon login, upcoming license expiry warning notifications will be shown for each license starting 60 days till its expiry date.
  **Note** : No additional configuration is required to enable the same.

* **Mail Notifications**
  * To get mail notifications regarding each upcoming license expiry, the SMTP mail server notifications can be configured
  * Refer to [Creating SMTP System](../help-center/troubleshooting/configure-failure-notification.md#smtp-configuration) for creating an SMTP system.
  * SMTP Mail Client system must be created in OpsHub Integration Manager and configured in **OpsHub System** under **SMTP System For Notification**.
   ![SMTP Config](../../assets/OpsHubSystemSMTP.png)
  * Mails will be sent out to the **to** and **cc** configured in SMTP system.
  * It will notify the configured SMTP system regarding upcoming expiry at intermittent intervals starting from 60 days before its expiry date. It will send out mail notifications on 60, 45, 30, 15, and from 10 days until 1 day before the expiry of any license.
  * If for any reason (such as the SMTP mail server is not connected or SMTP system configuration is not valid or OpsHub Integration Manager is down) license expiry notification doesn't come, it will be logged in OpsHub Integration Manager logs.

# Uninstall License

* Navigate to the Administration section and select **License Management** from the drop-down options.  
* You will see the **Licenses** screen.  
* Click the cross icon against the License name which you want to delete.  

![Uninstall License](../../assets/License_Management_Image_7C.png)

After uninstalling, refresh the browser.  

**Note** You will not be able to see the details for a trial license and you will not be able to uninstall it.

## How to Procure and Renew Licenses

For procuring a license, you have to contact our [Sales](mailto:sales@opshub.com) / [Support](mailto:ps@opshub.com) representatives.
* Name  
* Email  
* Phone  
* Organization name  
* Country  
* MAC Address  

If you want to renew your license, send your current license number and your requirement to our sales/support representatives.

OpsHub Integration Manager works best with the following browsers: Google Chrome, Mozilla Firefox, and Safari.
