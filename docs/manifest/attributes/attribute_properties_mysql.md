# MySQL Attribute Properties

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

An attribute corresponds to a column of a MySQL table.

Use this schema when the `datastore` id on the model to which this attribute belongs refers to a datastore that uses the
`mysql` protocol.

* #### **`columnName` (string) [required]**

    **Manifest path: `$.models[*].attributes[*].properties.columnName`**

    Name of the MySQL column that the attribute corresponds to.
    
    While creating tables in MySQL for MySQL bound models in the manifest,
    Dore infers the required column name from this field's value.

* #### **`columnType` (string) [required]**

    **Manifest path: `$.models[*].attributes[*].properties.columnType`**

    Data type of the MySQL column that the attribute corresponds to.
    
    All 
    <a target="_blank" href="https://dev.mysql.com/doc/refman/8.0/en/data-types.html">
    data types supported by MySQL
    </a> 
    are supported here.