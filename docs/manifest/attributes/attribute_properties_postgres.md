# Postgres Attribute Properties

** Manifest path: `$.models[*].attributes[*].properties` **

This schema is applicable when the model associated with the attribute is linked to a datastore with  `protocol` set 
as `"postgres"`.


## Example

```json title="Postgres Attribute properties example"
{
  "properties": {
    "columnName": "foo",
    "columnType": "VARCHAR(30)"
  }
}
```

## Fields

* ###`columnName` (string) [required]

    **Manifest path: `$.models[*].attributes[*].properties.columnName`**

    Name of the Postgres column that the attribute corresponds to.
    
    While creating tables in Postgres for Postgres bound models in the manifest,
    Dore infers the required column name from this field's value.

* ### `columnType` (string) [required]

    **Manifest path: `$.models[*].attributes[*].properties.columnType`**

    Data type of the Postgres column that the attribute corresponds to.
    
    All 
    <a target="_blank" href="https://www.postgresql.org/docs/current/datatype.html">
    data types supported by Postgres
    </a> 
    are supported here.
