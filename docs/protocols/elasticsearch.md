# Dore Elasticsearch Protocol

<hr>

**Protocol name: `elasticsearch7`, `elasticsearch8`**

<hr>

## Manifest fields

| Field in Manifest | What it represents |
|-------------------|--------------------|
| Datastore         | Cluster            |
| Model             | Index              |
| Attribute         | Field              |

<br>
<hr>

## Datastore Properties

** Manifest path: `$.datastores[*].properties`**

### Example

```json title="Elasticsearch Datastore properties example" linenums="1"
{
  "host": "127.0.0.1",
  "port": "9001",
  "user": "john_doe",
  "password": "yourpassword"
}
```

### Fields

* ####`host` (string) [required]

    **Manifest path: `$.datastores[*].properties.host`**

    Elasticsearch host.

* ####`port` (string) [required]

    **Manifest path: `$.datastores[*].properties.port`**

    Elasticsearch port.

* ####`user` (string) [required]

    **Manifest path: `$.datastores[*].properties.user`**

    Elasticsearch username for connecting to the database.

* ####`password` (string) [required]

    **Manifest path: `$.datastores[*].properties.password`**

    Elasticsearch password for connecting to the database.
  
<br>
<hr>

## Model Properties

** Manifest path: `$.models[*].properties` **

### Example

```json title="Elasticsearch Model properties example" linenums="1"
{
  "indexName": "foobar"
}
```


### Fields

* ####`indexName` (string) [required]

    **Manifest path: `$.models[*].properties.indexName`**

    Name of the Elasticsearch *index* that the model corresponds to.

    While interacting with the Elasticsearch indexes corresponding to the model, Dore uses this `schemaName`
    to refer to the schema in the Elasticsearch database.
  
<br>
<hr>
  
## Attribute Properties

** Manifest path: `$.models[*].attributes[*].properties` **

### Example

```json title="Elasticsearch Attribute properties example" linenums="1"
{
  "fieldName": "foo",
  "fieldType": "keyword"
}
```

### Fields
 
* ####`fieldName` (string) [required]

    **Manifest path: `$.models[*].attributes[*].properties.fieldName`**

    Name of the Elasticsearch field that the attribute corresponds to.

* ####`fieldType` (string) [required]

    **Manifest path: `$.models[*].attributes[*].properties.fieldType`**

    Name of the Elasticsearch field that the attribute corresponds to.

    All 
    <a target="_blank" href="https://www.elastic.co/guide/en/elasticsearch/reference/current/mapping-types.html">
    field data types supported by Elasticsearch
    </a> 
    are supported here.