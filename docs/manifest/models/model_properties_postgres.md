# Postgres Model Properties

** Manifest path: `$.models[*].properties` **

This schema is applicable when `protocol` is `"postgres"`.

## Example

```json title="Postgres Model properties example"
{
    "properties": {
        "tableName": "foobar",
        "schemaName":" baz"
    }
}
```

## Fields

* ###`tableName` (string) [required]

    **Manifest path: `$.models[*].properties.tableName`**

    Name of the PostgreSQL table that the model corresponds to.

    While interacting with the PostgreSQL table corresponding to the model, Dore uses this `tableName`
    to refer to the model in the PostgreSQL database.

* ### `schemaName` (string) [required]

    **Manifest path: `$.models[*].properties.schemaName`**

    Name of the PostgreSQL *schema* that the model corresponds to.

    While interacting with the PostgreSQL table corresponding to the model, Dore uses this `schemaName`
    to refer to the schema in the PostgreSQL database.