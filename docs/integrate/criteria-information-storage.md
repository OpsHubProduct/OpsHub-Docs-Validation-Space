* Integration throughput can be improved by choosing to store criteria information in the end system instead of the database. This feature is, however, supported on only some systems.

* In the **Criteria Configuration** pop-up, in the **'Select criteria storage type'** field, choose the **'In End System'** from the drop-down list. Once you choose this option, enter the name of the field in the end system to store this information. Please note, only Text, Hyperlink, HTML, RTF, Wiki and Boolean fields can support this storage. 

* By choosing to store the criteria information in the end system, OpsHub is allowed to use the existing criteria query as provided and store relevant information in the selected field in the end system as it processes the entities. In case the entity is no longer required to be stored (but still meeting the set criteria), manually set the value of the field in the end system to “False”.

* This criteria storage feature, however, has some limitations that are listed below.
  * In case multiple integrations exist with different criteria for the same project and same entity, then each criterion will require a different field to allow OpsHub to store the information.
  * In case an entity meeting a criterion was synchronized by OpsHub to the target system and then deleted in the target system, on the next update over that entity in the source system, OpsHub will process the change as per the **''Action on Entity Deleted in Target''** configuration (recreate or ignore), provided the entity still meets the given criteria query.
  * When Rally is the source system, the field selected to store criteria information should have the same *Internal Name* and *Display Name*. No mismatch even in its type casing is acceptable.
  * When Rally is one of the systems in a bidirectional integration, it is mandatory to set the criteria storage field in Rally to ‘True’ from the other system during the ‘create event’ activity. This enables OpsHub to keep that entity in synchronization with the other system in the integration as per OpsHub’s model of integration.
