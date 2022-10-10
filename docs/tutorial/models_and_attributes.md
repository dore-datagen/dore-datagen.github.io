# Models and Attributes

Now that we have configured details for the `Dore_Ecommerce` database, we need to provide definitions for the
`Customer` and `Order` tables of the [e-commerce schema](/tutorial/ecommerce_schema/).

In Dore, A [**Model**](/manifest/models/models/) represents a set of structured data. Models usually correspond to
tables/collections/indexes in a database/cluster.
[**Attributes**](/manifest/attributes/attributes/) correspond to columns/fields.

Let's add the `models` object in the manifest which will contain the model definitions:

```json linenums="1" title="dore-ecommerce-manifest.json" hl_lines="15"
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
  },
  "models": {}
}
```

We will be adding definitions for each of the tables of the [ecommerce schema](/tutorial/ecommerce_schema/).

## Models

Like datastores, each model is defined with a key which will be the ID for the Model and
value as the [Model Definition](/manifest/models/model_definition/).

Let's add two models, `customer` and `order`, corresponding to `Customer` and `Order` tables of the
[ecommerce schema](/tutorial/ecommerce_schema/):

```json linenums="1" title="dore-ecommerce-manifest.json" hl_lines="16 17"
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
  },
  "models": {
    "customer": {},
    "order": {}
  }
}
```

### Linked Datastore

Since `Customer` and `Order` tables need to be created within the `Dore_Ecommerce` database, we define that both
`customer` and `order` models are associated with the `ecommerce` datastore:

```json linenums="1" title="dore-ecommerce-manifest.json" hl_lines="17 20"
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
  },
  "models": {
    "customer": {
      "datastore": "ecommerce"
    },
    "order": {
      "datastore": "ecommerce"
    }
  }
}
```

### Records

We need to define the count of records that Dore should generate for each of the models. So let's define this for
the `customer` and `order` models as follows:

```json linenums="1" title="dore-ecommerce-manifest.json" hl_lines="18 22"
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
  },
  "models": {
    "customer": {
      "datastore": "ecommerce",
      "records": 10
    },
    "order": {
      "datastore": "ecommerce",
      "records": 100
    }
  }
}
```

With the `records` field on the models, we have defined that Dore should generate **10** records for the `customer`
model and **100** records for the `order` model.

## Attributes

The **Customer** table of the [e-commerce schema](/tutorial/ecommerce_schema) has two columns:

* `customer_id`
* `customer_name`

And the **Order** table has three columns:

* `order_id`
* `customer_id`
* `order_date`

In order to add definitions for these columns in the manifest, we need to define
[**Attributes**](/manifest/attributes/attributes/) for the `customer` and `order` models corresponding to these
columns.

Attributes for a model are defined at `$.models[*].attributes` in the Manifest; i.e, within the `attributes` field for
a model. Like datastores and models, each attribute is defined with a key which will be the ID for the Attribute and
value as the [**Attribute Definition**](/manifest/attributes/attributes/).

```json linenums="1" title="dore-ecommerce-manifest.json" hl_lines="19 20 21 22 27 28 29 30 31"
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
  },
  "models": {
    "customer": {
      "datastore": "ecommerce",
      "records": 10,
      "attributes": {
        "customerId": {},
        "customerName": {}
      }
    },
    "order": {
      "datastore": "ecommerce",
      "records": 100,
      "attributes": {
        "orderId": {},
        "customerId": {},
        "orderDate": {}
      }
    }
  }
}
```

We will be now be adding value definitions for the attributes above.

<hr>

[ ➡ Next: Attribute Value Definition](/tutorial/attribute_value_definition/){.md-button}

<hr>
