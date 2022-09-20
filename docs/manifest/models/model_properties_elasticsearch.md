# Elasticsearch Model Properties

** Manifest path: `$.models[*].properties` **

This schema is applicable when `protocol` is `"elasticsearch7"` or `"elasticsearch8"`.

## Example

```json title="Elasticsearch Model properties example"
{
    "properties": {
        "indexName": "foobar"
    }
}
```


## Fields

* ###`indexName` (string) [required]

    **Manifest path: `$.models[*].properties.indexName`**

    Name of the Elasticsearch *index* that the model corresponds to.

    While interacting with the Elasticsearch indexes corresponding to the model, Dore uses this `schemaName`
    to refer to the schema in the Elasticsearch database.
