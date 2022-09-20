# MongoDB Datastore Properties

** Manifest path: `$.datastores[*].properties`**

This schema is applicable when `protocol` is `"mongodb"`.

## Example

```json title="MongoDB Datastore properties example"
{
    "properties": {
        "host": "127.0.0.1",
        "port": "27101",
        "user": "john_doe",
        "password": "yourpassword",
        "database": "foobar"
    }
}
```

## Fields

* ###`host` (string) [required]

    **Manifest path: `$.datastores[*].properties.host`**

    MongoDB host.

* ###`port` (string) [required]

    **Manifest path: `$.datastores[*].properties.port`**

    MongoDB port.

* ###`user` (string) [required]

    **Manifest path: `$.datastores[*].properties.user`**
    
    MongoDB username for connecting to the database.

* ###`password` (string) [required]

    **Manifest path: `$.datastores[*].properties.password`**

    MongoDB password for connecting to the database.

* ###`database` (string) [required]

    **Manifest path: `$.datastores[*].properties.database`**

    Name of the MongoDB database to connect to.