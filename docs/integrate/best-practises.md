Here are some best practices to consider when working with OpsHub Integration Manager.

# Infrastructure

## Database

* Use any database from the supported 4 databases [Oracle, MSSQL Server, MySQL, PostgreSQL] for production deployment. HSQL shouldn't be used for production deployments.

## Database Disk Space

| WorkItem             | Sync State         | Estimated DB Size       |
|----------------------|--------------------|--------------------------|
| <100K                | Current/History    | 50GB                    |
| 100K to 500K         | Current/History    | 100GB                   |
| 500K to 1 million    | History State      | 150GB                   |
| 500K to 1 million    | Current State      | 150GB to 250GB          |

> ![](../assets/Note.jpg) Actual size depends on various factors, including the total count of work items, sync state, sync failures, number of attachments, links, and overall usage patterns. For small-scale implementations, starting with a minimum database size of 15GB is recommended to accommodate initial needs effectively.

## RAM and Threads

| Integration | RAM allocated to OIM | Threads in OIM | Machine Core | Heap Space | Machine Disk Space | Environment Type    |
|-------------|----------------------|----------------|--------------|------------|---------------------|---------------------|
| Up to 50    | 8GB                  | 27             | 4            | 4GB        | 50GB-100GB          | Small               |
| 50-150      | 16GB                 | 50             | 6            | 12GB       | 150GB-200GB         | Medium              |
| 150-900     | 32GB                 | 100-150        | 8            | 28GB       | 300GB-350GB         | Large/Enterprise    |

> ![](../assets/Note.jpg) The RAM data is estimated, as RAM requirements depend on several factors, including the number of integrations, thread count, and scheduling cycle settings.

## Enable Monitoring for OpsHub Service, Database, and VM for Health Check

* In a production environment, it's important to have monitoring in place for the OpsHub service, database, and the virtual machine (VM) where OpsHub is installed.
  * **Set up alert**: OpsHub service, database, or VM goes down.
  * **Monitor OpsHub's database access** (if possible): if the database becomes unavailable or there are access issues, alerts are triggered.
* When OpsHub is down: It will not generate its usual failure alerts. Therefore, external monitoring is necessary to ensure you receive alerts if the system, database, or VM becomes unresponsive.

## Enable Database and VM backups

* **Database backup**: Once a day or less (point in time).
  * Frequent backups ensure you can quickly recover the most recent configuration, mappings, and sync histories in case of data loss or corruption.
* **VM [OIM installed] backup**: Once a month or quarterly.
  * A monthly or quarterly backup allows you to capture the state of the VM, including OS-level changes and configurations, while not overwhelming storage with frequent snapshots.

# Integration

## Integrate multiple projects through a single integration

* Group integrations for management efficiency when:
  * Multiple projects share similar templates or artifact structures.
  * Managing individual integrations becomes cumbersome.  
    Example: Managing user stories, tasks, and bugs across multiple Jira and Rally projects.
* **Grouping Benefits:**
  * Reduced API Calls
  * Simplified Maintenance
  * Unified Control
  * Easier Error Handling

## Managing Project Count in Integrations

* **Limit Projects per Integration**: 25 or fewer for optimal performance.
* **Balance Large and Small Projects**: Combine large projects (100,000+ entities) with smaller ones to avoid overloading the integration.

## Enable Remote ID and Remote Link

* **Remote ID**: Easily find and track items across systems.
* **Remote Link**: Relationships between items and understanding their connections.

## Polling Frequency/Scheduling

Setting the appropriate polling frequency is crucial for effective integration management.

| Criteria                                             | Recommended Polling Frequency                                          | Use case                                                                 |
|------------------------------------------------------|------------------------------------------------------------------------|--------------------------------------------------------------------------|
| Target: Reporting and compliance (Once a week)       | Every 12 hours<br> High volume: every 1 to 6 hours                     | Predictable data availability with fixed schedule (e.g., 6 AM/6 PM).     |
| Target: Needs latest data within 24 hrs              | Every 2 to 6 hours                                                     | Ensures data is updated in target system within a few hours.            |
| Small-scale environments                             | Every 15 minutes                                                       | Ensure quick data updates.                                              |
| Large-scale environments with 150+ integrations      | Every 30 minutes or more (Consult OpsHub for under 30 min)            | Reduces API calls and optimizes performance.                            |
| Non-time-based entities (e.g., Sprints, Iterations)  | Every 24 hours                                                         | Poll during non-peak hours (e.g., 12 AM) to minimize system load.       |

# Mapping

## Configure Multiple Integrations via a Single Mapping

* Identify similar integrations: Determine if multiple integrations share the same project template or artifact structure.
* Create a single field mapping: Develop one field mapping to apply across all identified integrations.

## Configure Default Value for Mandatory Fields

* When source field is optional and target is mandatory:
  * Do default value mapping: Configure a default value for the mandatory field in the target system to avoid sync failures.
* User fields' mismatch:
  * Ensure matching email addresses: Confirm that the same users exist in both systems to find the correct user during synchronization.
* User missing in target system:
  * Set up a default user: Assign a default user when an exact match isn't found to ensure successful synchronization.

## Enable Link Configuration in Cross-Entity Mappings for Sync

* To ensure that links sync reliably, set up relationships in both mappings.
  * For example, if a Bug is linked to a Requirement and you want this link to transfer to another system, add the link configuration in both the Bug and Requirement mappings. This setup helps keep relationships consistent across systems.

# Sync Monitoring

## Enable Failure Notification Emails

Setting up the failure notification emails in OIM is an essential practice that helps you stay on top of any issues with your data integration.

* **CC Key Personnel**: Add key team members to CC for prompt action if the main recipient is unavailable.
* **Persistent Failure Alert**: Set to 1 hour—alerts you about serious issues beyond temporary glitches.
* **Inactivity Alert**: Set to 24 hours to flag prolonged inactivity; shorter durations may cause unnecessary alerts.
* **Include Error Trace**: Enable to provide detailed failure information, speeding up troubleshooting.

## Manage Log Settings to Optimize Size and Improve Troubleshooting

| Setting                               | Description                                                                                      |
|---------------------------------------|--------------------------------------------------------------------------------------------------|
| Compress Backup Files [Global setting]| Enable at the global level to reduce log size and save memory.                                   |
| Log level                             | Production: Use WARN<br>Temporary Debugging: Use DEBUG/TRACE, then revert to WARN<br>Testing: DEBUG |
| Max Log Size                          | 50MB                                                                                            |
| Backup Files                          | 5                                                                                                |
| Lines per Log file                    | 100                                                                                              |

## Organize Integrations with Folders for Better Management

* Create folders for different integrations to enhance clarity.
* **Team or Project-Specific Folders**: Set up specific folders for each team or project to simplify management.

# Sync Optimization

## Enhance Performance by Setting a Longer Cache Timeout in OpsHub System

To reduce API calls and improve performance, it's recommended to set a longer cache timeout (like 24 or 48 hours), especially when metadata updates such as projects and fields are stable or infrequent. This approach minimizes unnecessary requests and helps prevent memory issues.

| Metadata Update Frequency             | Cache Timeout        |
|--------------------------------------|----------------------|
| Multiple times a day (e.g., hourly)  | 60 minutes           |
| Infrequent updates (1–2 times/week)  | 24 – 48 hours        |
| Stable environment with rare updates | 1 week               |

# Don'ts

Here are the practices you must avoid while working with OpsHub Integration Manager. While some exceptional cases may require specific operations, admins must not perform any of the following actions with the OpsHub Integration Manager system without proper guidance.

* Do not rename entity types or projects into end systems. Please consult the system expert or OpsHub Integration Manager support before implementing any such change in the end system.
* Do not upgrade OpsHub Integration Manager without going through pre and post migration checklist document.
* Do not back date 'Start polling time' once integration has started synchronizing.
* Do not delete any failures from the integration failure queue.
* Verify target search queries when you configure integration or reconciliation with this input to consider manually created entities are matched before integration transacts. Admin should manually verify that the search query is correct and producing the expected results. If this query is wrongly configured, then there are chances of entity duplication. For more information on what target search query is, refer to [Search in Target Before Sync](../integrate/integration-configuration.md#search-in-target-before-sync) section.
