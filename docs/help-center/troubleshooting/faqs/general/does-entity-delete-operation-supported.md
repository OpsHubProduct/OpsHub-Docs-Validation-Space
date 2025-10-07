# Description

Integration is configured from system A to system B. If entity is created/updated in system A then it will appropriately create/update in system B through <code class="expression">space.vars.SITENAME</code>.  

Now if entity is being deleted in system A, will <code class="expression">space.vars.SITENAME</code> synchronize delete operation in system B as well so that entity in system B is deleted after synchronization? 

# Solution

<code class="expression">space.vars.SITENAME</code> does not support delete operation. To work on the delete use case scenario, <code class="expression">space.vars.SITENAME</code> recommends adapting an approach of logical delete. 

Follow the steps below to adapt logical delete approach: 

1. Don't actually delete the entity but just mark the entity as deleted in some custom field or status that represents that an item has been deleted.  
2. Do field mapping to map that custom field or status value that is representing deleted to appropriate destination field or value which is representing deleted in destination.  
3. Once source side entity is marked deleted then <code class="expression">space.vars.SITENAME</code> will synchronize this value to target side to indicate that an item had been marked as deleted.  
