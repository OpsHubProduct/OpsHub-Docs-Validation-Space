This utility regenerates Secret Key for application. This can be used in following cases:
* Secret Key is lost.
* Secret Key has been tampered.
* User wants to change secret key for application.

Please follow below given steps for execution of this utility:

* Stop OpsHub Server/ Service before execution of this utility.
* Go to `<OpsHub Installation Folder>/Other_Resources/Resources`.
* Unzip `OpsHub Secret key reset utility.zip`.
* Execute `OpsHubSecretKeyResetUtility.bat` / `OpsHubSecretKeyResetUtility.sh` for Windows/Linux respectively.
* Enter path for OpsHub Installation Directory.

<p align="center">
  <img src="../../assets/Regenerate_Image_1.png" width="1200">
</p>


* Enter new location for security. (`opshub.key` should not be available on the same location).

<p align="center">
  <img src="../../assets/Regenerate_Image_2.png" width="1200">
</p>

* Select Data Encryption algorithm. By default, AES (128) is selected.

<p align="center">
  <img src="../../assets/Regenerate_Image_3.png" width="1200">
</p>


* Provide password for database. 

<p align="center">
  <img src="../../assets/Regenerate_Image_4.png" width="1200">
</p>

* This would generate new key at specified location.

<p align="center">
  <img src="../../assets/Regenerate_Image_5.png" width="1200">
</p>


* In case of HTTPS deployment of **<code class="expression">space.vars.SITENAME</code>**, run [Change Keystore and Private Key passwords utility](change-keystore-and-private-key-passwords.md) to store the passwords in encrypted form.

* Start OpsHub Server/ Service.  
* Re-enter passwords for all configured systems, configured database connections, configured proxy settings and overridden passwords in Advance Configuration of Integration.


