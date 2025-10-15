## Description

For OH-Connector-06200, the following error message appears:

OH-Connector-06200: Entity with entity id `<Entity Id>` is expected to have issue type `<Expected Entity Type>` and project id `<Expected Project Id>` but has issue type `<Actual Entity Type>` and project id `<Actual Project Id>`. Therefore, we will not proceed with the processing until the `Entity Type` and/or Project is restored as per expected values.''


## Cause

* The reason for this error is the mismatch between the expected "Entity type" and/or "Project" and the actual "Entity type" and/or "Project" for the target entity.
* When the entity type and/or project of the entity changes, further processing on the entity cannot be done with the given integration. This is because the end system can have different processing requirements for different entity types and/or projects. Hence, <code class="expression">space.vars.SITENAME</code> will generate the error for this event to inform the end user about the unexpected state of the entity for the values of "Entity type" and/or "Project".
* Suppose, for instance, <code class="expression">space.vars.SITENAME</code> synchronizes the "Entity type 1" in System 1 to the "Entity type 2" in System 2. And the entity type of the synchronized entity from system 1 to system 2 is updated from "Entity type 2" to "Entity type 3". There can be different fields for "Entity type 2" and "Entity type 3", so processing the data for "Entity type 3" using the configuration of "Entity type 2" can lead to an unexpected situation. <code class="expression">space.vars.SITENAME</code> will not proceed in this case.

## Solution

* Suppose the integration related to the updated "Entity type" and/or "Project" is unavailable in <code class="expression">space.vars.SITENAME</code>, In that case, the user needs to manually restore the entity by updating it with the expected value of "Entity type" and/or "Project" and retry the failure by clicking the 'Retry All With Dependents' failure option. For more information on how to retry failed event, refer [manage integration failures](../../../troubleshooting/manage-integration-failures.md#action-on-failures).
* Suppose bidirectional integration related to the updated "Entity type" and/or "Project" is available in the <code class="expression">space.vars.SITENAME</code>. In that case, it will take the following actions as per the "Entity Type" and/or "Project" change synchronization.
  * Suppose an "Entity type" and/or "Project" update is possible on the target entity corresponding to the entity whose "Entity type" and/or "project" is not matched with the expected values. In that case, this error will be auto-resolved by <code class="expression">space.vars.SITENAME</code> using the integration of updated "Entity type" and/or "Project".
  * Suppose an "Entity type" and/or "Project" update is not possible on the target entity corresponding to the entity whose "Entity type" and/or "project" is not matched with the expected values. In that case, this error will be deleted by the <code class="expression">space.vars.SITENAME</code> as the previously synchronized entity will be deprecated due to this "Entity type" and/or "Project" change.
