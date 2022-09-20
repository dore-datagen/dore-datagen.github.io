# MySQL Model Properties

** Manifest path: `$.models[*].properties` **

This schema is applicable when `protocol` for linked datastore is `"mysql"`.

## Example

```json title="MySQL Model properties example"
{
    "properties": {
        "tableName": "foobar"
    }
}
```

## Fields

* ###`tableName` (string) [required]

    **Manifest path: `$.models[*].properties.tableName`**

    Name of the MySQL table that the model corresponds to.

    While interacting with the MySQL table corresponding to the model, Dore uses this `tableName`
    to refer to the model in the MySQL database. 