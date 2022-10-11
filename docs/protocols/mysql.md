# Dore MySQL Protocol

<hr>

**Protocol name: `mysql`**

<hr>

## Manifest fields

| Field in Manifest | What it represents |
|-------------------|--------------------|
| Datastore         | Database           |
| Model             | Table              |
| Attribute         | Column             |

<br>
<hr>

## Datastore Properties

** Manifest path: `$.datastores[*].properties`**

### Example

```json title="MySQL Datastore properties example" linenums="1"
{
  "host": "127.0.0.1",
  "port": "3306",
  "user": "john_doe",
  "password": "yourpassword",
  "database": "foobar"
}
```

### Fields

* ####`host` (string) [required]

    **Manifest path: `$.datastores[*].properties.host`**

    MySQL host.

* ####`port` (string) [required]

    **Manifest path: `$.datastores[*].properties.port`**

    MySQL port.

* ####`user` (string) [required]

    **Manifest path: `$.datastores[*].properties.user`**
    
    MySQL username for connecting to the database.

* ####`password` (string) [required]

    **Manifest path: `$.datastores[*].properties.password`**

    MySQL password for connecting to the database.

* ####`database` (string) [required]

    **Manifest path: `$.datastores[*].properties.database`**

    Name of the MySQL database to connect to.

<br>
<hr>

## Model Properties

** Manifest path: `$.models[*].properties` **

### Example

```json title="MySQL Model properties example" linenums="1"
{
  "tableName": "foobar"
}
```

### Fields

* ####`tableName` (string) [required]

    **Manifest path: `$.models[*].properties.tableName`**

    Name of the MySQL table that the model corresponds to.

    While interacting with the MySQL table corresponding to the model, Dore uses this `tableName`
    to refer to the model in the MySQL database.
  
<br>
<hr>
  
## Attribute Properties

** Manifest path: `$.models[*].attributes[*].properties` **

### Example

```json title="MySQL Attribute properties example" linenums="1"
{
  "columnName": "foo", 
  "columnType": "VARCHAR(30)"
}
```

### Fields

* #### `columnName` (string) [required]

    **Manifest path: `$.models[*].attributes[*].properties.columnName`**

    Name of the MySQL column that the attribute corresponds to.
    
    While creating tables in MySQL for MySQL bound models in the manifest,
    Dore infers the required column name from this field's value.

* #### `columnType` (string) [required]

    **Manifest path: `$.models[*].attributes[*].properties.columnType`**

    Data type of the MySQL column that the attribute corresponds to.
    
    All 
    <a target="_blank" href="https://dev.mysql.com/doc/refman/8.0/en/data-types.html">
    data types supported by MySQL
    </a> 
    are supported here.