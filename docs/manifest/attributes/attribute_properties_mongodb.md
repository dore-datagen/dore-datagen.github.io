# MongoDB Attribute Properties

** Manifest path: `$.models[*].attributes[*].properties` **

This schema is applicable when the model associated with the attribute is linked to a datastore with  `protocol` set 
as `"mongodb"`.

## Example

```json  title="MongoDB Attribute properties example"
{
  "properties": {
    "fieldName": "foo"
  }
}
```

## Fields

* ### `fieldName` (string) [required]

    **Manifest path: `$.models[*].attributes[*].properties.fieldName`**

    Name of the MongoDB field that the attribute corresponds to.
