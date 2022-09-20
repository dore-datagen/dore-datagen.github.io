# Elasticsearch Attribute Properties

** Manifest path: `$.models[*].attributes[*].properties` **

This schema is applicable when the model associated with the attribute is linked to a datastore with  `protocol` set 
as `"elasticsearch7"` or `"elasticsearch8"`.

## Example

```json title="Elasticsearch Attribute properties example"
{
  "properties": {
    "fieldName": "foo",
    "fieldType": "keyword"
  }
}
```
 
* ###`fieldName` (string) [required]

    **Manifest path: `$.models[*].attributes[*].properties.fieldName`**

    Name of the Elasticsearch field that the attribute corresponds to.

* ###`fieldType` (string) [required]

    **Manifest path: `$.models[*].attributes[*].properties.fieldType`**

    Name of the Elasticsearch field that the attribute corresponds to.

    All 
    <a target="_blank" href="https://www.elastic.co/guide/en/elasticsearch/reference/current/mapping-types.html">
    field data types supported by Elasticsearch
    </a> 
    are supported here.
