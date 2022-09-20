# MongoDB Model Properties

** Manifest path: `$.models[*].properties` **

This schema is applicable when `protocol` for lined datastore is `"mongodb"`.

## Example

```json title="MongoDB Model properties example"
{
    "properties": {
        "collectionName": "foobar"
    }
}
```

## Fields

* ###`collectionName` (string) [required]

    **Manifest path: `$.models[*].properties.collectionName`**

    Name of the MongoDB collection that the model corresponds to.

    While interacting with the MongoDB collection corresponding to the model, Dore uses this `collectionName`
    to refer to the model in the MongoDB database. 