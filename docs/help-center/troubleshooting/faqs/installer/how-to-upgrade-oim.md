## Description

Migrating {{SITENAME}} to new version will ensure that the application includes new features and improved functionality.

## Solution

Make sure that the {{#ifeq: {{SITENAME}} | OpsHub Migrator for Microsoft Azure DevOps | [Pre-Upgrade Checklist](../../../../manage/upgrade/upgrading-application-version.md#pre-upgrade-checklist) | [Migration Pre-requisites](../../../../manage/upgrade/upgrading-application-version.md#migration-pre-requiste-for-windows-and-linux) }} steps are followed before migrating to new version.

Once the pre-requisites are met, follow one of the below {{#ifeq: {{SITENAME}} | OpsHub Migrator for Microsoft Azure DevOps | section | sections }}

- [Steps to migrate on Windows](../../../../manage/upgrade/upgrading-application-version.md#migration-steps-for-windows)  
{{#ifeq: {{SITENAME}} | OpsHub Migrator for Microsoft Azure DevOps || [Steps to migrate on Linux](../../../../manage/upgrade/upgrading-application-version.md#migration-steps-for-linux) }}

Once migration is completed successfully, follow these [Post Migration Steps](../../../../manage/upgrade/upgrading-application-version.md#post-migration-steps-for-windows-and-linux).

In case the migration fails, you can check for the cause of failure in `Migration.log` file located under `logs` folder at {{SITENAME}} `<installation_path>`.
