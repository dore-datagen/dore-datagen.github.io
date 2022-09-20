# Postgres Datastore properties

** Manifest path: `$.datastores[*].properties`**

This schema is applicable when `protocol` is `"postgres"`.

## Example

```json title="Postgres Datastore properties example"
{
    "properties": {
        "host": "127.0.0.1",
        "port": "5432",
        "user": "john_doe",
        "password": "yourpassword",
        "database": "foobar"
    }
}
```

## Fields

* ###`host` (string) [required]

    **Manifest path: `$.datastores[*].properties.host`**

    PostgreSQL host.

* ###`port` (string) [required]

    **Manifest path: `$.datastores[*].properties.port`**

    PostgreSQL port.

* ###`user` (string) [required]

    **Manifest path: `$.datastores[*].properties.user`**

    PostgreSQL username for connecting to the database.

* ###`password` (string) [required]

    **Manifest path: `$.datastores[*].properties.password`**

    PostgreSQL password for connecting to the database.

* ###`database` (string) [required]

    **Manifest path: `$.datastores[*].properties.database`**

    Name of the PostgreSQL database to connect to.
