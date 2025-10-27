---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: false
  metadata:
    visible: false
---

# Supported Systems

Given below are the systems supported currently by <code class="expression">space.vars.SITENAME</code>:

| No.| System|    Versions Supported       |    Entities Supported                        |           Formerly Known as            |
|----|-------|-----------------------------|----------------------------------------------|----------------------------------------|
| 1 | Aha! | All | Epic, Feature, Release, Requirement, To-do, Note | |
| 2 | Aras Innovator | All | All System Item Types (excluding Item Types of Relationship and Core Type) and All Custom Item Types (excluding Item Types of Relationship Type) | |
| 3 | Azure DevOps Server | {% include "../.gitbook/includes/tfs-tfvc-supported-versions.md" %} | {% include "../.gitbook/includes/tfs-supported-entities.md" %} | Team Foundation Server (TFS) |
| 4 | Azure DevOps Server Version Control | {% include "../.gitbook/includes/tfs-tfvc-supported-versions.md" %} | {% include "../.gitbook/includes/tfvc-supported-entities.md" %} | Team Foundation Server Version Control |
| 5 | Azure DevOps Services | All | {% include "../.gitbook/includes/vsts-supported-entities.md" %} | Visual Studio Team Services (VSTS) |
| 6 | Blueprint* | From 5.4 to 13.0 | All System/Custom Entities | |
| 7 | BMC Remedy* | 6.3, 8.0, 8.1 | Request | Remedy |
| 8 | Broadcom Clarity | SaaS : 16.2.2 and above | Project, Task, To Do, Custom Investment Object (Parent only) | CA PPM |
| 9 | Broadcom Rally Software | All | Portfolio Items, Defect, Task, Test Case, Test Case Result, Test Set, Test Folder, User Story, Change Set [Write support only, Release, Iteration, Milestone], Risk | CA Agile |
| 10 | Broadcom Service Desk Manager* | alb-165 | Change Request, Incident, Problem, Issue | CA Service Desk Manager |
| 11 | Bugzilla | 4.4, 4.4.1, 4.4.2, 5.0 and above<br/>Read only: 4.4.3 to 4.4.13 | Bug | |
| 12 | Cherwell* | 10.1.0 | Incident | |
| 13 | Codebeamer | 21.09-SP3, 21.09-SP9, 22.10 LTS, 2.x, 3.x | All System and Custom Tracker items<br/><br/>Not Supported: SCM type entities (Working Sets, Baselines, SCM commits, repositories), timekeeping trackers (Worklogs), Non-ALM entities (Wiki pages, documents) | |
| 14 | Codebeamer X | 4.2.1 | All System and Custom Tracker items<br/><br/>Not Supported: SCM type entities (Working Sets, Baselines, SCM commits, repositories), timekeeping trackers (Worklogs), Non-ALM entities (Wiki pages, documents) | |
| 15 | Database | All versions supported for MySQL, MS SQL Server/Azure SQL, Oracle, PostgreSQL, MariaDB | All tables or views in the database | |
| 16 | Digital.ai Agility | Cloud (All) | Backlog Item, Defect, Epic, Goal, Issue, Request, Task, Test, TestSet, Theme, Project/Release, Iteration, Build Run, Changesets, Actuals | VersionOne |
| 17 | Digital.ai TeamForge | 17.11 to 21.x | All System/Custom Tracker Types, Planning Folders, Teams | |
| 18 | Enterprise Architect** | 10, 11, 13.0, 13.5, 14, 15, 16 (Build 1622 onwards), 17 | Element, Diagram, Package, Operation (read only), Attribute (read only) | |
| 19 | FogBugz* | 8.8.*, 8.9.*, 8.9.110.0H, 8.9.122.0H | Case | |
| 20 | Gerrit | 3.6.8 | Change (read only) | |
| 21 | Git | 1.7.6, 1.8.3 | Commit Information (read only) | |
| 22 | GitHub | GitHub Enterprise - From 2.7 to 2.20<br/>SaaS - 2.1 | Issue, Commit Information (read only), Pull Request (read only) | |
| 23 | GitLab | SaaS<br/>On Premise: 15.x, 16.x, 17.x, 18.x | Commit (read only), Epic, Issues | |
| 24 | Helix ALM | 2021, 2024 | Requirement, Issue, Test Case | Testtrack |
| 25 | Helix Core* | 2009.2, 2013.1, 2015 | Commit Information (read only) | |
| 26 | HubSpot | SaaS | Deal, Ticket, Contact, Company, Orders, Notes, Emails, Tasks, Calls, Meetings | |
| 27 | IBM DevOps Code ClearCase* | 8.x | Delivery Information | Rational ClearCase |
| 28 | IBM Engineering Requirements Management DOORS Next | 6.0.5, 6.0.6, 7.0.1, 7.0.2 to 7.0.2 IFix25, 7.0.3 | All Artifacts (Text + Collection) | IBM DOORS NG |
| 29 | IBM Engineering Test Management | 6.0.5, 7.0.1 | Test Plan, Test Suite, Test Case, Test Script, Test Case Execution Record, Test Case Result, Keyword | |
| 30 | IBM Engineering Workflow Management | 5.0.2, 6.0.1, 6.0.2, 6.0.3, 7.0.1, 7.0.2 | Process Template/All Custom Entities | Rational Team Concert |
| 31 | IBM Rational ClearQuest | 8.x | Defect / Any Stateful Record Type | |
| 32 | IBM Rational DOORS | 9.1–9.7.2 | Requirement, Baseline (read only) | |
| 33 | IBM Rational RequisitePro* | 7.0.1+ | Requirement [All Custom-created Requirement Types supported] | |
| 34 | Jama Connect | Cloud/Self-Hosted: From 8.22+ | All System/Custom Item Types (Defect, Epic, Persona, Test Plan, Test Cycle, Test Run, Commit, Component, Set, Folder, etc.)<br/>Not Supported: Attachment, Core | |
| 35 | Jenkins | 1.617, 2.7.1 | Build (Read & Trigger) | |
| 36 | Jira Agile | Cloud<br/>Data Center: 6.7.7 – 9.12.x | Sprint, Epic, Link | |
| 37 | Jira AIO (All-In-One) Tests* | Data Center: 4.4.0<br/>Cloud: 4.4.0 | AIO Test Case (read), AIO Test Cycle (read), AIO Test Run (read) | |
| 38 | Jira Align | SaaS | Capability, Customer, Defect, Epic, Initiative, Portfolio, Program, PI, Release, Sprint, Story, Task, Theme, Value Stream, Objectives | |
| 39 | Jira Cloud | All | All System & Custom Issue Types, Sub-Task Types, Version, Work-log | |
| 40 | Jira Data Center | 5.x–10.x | All System & Custom Issue Types, Sub-Task Types, Version, Work-log | |
| 41 | Jira Elements Connect | On-Premise: 6.13.x | Live text/user/date/datetime custom fields | |
| 42 | Jira Project & Portfolio Management | From Jira 8.15+ (part of Jira software)<br/>2.24.0–3.29.x | Portfolio Items | |
| 43 | Jira QMetry** | On Premise: QMetry 3.X, Build 4.6.1 | Test Case, Test Scenario, Test Run, QMetry Test Execution | |
| 44 | Jira R4J | 4.4.x–4.18.4 | Folders, R4J Relationships (Folders ↔ Jira Issues) | |
| 45 | Jira Service Management | Cloud<br/>On Premise: 3.1.10–5.12.1 | All System & Custom Issue Types | Jira Service Desk |
| 46 | Jira SLA Powerbox | 3.x–4.2.x (excl. 3.5.x) | SLA Metric field (read only) | |
| 47 | Jira Stagil Assets Management | On Premise: Stagil Assets – Advanced Link 5.0.86 | All Entities Supported By <code class="expression">space.vars.SITENAME</code> In JIRA | |
| 48 | Jira Xray** | On Premise: 3.6.x–6.1.3<br/>Cloud: V1.1.90-AC-4.004.000 | On Premise: Test, Test Plan, Test Execution, Test Set, Sub Test Execution, Pre-Condition<br/>Cloud: Xray Test, Test Plan, Test Execution, Test Set, Test Run, Precondition | |
| 49 | Jira Zephyr Essential** | Data Center: 9.x, 10.x<br/>Cloud: 8.x (1.3.33-AC) | Test, Test Cycle, Test Execution, Folder | Zephyr Squad |
| 50 | Mercurial* | 2.0–2.0.1, 2.6.1, 2.6.2 | Commit Information | |
| 51 | Microsoft Dynamics 365 | 9.2 | All Entities | |
| 52 | Modern Requirements | 2010–2019 | Test Result, Test Run, Test Suite, Work items (Bug, Requirement, Task, Test Case, User Story, etc.), Iteration, Git Commit, Custom Entities | |
| 53 | OpenText ALM Octane | On Premise: 16.1.x, 16.2.x<br/>SaaS | Defect, User Story, Epic, Feature, Task, Requirement, Test, Run, etc. | Micro Focus ALM Octane |
| 54 | OpenText ALM Quality Center | SaaS: 15.x<br/>On-Prem: 10.0+ to 24.x | Defect, Requirement, Test, Test Set, Release, Cycle, Test Run, Folders, Configurations, Execution Request | Micro Focus ALM/QC, HPALM |
| 55 | OpenText IT Operations Cloud* | 2009 R3,R4, 10.1.2.1,11.0 | All Custom Primary Item Entities | Serena Business Manager |
| 56 | OpenText Project & Portfolio Mgmt (PPM)* | 11.3, 11.5 | Requirement | Caliber RM |
| 57 | PagerDuty | Cloud | Incident | |
| 58 | ReadyOne | 14.0.x (Release 26) | All System Item Types (Core + Custom) | |
| 59 | Redmine | 3.1.2+ | Redmine Issue + Custom Issue Types | |
| 60 | Salesforce | All | Case, Opportunity, Feeds, Custom Objects | |
| 61 | SAP** | ECC, S/4HANA | Program, Transport Request, Transaction Code, Enhancement, Usage Details, Table, Function, Package, Auth Object, Class, Data Element, TADIR | |
| 62 | Selenium* | All | TestScripts | |
| 63 | ServiceNow | San Diego–Zurich | All System + Custom Tables | |
| 64 | Slack* | Cloud | Comments, Attachments, Post (write only) | |
| 65 | Snowflake** | Cloud | Tables and Views | |
| 66 | Subversion* | 1.5, 1.6.3, 1.6.17, 1.7.9 | Commit Information | |
| 67 | TestRail** | 7.2.1, 7.8.0, 8.0.1 | Tests, Test Cases, Test Plans, Test Results, Test Runs, Test Suites, Sections, Milestones | |
| 68 | Trac* | 0.12.0, 0.11.5, 1.0 | Trac Ticket | |
| 69 | Tricentis qTest | Cloud (All)<br/>On-prem: 8.4.2–2023.x.x | Defect, Requirement, Testcase, Testlog, Release, Test Suite, Test Run, Module, Test Cycle, Build (read only) | QA Symphony |
| 70 | Tricentis Tosca | 2023.2.x, 2024.2.x (x64) | TestCase, ExecutionTestCaseLog (read), ExecutionEntry, TCFolder, Requirement, RequirementSet, Issue, Module | |
| 71 | Verisium Manager** | 20.x–25.x (up to 25.01) | Section, Metrics Port, Reference [from 21.01+]<br/>Supported for vPlan in DB only | vManager |
| 72 | Windchill | 2009–13.3 | Change Order, Change Request, Defect, Document, Model, Portfolio, Product, Project, Requirement, Test, Specification, Work Item, Custom Entities | PTC, Windchill RV&S |
| 73 | Zendesk | Cloud | Zendesk Ticket | |


(*) Professional services required for version specific certification.  
(**) Professional services recommended due to modelling complexity.
