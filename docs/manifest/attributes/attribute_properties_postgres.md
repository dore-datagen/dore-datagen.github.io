# Postgres Attribute Properties

* #### `properties` (object)

**Manifest path: `$.models[*].attributes[*].properties`**

```json
{
  "properties": {
    "columnName": "foo",
    "columnType": "VARCHAR(30)"
  }
}
```

An attribute corresponds to a column of a Postgres table.

Use this schema when the `datastore` id on the model to which this attribute belongs refers to a datastore that uses the
`postgres` protocol.

* #### **`columnName` (string) [required]**

    **Manifest path: `$.models[*].attributes[*].properties.columnName`**

    Name of the Postgres column that the attribute corresponds to.
    
    While creating tables in Postgres for Postgres bound models in the manifest,
    Dore infers the required column name from this field's value.

* #### **`columnType` (string) [required]**

    **Manifest path: `$.models[*].attributes[*].properties.columnType`**

    Data type of the Postgres column that the attribute corresponds to.
    
    All 
    <a target="_blank" href="https://www.postgresql.org/docs/current/datatype.html">
    data types supported by Postgres
    </a> 
    are supported here.