# Description

{{SITENAME}} has been installed with HTTP. However, even after installation with a few steps, the user can enable it to connect with HTTPS. 

# Solution

Follow the steps given below to enable HTTPS on {{SITENAME}} which has already been installed with HTTP:

1. Take a backup of the OpsHub Installation Folder; so that in case of any problem the user can restore it.  
2. Stop the OpsHub Server.  
3. Also, take the backup of bundled JRE within OpsHub installation. JRE location is:  
`<OpsHub Installation Directory>\OpsHub_Resources\jre`
4. Below are the steps/commands that help the user to create a CSR (which can be provided to CA to get the valid certificate) and will import the certificates (provided by CA).  

* Following are the commands that need to be executed in the given sequence within the Command Prompt on the machine where {{SITENAME}} has been installed:  
* Open the command prompt with the administrative privileges and go to the bin directory path of the OpsHub’s JRE:  
  ```
  cd <OpsHub Installation Directory>\OpsHub_Resources\jre\bin
  ```

**Command 1:**  
``` 
cd keytool -genkey -keyalg RSA -alias opshub.com -keysize 2048 -keystore <OpsHub Installation Directory>\AppData\OpsHubData\cacerts
 ```
**Note:**  
* The alias provided in the above command should be used for Command 2 as well as while importing the certificate, so please take a note of the alias name used.  
* Upon successful execution, it will prompt the user to enter the keystore password for `AppData\OpsHubData\cacerts`. The default password for the keystore is `changeit`.  
* After entering the password, the user is prompted to enter various certificate details. For the **first name and last name**, the user must provide the **hostname of the machine** where {{SITENAME}} is installed. Otherwise, the signed certificate will not be visible even after successful import.  

**Command 2:**  
``` cd keytool -certreq -keyalg RSA -alias opshub.com -file <path of new CSR file> -keystore <OpsHub Installation Path>\AppData\OpsHubData\cacerts```

After execution, share the CSR file with your CA (Certificate Authority) to generate the certificate file (`.cer`). For example, the certificate file generated could be `opshub.cer`. Once the certificate is generated, proceed with Command 3.  

**Command 3:** Import the certificate file into the keystore.  

* If certificates include Root or Chain Certificates, first import the Root Certificate, then the Chain Certificate(s), and finally the actual certificate.  
* If no Root certificate is present, import only the certificate file.  

Command to import the root certificate:  
```cd keytool -importcert -alias root -keystore <OpsHub Installation Path>\AppData\OpsHubData\cacerts -trustcacerts -file <root CER file path>```

Command to import your certificate:  
``` cd keytool -import -alias opshub.com -keystore <OpsHub Installation Path>\AppData\OpsHubData\cacerts -file <Path of your CER file>```


**Notes:**  
* If your certificate chain is `root → chain cert1 → opshub.cer`, then import `chain cert1` with a different alias.  
* For the main certificate (`opshub.cer` in this case), the alias must be the same as used in Command 1 and Command 2 (`opshub.com`).  

5. To access {{SITENAME}} with HTTPS, please refer to the [Configurations for HTTPS](#configurations-for-https) section.  
6. Save the `server.xml` file.  
7. Start the OpsHub Server.  
8. Access {{SITENAME}} with the URL:  
`https://[hostname]:8443/OpsHubWS/`

**Note:** All the above steps should be executed by a user having administrator rights.

# Configurations for HTTPS

Go to:  `<OpsHub Installation Directory>\OpsHubServer\conf`

Open `server.xml` in any text editor.

* Search for `<Connector port="8989" ...>` and **comment out that connector tag**. Example:  

```xml
<!--
<Connector port="8989" protocol="HTTP/1.1" maxHttpHeaderSize="65536"
           connectionTimeout="20000"
           redirectPort="8443"
           server="OpsHub Server"
           maxParameterCount="1000"
/>
-->
```
* Now, paste the below code in server.xml:
```xml
<Connector port="8443" protocol="com.opshub.security.resources.OpsHubHttp11Nio2Protocol" 
           maxHttpHeaderSize="65536" SSLEnabled="true"
           maxThreads="150" scheme="https" secure="true" 
           server="OpsHub Server" maxParameterCount="1000">
    <SSLHostConfig sslProtocol="TLS" protocols="TLSv1.2,TLSv1.3" certificateVerification="false"
                   ciphers="TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256,
                            TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256,
                            TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384">
        <Certificate certificateKeyAlias="@AliasName@" 
                     certificateKeystoreFile="<OpsHub Installation folder>\AppData\OpsHubData\cacerts"
                     certificateKeyPassword="@KeyPassword@" 
                     certificateKeystorePassword="@KeyStorePassword@" />
    </SSLHostConfig>
</Connector>
```
* **Here is a breakdown of the elements used in the `<Connector>` tag that must be updated by the user:**
  * Run [Change Keystore and Private Key passwords](../../../manage/advanced-utilities/change-keystore-and-private-key-passwords.md) to update `certificateKeystorePassword` and `certificateKeyPassword` passwords in encrypted format.
  * Provide Alias Name at `@AliasName@` given in step 4 in the 'Solution' section above.
  * Substitute OpsHub Installation Path in `<OpsHub Installation folder>` to access Certificate Key Store File.

* **Below are the static parameters in the `<Connector>` tag:**
  * `port="8443"`: Specifies the port number to listen for incoming secure (SSL/TLS) connections, typically port `8443` for HTTPS traffic.
  * `protocol`: Specifies the protocol implementation used for handling HTTP connections.
  * `maxHttpHeaderSize="65536"`: The maximum size (in bytes) for HTTP request headers.
  * `SSLEnabled="true"`: Enables SSL (Secure Sockets Layer) encryption for the connector, making the connection secure (HTTPS).
  * `maxThreads="150"`: Sets the maximum number of threads that the connector can use to handle requests concurrently.
  * `scheme="https"`: Specifies the scheme used for the connector, which in this case is `https`, indicating a secure connection.
  * `secure="true"`: Indicates that the connection is secure, meaning SSL/TLS is enabled.
  * `server="OpsHub Server"`: Specifies the server name for identifying the OpsHub server instance in the HTTP response headers.
  * `maxParameterCount="1000"`: Sets the maximum number of parameters that can be processed in a single HTTP request.
  * `sslProtocol="TLS"`: Specifies the SSL protocol used for secure communication, in this case, `TLS` (Transport Layer Security), which is the modern replacement for SSL.
  * `protocols="TLSv1.2,TLSv1.3"`: Specifies the allowed versions of TLS, here it allows both `TLS 1.2` and `TLS 1.3`.
  * `certificateVerification="false"`: Disables certificate verification (typically used in a development environment or for self-signed certificates).
  * `ciphers="TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256,TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256,TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384"`: Specifies the cipher suites to use for secure communication. These define the encryption algorithms for the connection.





