# Overview

OpsHub Integration Manager has rich user interface for achieving the integration configurations and using other functionality of OpsHub Integration Manager. However, there can be various cases where the user might need to achieve/use them programmatically, i.e., with the external script, external software program, or with some API client, and OpsHub Integration Manager API is useful in such cases. It is an alternate way to communicate with the OpsHub Integration Manager.

The OpsHub Integration Manager API is organized around REST and uses [JSON](https://www.json.org/json-en.html) format for data exchange.

To have a quick look on the use cases samples and OpsHub Integration Manager API usage examples, please refer to [Use Cases](sample-use-cases.md).

# Prerequisites

Following are the prerequisites to use OpsHub Integration Manager API:

## Access to OpsHub Integration Manager Instance

- An active instance of OpsHub Integration Manager which needs to be accessible from the machine/[platform](#platforms) for invoking the OpsHub Integration Manager API.
- URL of OpsHub Integration Manager instance. Example: `http://10.13.20.20:8989/OIM/` or `https://10.13.20.20:8443/OIM/`.
- User credentials for accessing the OpsHub Integration Manager instance.  
  ![Note](assets/Note.jpg) Please refer to [Validate access](#validate-access-to-opshub-integration-manager-instance) for validating this prerequisite.

## API License

- Usage of OpsHub Integration Manager API requires "API" add-on in the OpsHub Integration Manager license.  
  ![Note](assets/Note.jpg) Please refer to [Validate API feature](#validate-api-feature) to determine whether the "API" feature is enabled or not on your OpsHub Integration Manager instance.

## Platforms

- OpsHub Integration Manager APIs can be invoked from the platform which can make the REST API Calls.
  - API client such as [postman](https://www.postman.com/).
  - Programs written in any programing language which has support for HTTP or HTTPS communication.
  - Command line tool such as [curl](https://curl.se/).

# Access to API

Access to API will be available for your instance with URL like below:

<center><code>&lt;Protocol&gt;://&lt;Host Name or IP address of OpsHub Integration Manager instance&gt;:&lt;Port Number&gt;/OIM/rest/api/docs</code></center>

**For example** – If the application url of OpsHub Integration Manager is `http://10.13.20.20:8989/OIM/`, then the Swagger UI will be available at `http://10.13.20.20:8989/OIM/rest/api/docs`.

# Appendix

## Validate API feature

To check whether the "API" feature is enabled in the OpsHub Integration Manager or not, please perform the below steps:

1. [Login](Logging_In) to OpsHub Integration Manager with the valid OpsHub Integration Manager user credentials.
2. Navigate to the Footer and find "Edition" value.
3. Click on the Edition value of the OpsHub Integration Manager  
   ![Edition](assets/API1.png)
4. Please make sure the "API" feature is enabled.  
   ![API Feature](assets/API2.png)  
   ![Note](assets/Note.jpg) If this feature is disabled, and you have the license in which this feature is available, then please [install](Managing_Licenses) the correct license. If you don’t have a valid license, please reach out to OpsHub Sales/Support team for receiving the appropriate license.

## Validate access to OpsHub Integration Manager instance

To check whether the OpsHub Integration Manager instance is accessible or not, please perform the below steps:

1. Open OpsHub Integration Manager instance URL from any browser from the machine/platform where OpsHub Integration Manager APIs are invoked.
2. Access the OpsHub Integration Manager instance from browser using the credentials you want to use for OpsHub Integration Manager API communication.
3. If you can successfully login, this prerequisite is met.  
   ![Note](assets/Note.jpg) If OpsHub Integration Manager is configured on HTTPS, then SSL certificates needs to be imported based on the chosen platform:
   - For the API clients like [postman](https://www.postman.com/), there are some [steps](https://learning.postman.com/docs/sending-requests/certificates/) to configure it.
   - For the [curl](https://curl.se/) command, this can be [configured using -cert](https://curl.se/docs/manpage.html) option.
   - For the programs, the steps will differ based on the expectation of the programming languages in which it was written.

# Known Limitations

1. SAML Users won't be able to login through the API.
   - Let's say the user has configured SAML login for OIM UI Login. Such users won't be able to login through the API. It would need either Default or LDAP user.
