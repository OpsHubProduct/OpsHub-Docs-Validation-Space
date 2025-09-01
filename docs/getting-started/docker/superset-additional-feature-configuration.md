## Prerequisites

* Cube and Superset containers should be up and running.

## Configuring OAuth based Authentication

* Ensure that the Superset application is running on HTTPS for configuring OAUTH, as most of providers do not allow http in redirect URL. This can be done by setting up a nginx-proxy docker container, refer [this](https://hub.docker.com/r/nginxproxy/docker-gen) for proxy confihuration.
* Make a local copy of superset_config.py file present in the /app/pythonpath folder inside the container of ‘superset_app’.

```bash
docker cp <container_id>:/app/pythonpath <local_path>
```

* Edit the local copy of superset_config.py file by uncommenting the following piece of code:

```python
# For OAUTH type configuration uncomment the following add the required application credentials
AUTH_TYPE = AUTH_OAUTH
AUTH_USER_REGISTRATION = True
AUTH_USER_REGISTRATION_ROLE = "Admin"
OAUTH_PROVIDERS = [
 {
     "name": "",
     "icon": "",
     "token_key": "access_token",
     "whitelist":['@'],
     "remote_app": {
         "client_id": "",
         "client_secret": "",
         "api_base_url": "",
         "client_kwargs": {
             "scope": "email profile",
         },
         "api_base_url": "",
         "request_token_url": None,
         "access_token_url": "",
         "authorize_url": "",
     },
 },
]
```

* Give the OAuth providers' details in OAUTH_PROVIDERS list and save the file. For more information, refer [superset configuration](https://superset.apache.org/docs/configuration/configuring-superset).
* Copy the local file to its location in superset_app container:

```bash
docker cp <local_path>/superset_config.py <container_id>:/app/pythonpath/
```

* Restart the “superset_init” container:

```bash
docker restart superset_init
```

* Restart the “superset_app” container:

```bash
docker restart superset_app
```

## Setting Up Email Jobs

* Make a local copy of superset_config.py file present in the /app/pythonpath folder inside the container of ‘superset_app’.

```bash
docker cp <container_id>:/app/pythonpath <local_path>
```

* Edit the local copy of superset_config.py file by filling out the following variables to send out emails. For more information, refer [superset configuration](https://superset.apache.org/docs/configuration/configuring-superset).

```python
SMTP_HOST = ""  # change to your host
SMTP_PORT = 587  # your port, e.g. 587
SMTP_STARTTLS = True
SMTP_SSL_SERVER_AUTH = True  # If your using an SMTP server with a valid certificate
SMTP_SSL = False
SMTP_USER = ""  # use the empty string "" if using an unauthenticated SMTP server
SMTP_PASSWORD = ""  # use the empty string "" if using an unauthenticated SMTP server
SMTP_MAIL_FROM = ""
EMAIL_REPORTS_SUBJECT_PREFIX = "[Superset] "  # optional - overwrites default value in config.py of "[Report] "
```

* Copy the local file to its location in superset app container:

```bash
docker cp <local_path>/superset_config.py <container_id>:/app/pythonpath/
```

* Restart the “superset_worker” container:

```bash
docker restart superset_worker
```

* Open Superset application in the browser and select `Settings -> Alerts & Reports`.
* In next window, it will show two tabs: Alerts and Reports. Select the Reports tab.
* Click on `+ Report` button and it will open the following window. Configure the cron schedule, dashboard name, notification method, and the receiver email ids. Click on Add.

![Add Report](../assets/Add_Report.png)

* Click the **Execution log** icon in **Actions** column to access the log details.

## Enabling Row-Level Security (RLS) Rules

* Assign some roles to the users. As an example, let's consider these three roles: Admin, Engineering and Service.
  * In Superset application, go to `Settings -> List Roles`
  * Create a copy of Admin Role and open it in edit mode. Rename the role to Engineering.
  * Select the users you want to give permission to. For example, let's keep `test_eng` user inside Engineering.
  * Save it and assign roles to all users. One can see the assigned roles in `Settings -> List Users` menu.

* Enable the row-level security for these custom roles:
  * Go to `Settings -> Row-Level Security` and click on `+ Rule`.
  * Select the cubes on which you want to enable the row-level security.
  * Select a Role in the Roles field. Select only one role at a time.
  * Select Filter Type = `Regular` for simple rules, and `Base` for inverse rules.
  * In Clause field, type `__user = <role_name>`. For example, `__user = 'Engineering'`. Click on Save.

![Edit Rule](../assets/Edit_Rule.png)

* The configurations from Superset end are completed. However, the rules are not effective without defining them inside cube.js file.
  * Download the cube.js from [here].
  * Define the rules in cube.js that you want to configure. For this, add logic inside `queryRewrite` function for configuring the rules.
  * For details on `query_rewrite`, refer to [Using query_rewrite](https://cube.dev/docs/product/auth/context#using-query_rewrite) and [Authentication and Authorization](https://cube.dev/docs/product/apis-integrations/sql-api/security).

* Save the cube.js file and copy it in cube container:

```bash
docker cp <local_path>/cube.js cube:/cube/conf/
```

* Restart the cube container:

```bash
docker restart cube
```

## Enabling Auto Refresh

* Auto-refresh functionality in Apache Superset is a useful feature that allows users to automatically refresh the page periodically without having to manually refresh. It helps to monitor real-time data in dashboards or alerts, data analysis and exploration.
* Add the desired time interval for refreshing the dashboards to fetch the data periodically, making the dashboards dynamic.
* Click on `Edit Dashboard -> click on three dots on right side -> select Set auto-refresh interval.`
* Select the desired interval from drop-down list.
* Once edited, save the dashboard.
* You may verify the settings preserved in `JSON METADATA`, inside the Dashboard properties.

![Dashboard Properties](../assets/Dashboard_Properties.png)
