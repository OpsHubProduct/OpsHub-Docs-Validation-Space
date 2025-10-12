# Description

Received the error: Entity synchronization is failing due to error: OpsHub-012010: Processing Stopped – earlier event(s) for entity have to be processed first. How to resolve this error?

# Solution

A failed event on a given entity is blocking further synchronization. For example, if OpsHub Integration Manager notices that for entity E1, there is already a failed event in the queue, then all further updates will fail with the above error.  
To fix this error, first find the entity on which the error is coming and fix the error. To get the Entity Id of the entity on which error is coming, follow the steps given below:

* Go to OpsHub Integration Manager Dashboard and click on the Integration Name:  

<p align="center">
  <img src="../../../assets/trouble.png"  width="800px">
</p>

* The exclamation marks represent errors. Pink exclamation mark is Global Failure and Red exclamation mark is Processing Failure. You can click the error directly or click the relevant tab (Global Failure/Processing Failure) to know what the error is. We click the Processing Failure tab.
* Click the ![almarrow.png](../../../assets/almarrow.png) in the error (right corner) to expand the error.
* You can see the Entity Id column listed in the error.
* Fix the error on the entity and retry all failed events for the entity. The error OpsHub-012010 should be processed during retries.
