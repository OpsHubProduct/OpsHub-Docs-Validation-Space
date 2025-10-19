# Known Limitations

* Docker-based deployment for <code class="expression">space.vars.SITENAME</code> is not supported with HSQL database.
* End systems where other services or external tools dependency would be needed, then those services need to be deployed separately on another machine, as it can not be deployed in the Docker container. E.g., TFS Service.
* Docker-based deployment should not be used, if IBM Rational DOORS is one of the end points in the sync.  
    * **Reason:** DOORS requires a Windows host.
