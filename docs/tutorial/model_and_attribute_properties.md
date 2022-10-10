# Protocol specific properties for Models and Attributes

Similar to how Datastores need to have *protocol specific properties* defined in the manifest so Dore can connect
and interact with the underlying system, Models and Attributes need to have *protocol specific properties*, such as
table names for models, column names and their data types for attributes, defined in the manifest so Dore can
interact with the entities in the underlying system.

Let's add these properties to the Models and Attributes we created in the previous section as shown below:

```json linenums="1" title="dore-ecommerce-manifest.json" hl_lines="19 20 21 24 25 26 27 35 36 37 38 50 51 52 55 56 57 58 66 67 68 69 75 76 77 78"
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

With these additions, we have completed the ecommerce manifest.

<br>
<hr>

[ ➡ Next: Manifest Review](/tutorial/ecommerce_manifest_review/){.md-button}

<hr>
