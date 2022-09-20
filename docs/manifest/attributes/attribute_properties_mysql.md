# MySQL Attribute Properties

** Manifest path: `$.models[*].attributes[*].properties` **

This schema is applicable when the model associated with the attribute is linked to a datastore with  `protocol` set 
as `"mysql"`.

## Example

```json title="MySQL Attribute properties example"
{
  "properties": {
    "columnName": "foo", 
    "columnType": "VARCHAR(30)"
  }
}
```

## Fields

* ### `columnName` (string) [required]

    **Manifest path: `$.models[*].attributes[*].properties.columnName`**

    Name of the MySQL column that the attribute corresponds to.
    
    While creating tables in MySQL for MySQL bound models in the manifest,
    Dore infers the required column name from this field's value.

* ### `columnType` (string) [required]

    **Manifest path: `$.models[*].attributes[*].properties.columnType`**

    Data type of the MySQL column that the attribute corresponds to.
    
    All 
    <a target="_blank" href="https://dev.mysql.com/doc/refman/8.0/en/data-types.html">
    data types supported by MySQL
    </a> 
    are supported here.
