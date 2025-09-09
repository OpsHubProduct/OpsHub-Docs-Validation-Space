
- **[OpsHub-012000: Processing blocked - Processing is already in progress or has failed for the corresponding target entity; this target entity has to be processed first, then you may require retrying failure for this entity `<entity_id>`](common/opshub-012000.md)**

- **[OpsHub-012010: Processing blocked - Earlier event(s) for the entity `<Entity_Id>` have to be processed first. This is a dependent failure, which may require retry once the actual failure of entity gets processed](common/opshub-012010.md)**

- **[OpsHub-012075: Processing blocked - for the entity `<entity-id>` because the other integration is trying to synchronize the data from this entity. You may need to retry this error once the processing of this entity is completed.](common/opshub-012075.md)**

- **[OH-Connector-0002: Entity with internal id `<entity_id>` does not exists.](common/oh-connector-0002.md)**

- **[OH-Connector-0043: Unable to find following field in target system : `<target field names>`. These fields are mapped in mapping but not present in target system and if you want to skip these fields and sync the remaining fields then select YES in Skip absent fields in advanced configuration in integration.](common/oh-connector-0043.md)**

- **[OH-Connector-0059: Error occurred while processing entity, because `<Link Type>` link is mandatory for `<Entity Name>`. Either it is not configured in issue relationship panel or configured link entity is not found.](common/oh-connector-0059.md)**

- **[OH-Connector-0174: Target entity `<target_entity_id>` corresponding to source entity `<source_entity_id>` is deleted from target system. As you have selected re-create option in such case, integration will create it again in the next run.](common/oh-connector-0174.md)**

- **[OH-Connector-0030: Link will not be added. No entity exists in system with global id `<global_id>`](common/oh-connector-0030.md)**

- **[OH-Connector-0045: An error occurred while getting the input stream for attachment for entity id: `<entity id>` and stream URI: `<attachmentURI>`. Please check if the attachment is present in the source or if it can be accessible by the integration user or not. If you want to skip such attachments globally for all the systems, go to System Configuration -> opshub system -> select 'Skip the attachments for which content is not found in source' as 'Yes'.](common/oh-connector-0045.md)**

- **[Redirect errors with SOAP based services.](common/redirect-errors-with-soap-based-services.md)**

- **[Connection Related Errors](common/connection-related-errors.md)**

- **[OpsHub-020401: Processing blocked for the entity with the id `<Entity Id>` because some other integration is processing the event sync for this entity.](common/opshub-020401.md)**

- **[OpsHub-012074: Processing blocked - Earlier event(s) for the entity with entity id: "`<Entity Id>`" and entity type: "`<Entity type>`" in the integration: "`<Integration Name>`" have to be processed first. It is a dependent failure, which may require a retry once the actual failure of the entity gets processed](common/opshub-012074.md)**

- **[OH-Connector-06200: Entity with entity id "`<Entity Id>`" is expected to have issue type "`<Expected Entity Type>`" and project id "`<Expected Project Id>`" but has issue type "`<Actual Entity Type>`" and project id "`<Actual Project Id>`". Therefore, we will not proceed with the processing until the "Entity Type" and/or Project is restored as per expected values.](common/oh-connector-06200.md)**

- **[OH-Connector-06201: The target entity corresponding to the source entity "`<Entity Id>`" will be created with all source data as the source entity's scope has been updated. Please note this error is thrown temporarily for creating a new entity in the target with all the source data. It will be resolved automatically. If a 0 value is set for the "Maximum Retry Count" in the advanced configuration of the integration, then this failure needs to be retried manually to resolve it; Additionally, if "New Event" has been selected in the "Sync" advance configuration of the integration, then this configuration needs to be updated to "Both (Failed and New Events)" to resolve this error.](../common/oh-connector-06201.md)**

