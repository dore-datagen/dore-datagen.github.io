# Elasticsearch Datastore Properties

** Manifest path: `$.datastores[*].properties`**

This schema is applicable when `protocol` is `"elasticsearch7"` or `"elasticsearch8"`.

## Example

```json title="Elasticsearch Datastore properties example"
{
    "properties": {
        "host": "127.0.0.1",
        "port": "9001",
        "user": "john_doe",
        "password": "yourpassword"
    }
}
```

## Fields

* ###`host` (string) [required]

    **Manifest path: `$.datastores[*].properties.host`**

    Elasticsearch host.

* ###`port` (string) [required]

    **Manifest path: `$.datastores[*].properties.port`**

    Elasticsearch port.

* ###`user` (string) [required]

    **Manifest path: `$.datastores[*].properties.user`**

    Elasticsearch username for connecting to the database.

* ###`password` (string) [required]

    **Manifest path: `$.datastores[*].properties.password`**

    Elasticsearch password for connecting to the database.