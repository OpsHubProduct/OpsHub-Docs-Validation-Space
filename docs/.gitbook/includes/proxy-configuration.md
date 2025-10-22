# proxy-configuration

{% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}    
To start the <code class="expression">space.vars.SITENAME</code> installer on a machine that is behind a proxy, please perform the following steps:
{% endif %}

{% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}  
1.
{% endif %}

{% if "OpsHub Integration Manager" === space.vars.SITENAME %}  
6.
{% endif %}

Open environment configuration from My Computer -> Properties -> Advanced System Settings -> Environment Variables

<div align="center"><img src="../assets/Proxy%201.png" alt="" width="600"></div>

<div align="center"><img src="../assets/Proxy2.png" alt="" width="600"></div>

<div align="center"><img src="../assets/Proxy3.png" alt="" width="600"></div>

{% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}  
2.
{% endif %}

{% if "OpsHub Integration Manager" === space.vars.SITENAME %}  
7.
{% endif %}

Create a new environment variable with the name **"\_JAVA\_OPTIONS"**.

<div align="center"><img src="../assets/Proxy4.png" alt="" width="600"></div>

{% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}  
3.
{% endif %}

{% if "OpsHub Integration Manager" === space.vars.SITENAME %}  
8.
{% endif %}

Set the variable's value as per the format ->\
`-Dhttp.proxyHost= -Dhttp.proxyPort= -Dhttp.nonProxyHosts="localhost|127.0.0.1" -Dhttp.proxyUser= -Dhttp.proxyPassword= -Dhttps=`

| **Attribute**          | **Description**                                                                                                                                                                            |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `-Dhttp.proxyHost`     | Proxy server host address                                                                                                                                                                  |
| `-Dhttp.proxyPort`     | Proxy server host port number                                                                                                                                                              |
| `-Dhttp.nonProxyHosts` | Hosts accessible without proxy server                                                                                                                                                      |
| `-Dhttp.proxyUser`     | User name to access proxy server                                                                                                                                                           |
| `-Dhttp.proxyPassword` | Password for the provided username to access proxy server                                                                                                                                  |
| `-Dhttps`              | <p>If proxy server is hosted over HTTPS, then set this parameter as <code>"true"</code> else <code>"false"</code>.<br>This attribute is not mandatory. Default is <code>"false"</code></p> |

**For example:**\
`-Dhttp.proxyHost='00.00.00.00' -Dhttp.proxyPort='8080' -Dhttp.nonProxyHosts="localhost|127.0.0.1" -Dhttp.proxyUser='username' -Dhttp.proxyPassword='password' -Dhttps=false`

In the above example:\
ProxyIP → `00.00.00.00`, Proxy Port → `8080`, Proxy User Name → `username`, Proxy Password → `password`

<div align="center"><img src="../assets/Proxy5.png" alt="" width="600"></div>

{% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}  
4. Save all the changes.
{% endif %}

{% if "OpsHub Integration Manager" === space.vars.SITENAME %}  
9. Save all the changes and restart the <code class="expression">space.vars.SITENAME</code> Service.
{% endif %}

{% if "OpsHub Integration Manager" === space.vars.SITENAME %}  
10. Test the proxy by opening service URL \*\*http://:/TFSService\*\* in browser. Now check the connection by trying to create mapping.
{% endif %}

> **Note**: Even after performing all these steps, if you are still unable to connect, then please check the proxy credentials given in
>
> {% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}  
> Step 3
> {% endif %}
>
> {% if "OpsHub Integration Manager" === space.vars.SITENAME %}  
> Step 8
> {% endif %}
>
> and
>
> {% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}  
> restart your installer.
> {% endif %}
>
> {% if "OpsHub Integration Manager" === space.vars.SITENAME %}  
> restart the <code class="expression">space.vars.SITENAME</code> Service.
> {% endif %}
