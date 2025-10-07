## Description

* Loading the audits can be affected by the size of audits as the audits will be keep increasing over the time.  
* To improve the audit loading time, the clean up for unnecessary audits on specific time period is required.  
  - **Reason:** Removing the audits reduce the database size.  

## Solution

* Please refer to [Purge Audit Logs](../../../manage/administrator/purge-records.md#purge-audit-logs) page to know more about how to remove the audits data in <code class="expression">space.vars.SITENAME</code>.  
* Use small time frame/window (e.g., 6 months or 1 year) for purge operations.  
  - **For example:** The <code class="expression">space.vars.SITENAME</code> was installed in Jan-2015, then <code class="expression">space.vars.SITENAME</code> will have audits since Jan-2015 till date.  
    - In first go, purge audits till Dec-2015.  
    - In second go, purge audits till Dec-2016.  
    - Follow the same process till the date you want to remove the audit.  

* **Note:** Removing the audits data will not affect the synchronization.  
