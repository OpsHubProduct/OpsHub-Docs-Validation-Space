# Description
OH-ServiceNow-1014: Not able to get "Import set table" field for entity type &lt;entity_type&gt; and for actual field &lt;field_name&gt;. Please create field in "Import set table" &lt;import_set_table&gt; and add it to the Transformation Map &lt;transformation_map&gt;.

# Cause

A field is not added in "Import set table" and "Transformation map" for the entity type &lt;entity_type&gt; and for actual field &lt;field_name&gt;.

# Solution

Configure the field (you want to synchronize) within "Import set table" and "Transformation map". 

For steps, please refer [Import Set and Transformation map](../../../../connectors/servicenow.md#configure_import_set_table_and_transformation_map)

As 'Import set table' and 'Transform map' configuration are a part of [pre-requisites](../../../../connectors/servicenow.md#prerequisites) for ServiceNow connector, we would advise you to relook into the pre-requisites and fulfill all of them to avoid such issues in the future.
