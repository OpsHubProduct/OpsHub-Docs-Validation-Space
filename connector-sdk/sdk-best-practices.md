- When dealing with REST APIs in the end system, try to map the request and response JSON to programming objects rather than dealing with maps or dictionaries.  
  - For example, when implementing APIs in Java, convert JSON payloads to Java classes.  
    - Following are the links that can help you convert JSON to Java classes:  
      - [https://jsonformatter.org/json-to-java](https://jsonformatter.org/json-to-java)  
      - [https://www.baeldung.com/java-generate-class-from-json](https://www.baeldung.com/java-generate-class-from-json)

- The required static response for [Entity Type – Get](entity-type-get.md) or [Connector Metadata – Get](connector-metadata-get.md) APIs can be stored in JSON format. Additionally, JSON can be converted to programming objects for adding dynamic fields to the response.  
  - Therefore, it will be easier to prepare a JSON file instead of preparing the objects.
