## Description

{{SITENAME}} stores end system's credentials. How does it secure end system's data? What are the various security measures followed in {{SITENAME}} to ensure the data used and accessed using {{SITENAME}} is secure?

## Solution

### Data Access

Customer data privacy and protection is the top-most priority at OpsHub. To ensure the same, {{SITENAME}} follows the measures given below.

* {{SITENAME}} doesn't connect to any system outside company's firewall unless explicitly requested by the customer to do so.
* {{SITENAME}} doesn't access any system within company firewall unless explicitly requested by the customer to do so.
* {{SITENAME}} doesn't directly receive any sensitive information from {{SITENAME}} itself post installation unless shared by customer.
* Access to {{SITENAME}} is completely under the control of customer and cannot be accessed by OpsHub or any third party directly unless customer shares access credentials using web meeting.
* All logs, configuration details, and sync details are stored in customer specified physical location and cannot be accessed by {{SITENAME}}, unless shared by customer.

### Data Security

* Users must authenticate themselves with a user name and password to gain access to {{SITENAME}}.
* All {{SITENAME}} users' passwords are stored with one-way hash with a salt so decrypting {{SITENAME}} passwords is not possible.
* {{SITENAME}} stores sensitive data such as system's passwords, API token, database password in an encrypted format so that only {{SITENAME}} can access it and others can't access it. {{#ifeq: {{SITENAME}} | OpsHub Migrator for Microsoft Azure DevOps ||The default encryption algorithm is AES-256. Encryption algorithm selection option is visible in advance configuration of installation. For more information on how to select encryption algorithm and what other encryption algorithm options are available, please refer [Data Encryption Configuration](../../../getting-started/installation.md#data-encryption-configuration)
.}} 

{{#ifeq: {{SITENAME}} | OpsHub Migrator for Microsoft Azure DevOps ||### HTTPS deployment

{{SITENAME}} supports https deployment. This option is available during installation. For more information please refer [Advance Installation](../../../getting-started/installation.md#advance-installation).

* HTTPS is a way to encrypt information exchanged between a browser and a web server. This protects 'man-in-the-middle' attacks, where someone steals the information being sent to a web server.
* {{SITENAME}} supports TLS 1.3 protocol.}}

### Third Party Services/Libraries

{{SITENAME}} doesn't outsource any part of the software development or services to any third-party organization. However, we do use some third-party libraries & jars that come bundled with product and don't require additional license or installation. For seeking further information on third party jars, please reach out to account management team or your sales point of contact.

### Application Security

Ensuring comprehensive security for {{SITENAME}} is important to us. We take multi-layer approach to ensuring proper security implementation in {{SITENAME}}. 
    
* {{SITENAME}} conducts application vulnerability testing with every release using an industry-leading web application vulnerability testing provider to ensure that {{SITENAME}} application and network environment is secured from outside attack.
* Next layer we use is based on OWASP project (https://www.owasp.org/index.php/Main_Page) to ensure {{SITENAME}} meets all OWASP security guidelines. 

Scans are carried regularly, and it is ensured that no high/critical/Medium vulnerability exists in product.

### Code Security Audits

{{SITENAME}} conducts security audit of code base as a part of every release. We analyze the entire code base for any high/critical vulnerabilities and in rare situations, if any high/critical vulnerabilities are found, it is fixed. Security audit tool extensively covers OWASP Top 10 and CWE guidelines.
