# Dore MongoDB Protocol

<hr>

**Protocol name: `mongodb`**

<hr>

## Manifest fields

| Field in Manifest | What it represents |
|-------------------|--------------------|
| Datastore         | Database           |
| Model             | Collection         |
| Attribute         | Field              |

<br>
<hr>

## Datastore Properties

** Manifest path: `$.datastores[*].properties`**

### Example

```json title="MongoDB Datastore properties example" linenums="1"
{
  "host": "127.0.0.1",
  "port": "27101",
  "user": "john_doe",
  "password": "yourpassword",
  "database": "foobar"
}
```

### Fields

* ####`host` (string) [required]

    **Manifest path: `$.datastores[*].properties.host`**

    MongoDB host.

* ####`port` (string) [required]

    **Manifest path: `$.datastores[*].properties.port`**

    MongoDB port.

* ####`user` (string) [required]

    **Manifest path: `$.datastores[*].properties.user`**
    
    MongoDB username for connecting to the database.

* ####`password` (string) [required]

    **Manifest path: `$.datastores[*].properties.password`**

    MongoDB password for connecting to the database.

* ####`database` (string) [required]

    **Manifest path: `$.datastores[*].properties.database`**

    Name of the MongoDB database to connect to.
  
<br>
<hr>

## Model Properties

** Manifest path: `$.models[*].properties` **

### Example

```json title="MongoDB Model properties example" linenums="1"
{
  "collectionName": "foobar"
}
```

### Fields

* ####`collectionName` (string) [required]

    **Manifest path: `$.models[*].properties.collectionName`**

    Name of the MongoDB collection that the model corresponds to.

    While interacting with the MongoDB collection corresponding to the model, Dore uses this `collectionName`
    to refer to the model in the MongoDB database.
  
<br>
<hr>
  
## Attribute Properties

** Manifest path: `$.models[*].attributes[*].properties` **

### Example

```json  title="MongoDB Attribute properties example" linenums="1"
{
  "fieldName": "foo"
}
```

### Fields

* #### `fieldName` (string) [required]

    **Manifest path: `$.models[*].attributes[*].properties.fieldName`**

    Name of the MongoDB field that the attribute corresponds to.
