## Description

While configuring integration there is one setting called 'Start Polling Time' appear in Entity level mandatory settings section, what is the importance of this settings in integration configuration?  

## Solution

'Start Polling Time' means the time from when <code class="expression">space.vars.SITENAME</code> should start polling data from the source system. <code class="expression">space.vars.SITENAME</code> fetches only those changes/entities that are updated after given 'Start Polling Time'.

While creating new integration, 'Start Polling Time' will be default set to latest updated time of the source system. If you want to sync older entities then change it accordingly. To change 'Start Polling Time', navigate to 'Entity level Mandatory settings' and change it.

>**Note**: Do not change the 'Start Polling Time' once integration has started synchronizing the data otherwise there is a chance of conflicts.
