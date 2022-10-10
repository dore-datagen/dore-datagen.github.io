# Defining the E-Commerce Datastore

Since all tables of the [ecommerce schema](/tutorial/ecommerce_schema/) are present in an `Dore_Ecommerce` database, we 
need a way to define details of the MySQL database in the Manifest.

## Datastores

In Dore, [**Datastores**](/manifest/datastores/datastores/) represent data sources. It usually represents a 
particular database, whether that's a database running within a locally installed MySQL server, a remote 
Elasticsearch cluster, or a hosted MongoDB database.

Let's add the `datastores` object in the manifest:

```json linenums="1" title="dore-ecommerce-manifest.json" hl_lines="3"
{
  "id": "ecommerce-example",
  "datastores": {}
}
```

This will contain definition for the `Dore_Ecommerce` MySQL database.

## Defining the `ecommerce` Datastore

Datastores are configured at `$.datastores` in the Manifest, i.e, inside the `datastores` object we added above.  Each
datastore is defined with a key which will be the ID for the Datastore and value as the 
[Datastore Definition](/manifest/datastores/datastore_definition/).

Let's add the `ecommerce` datastore to our Manifest:

```json linenums="1" title="dore-ecommerce-manifest.json" hl_lines="4"
{
  "id": "ecommerce-example",
  "datastores": {
    "ecommerce": {}
  }
}
```

In the snippet above, we have defined a datastore with ID `ecommerce`. We will add the definition for 
`Dore_Ecommerce` database within this object. 

### Protocol

Each datastore must specify a [`protocol`](/manifest/datastores/datastore_definition/#protocol-string-required) which 
indicates the type of system the datastore represents. In our case, the datastore represents a `mysql` database. 
Let's specify that `ecommerce` datastore uses `mysql` protocol:

```json linenums="1" title="dore-ecommerce-manifest.json" hl_lines="5"
{
  "id": "ecommerce-example",
  "datastores": {
    "ecommerce": {
      "protocol": "mysql"
    }
  }
}
```

### Properties

We also need to define certain [*protocol specific properties*](/manifest/datastores/datastore_definition/#properties-object-required) 
for a datastore which allows Dore to interact with the underlying system:

```json linenums="1" title="dore-ecommerce-manifest.json" hl_lines="6 7 8 9 10 11 12"
{
  "id": "ecommerce-example",
  "datastores": {
    "ecommerce": {
      "protocol": "mysql",
      "properties": {
        "database": "Dore_Ecommerce",
        "host": "127.0.0.1",
        "port": "3306",
        "user": "root",
        "password": "password"
      }    
    }
  }
}
```

These properties specify details which Dore uses to identify, connect, and interact with the `Dore_Ecommerce` MySQL 
database represented by the Datastore.

Please provide details for your MySQL instance for the `host`, `port`, `user`, and `password` fields above.

<hr>

[ ➡ Next: Models and Attributes](/tutorial/models_and_attributes/){.md-button}

<hr>
