# MySQL Datastore Properties

** Manifest path: `$.datastores[*].properties`**

This schema is applicable when `protocol` is `"mysql"`.

## Example

```json title="MySQL Datastore properties example"
{
    "properties": {
        "host": "127.0.0.1",
        "port": "3306",
        "user": "john_doe",
        "password": "yourpassword",
        "database": "foobar"
    }
}
```

## Fields

* ###`host` (string) [required]

    **Manifest path: `$.datastores[*].properties.host`**

    MySQL host.

* ###`port` (string) [required]

    **Manifest path: `$.datastores[*].properties.port`**

    MySQL port.

* ###`user` (string) [required]

    **Manifest path: `$.datastores[*].properties.user`**
    
    MySQL username for connecting to the database.

* ###`password` (string) [required]

    **Manifest path: `$.datastores[*].properties.password`**

    MySQL password for connecting to the database.

* ###`database` (string) [required]

    **Manifest path: `$.datastores[*].properties.database`**

    Name of the MySQL database to connect to.
