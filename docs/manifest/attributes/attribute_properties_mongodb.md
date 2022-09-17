# MongoDB Attribute Properties

* #### `properties` (object)

**Manifest path: `$.models[*].attributes[*].properties`**

```json
{
  "properties": {
    "fieldName": "foo"
  }
}
```

An attribute corresponds to a field of a MongoDB collection.

Use this schema when the `datastore` id on the model to which this attribute belongs refers to a datastore that uses the
`mongodb` protocol.

* #### **`fieldName` (string) [required]**

    **Manifest path: `$.models[*].attributes[*].properties.fieldName`**

    Name of the MongoDB field that the attribute corresponds to.
