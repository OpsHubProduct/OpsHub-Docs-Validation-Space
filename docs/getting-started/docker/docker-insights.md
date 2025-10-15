# Prerequisites
{% include "../.gitbook/includes/docker-prerequisites.md" %}

![info](../assets/info.jpg)  
*Follow steps as given on [Docker Insights PreConfiguration](../docker/docker-insights-preconfiguration.md) page to configure the required jsons for creating SCM and ALM Systems' integrations.  
  **The json files are in `userjsons` folder in `InsightsPreConfigurations.zip` along with the Docker image.*  
*In case of **Git** as an SCM system, the Git repository needs to be cloned in the VM where the docker container needs to be created, and the cloned repository needs to be copied to the container.  
*The database used for OpsHub Insights installation must not be restricted to localhost. It should be configured to allow access from Docker containers, as it will be used in Cube and Superset containers for data visualization.

# Steps to run OpsHub Insights on Docker
{% include "../.gitbook/includes/oim-docker-configurations.md" %}

![info](../assets/info.jpg)  
*Extract `InsightsPreConfigurations` and `CubeSupersetResources` folders from their respective compressed zip files.  
*The `InsightsPreConfigurations` folder containing updated jsons needs to be mounted to `/home/InsightsPreConfigurations` in the container for configuring systems in the docker-based deployment.  
*Remove the comment from the line which mounts the `InsightsPreConfiguration` folder in `docker-compose-OIM.yml` file.  
```yaml
- "./InsightsPreConfigurations:/home/InsightsPreConfigurations"
```

*If `InsightsPreConfigurations` folder is available in the same directory as the `docker-compose-OIM.yml`, there is no need to change the path. Else, provide the local path of the extracted `InsightsPreConfigurations` folder before colon (`:`).

## Superset Dashboard Configuration

The variable values need to be added in `config.json` inside `CubeSupersetResources` folder to set up the Superset dashboard.

| **Variable Name**         | **Description**                                                              | **Sample Value**                                                                 |
|---------------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| `hostName`                | Name or IP of the host where <code class="expression">space.vars.SITENAME</code> is installed         | localhost                                                                       |
| `commitUrlPath`           | Commit URL for SCM system used to redirect user to the SCM system            | https://github.com/docker/compose/commit                                        |
| `authentication`          | Authentication password salt for <code class="expression">space.vars.SITENAME</code> login            | Basic YWRtaW46cGFzc3dvcmQ=                                                      |
| `workitemUrlPath`         | Work item URL for ALM system to redirect user to ALM                         | https://org.visualstudio.com/project/_workitem/edit                             |
| `productionAreas`         | Used to show area-specific filters in dashboard                              | ('OpsHub Production', 'OpsHub Demo(Configuration)', 'PS', 'Support', 'Partners') |
| `defectTypeName`          | Work item type names for defect                                               | ('Bug')                                                                         |
| `featureTypeName`         | Work item type names for feature                                              | ('Feature')                                                                     |
| `requirementTypeName`     | Work item type names for requirement                                          | ('Requirement')                                                                 |
| `taskTypeName`            | Work item type names for task                                                 | ('Task')                                                                        |
| `problemTypeName`         | Work item type names for problem                                              | ('Problem')                                                                     |
| `releaseTypeName`         | Work item type names for release                                              | ('iteration')                                                                   |
| `failureTypeName`         | Work item type names for failure                                              | ('Failure')                                                                     |
| `threshold`               | Minimum value threshold for delta code coverage                              | 90                                                                              |
| `gitRepositoryFilePath`   | SCM repo URL to main/master branch of SCM system                              | https://github.com/docker/compose                                               |
| `migrationFileExtension`  | Regex for migration file extension                                            | %.sql                                                                           |
| `migrationFilePaths`      | Regex to migration file folder path                                           | ["OpsHubV2/Util/com/opshub/migrations/", "OpsHubV2/sql/migrations/"]            |

## Install and setup <code class="expression">space.vars.SITENAME</code>, Cube and Superset

* **Windows**: Open Command Prompt inside the directory containing `OIM_Insights_Installation.bat` file. Execute:
```bat
OIM_Insights_Installation.bat
```

* **Linux**: Open Terminal inside the directory containing `OIM_Insights_Installation.sh` file. Execute:
```bash
sudo su
bash OIM_Insights_Installation.sh
```

* On completion, the script will start showing logs of <code class="expression">space.vars.SITENAME</code>. To halt, press `Ctrl+C`.  
* Installation logs will be stored in `OIM_Cube_Superset_Installation.log` inside the installer directory.  
* Open Superset and Cube environment in browser:
  - **Cube**: `http://<HOST_NAME or IP>:4000/`
  - **Superset**: `http://<HOST_NAME or IP>:8088/`  
* For additional features, refer to [Superset Additional Feature Configurations](../docker/superset-additional-feature-configuration.md)

### After installation dashboards customization

#### Cubes and Views:
- The Docker container for Cube includes four folders for cubes and views at `/cube/conf/model`.
- `cubes` and `views` folders contain **default** cubes and views. **DO NOT modify them**.
- `custom_cubes` and `custom_views` folders are empty by default. Add new custom cubes/views here if needed.
- Modifications in `custom_cubes` and `custom_views` will be **retained** after upgrades. All other folders may be overwritten.

#### Superset Dashboards:
- Default dashboards will be auto-imported.
- You may create and add new custom dashboards after installation.
- Custom charts can use existing datasets or newly added custom cubes/views.
- You may rename or remove default dashboards, but these changes will be **overwritten** during upgrades.
- Custom dashboards will be retained post-upgrade.
- If a default dashboard is deprecated in a new release, remove it manually after upgrade.
- If a chart is removed from the source and was part of a custom dashboard, it will no longer be available.

# Steps for copying the Git repository in the Docker container

*If **Git** is the SCM system, clone the Git repository on the VM where the Docker container will run, then copy it to the container.*

1. Run the container (as per previous section), then in a separate session:
2. Check if container is running:
```bash
docker ps -a
```

3. Note `<Container_Name>` from the last column of the output.
   - If not visible, wait and rerun the command.
4. Run the command below to copy the Git repository into the container:
```bash
docker cp "<Path To Git Repository>" "<Container_Name>":/home/repository
```
- Replace `<Path To Git Repository>` with actual repo location.
- You may use `Container_Id` instead of name.
- The destination path `/home/repository` must match the `gitRepositoryPath` in `Git_systemUserProperties.json`.

> ![info](../assets/Note.jpg) If `gitRepositoryPath` is `"home/repository"`, then the copy destination should also be `"/home/repository"`.

# Limitations

Refer to [Docker Limitations](../docker/docker-limitations.md)

# Upgrade Application Version

## Upgrade <code class="expression">space.vars.SITENAME</code> Application Version

Refer to [Docker Update OIM](../docker/docker-update-oim.md)

## Upgrade Cube and Superset Application Version

1. Extract `CubeSupersetResources` from its zip.
2. Backup custom dashboards (export them from Superset).
3. Backup Docker volumes: `superset_home`, `db_home`, `redis`.
4. If `superset_config.py` was modified, backup from container:
```bash
docker cp superset_app:/app/pythonpath/superset_config.py superset_config_backup.py
```

> **Optional:** Update the new `superset_config.py` inside `CubeSupersetResources/superset_resources` using the backup if needed. See [Superset Additional Feature Configurations](../docker/superset-additional-feature-configuration.md)

5. If any new attribute is added or updated in `config.json`, modify the file in `CubeSupersetResources`.  
   Leave values as `""` to retain existing.

6. Update volume names in:
   - `docker-compose-non-dev-linux.yml`
   - `docker-compose-non-dev-windows.yml`

Update values
