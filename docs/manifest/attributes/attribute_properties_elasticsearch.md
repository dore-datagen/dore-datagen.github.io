# Elasticsearch Attribute Properties

* #### `properties` (object)

**Manifest path: `$.models[*].attributes[*].properties`**

```json
{
  "properties": {
    "fieldName": "foo",
    "fieldType": "keyword"
  }
}
```

An attribute corresponds to a field of an Elasticsearch index.

Use this schema when the `datastore` id on the model to which this attribute belongs refers to a datastore that uses the
`elasticsearch7` or `elasticsearch8` protocol.
 
* #### **`fieldName` (string) [required]**

    **Manifest path: `$.models[*].attributes[*].properties.fieldName`**

    Name of the Elasticsearch field that the attribute corresponds to.

* #### **`fieldType` (string) [required]**

    **Manifest path: `$.models[*].attributes[*].properties.fieldType`**

    Name of the Elasticsearch field that the attribute corresponds to.

    All 
    <a target="_blank" href="https://www.elastic.co/guide/en/elasticsearch/reference/current/mapping-types.html">
    field data types supported by Elasticsearch
    </a> 
    are supported here.
