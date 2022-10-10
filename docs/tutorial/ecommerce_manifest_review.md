# Ecommerce Manifest Review

Let's do a quick review of what we have done so far:

* We started off by learning about the Ecommerce schema, its tables, and the relationships amongst them.

    [[ref: The Ecommerce schema ↗]](/tutorial/ecommerce_schema/)
  <br><br>

* Then, we learnt that in order to generate data for any schema with Dore we need to create a **Manifest**
  for the schema which defines requirements of the target data.

    [[ref: Dore Manifest ↗]](/tutorial/dore_manifest/)
  <br><br>

* We then proceeded with creating the Manifest and providing the Manifest with an ID.

    [[ref: Creating the Manifest ↗]](/tutorial/create_manifest/)
  <br><br>

* Next, we learnt about **Datastores** and we defined the `ecommerce` Datastore, which defines details for the
  **Dore_Ecommerce MySQL database** in the Manifest.

    [[ref: Datastore ↗]](/tutorial/ecommerce_datastore/)
  <br><br>

* Then, we learnt about **Models** and **Attributes**. We defined the `customer` and `order` Models and their
  Attributes.

    [[ref: Models and Attributes ↗]](/tutorial/models_and_attributes/)
  <br><br>

* We then learnt about **Attribute Value Definitions** and defined how Dore should generate values for each of the
  attributes of the `customer` and `order` models.

    [[ref: Models and Attributes ↗]](/tutorial/value_config/)
  <br><br>

* Finally, we learn about **Protocol specific properties** for Models and Attributes and defined protocol specific
  properties for each of the models and their attributes in our Manifest.

    [[ref: Model and Attribute Properties ↗]](/tutorial/model_and_attribute_properties/)
  <br><br>



The following snippet contains the complete ecommerce manifest:

```json linenums="1" title="dore-ecommerce-manifest.json"
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
      "properties": {
        "tableName": "Customer"
      },
      "attributes": {
        "customerId": {
          "properties": {
            "columnName": "customer_id",
            "columnType": "CHAR(50)"
          },
          "value": {
            "faker": {
              "uuid4": {}
            }
          }
        },
        "customerName": {
          "properties": {
            "columnName": "customer_name",
            "columnType": "CHAR(50)"
          },
          "value": {
            "faker": {
              "name": {}
            }
          }
        }
      }
    },
    "order": {
      "datastore": "ecommerce",
      "records": 100,
      "properties": {
        "tableName": "Order"
      },
      "attributes": {
        "orderId": {
          "properties": {
            "columnName": "order_id",
            "columnType": "CHAR(50)"
          },
          "value": {
            "faker": {
              "uuid4": {}
            }
          }
        },
        "customerId": {
          "properties": {
            "columnName": "customer_id",
            "columnType": "CHAR(50)"
          },
          "value": {
            "ref": "customer.customerId"
          }
        },
        "orderDate": {
          "properties": {
            "columnName": "order_date",
            "columnType": "DATE"
          },
          "value": {
            "faker": {
              "date_between": {
                "start_date": "-1y"
              }
            }
          }
        }
      }
    }
  }
}
```



Next, we're going to try invoking **Dore** with the above manifest and verify that we're able to generate data as
per the schema requirements.

<br>
<hr>

[ ➡ Next: Invoke Dore](/tutorial/invoke_dore/){.md-button}

<hr>
