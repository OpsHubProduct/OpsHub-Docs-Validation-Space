
# Description
<code class="expression">space.vars.SITENAME</code> supports a polling mechanism for retrieving data from source systems. The polling mechanism can be categorized based on the richness of the end system's API.

# Category of Read Mechanism
<code class="expression">space.vars.SITENAME</code> supports 3 types of Reading Mechanism Techniques.

## History
* "History" means that the end system provides APIs that allow access to the history or audit data of the items.

## Non-History
* "Non-History" means that the end system does not provide APIs to access the history or audit data of the items.

## Non-Timestamp
* "Non-Timestamp" refers to a scenario where the end system's API either lacks fields for creation or update dates, or does not support filtering based on these fields. This is also known as TimeBox.
