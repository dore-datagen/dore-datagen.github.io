# Create Manifest

Manifests have the following structure:

```json title="General structure of a Dore manifest" linenums="1"
{
  "id": "manifest ID",
  "datastores": {
    // ... datastore definitions ...
  },  
  "models": {
    "a_model": {
      "attributes": {
        // ... attribute definitions ...
      }
    },
    
    // ... other model definitions ...
  }
}
```

Take a moment to look at the fields mentioned in the manifest above.
You would notice three main things:

* `datastores` (line 3)
* `models` (line 6)
  * `attributes` (line 8)

Although Dore supports generating and persisting data for multiple protocols, we shall keep our vocabulary specific to
MySQL for the purposes of this example. 

`models` correspond to tables, its `attributes` correspond to the table's columns, and `datastores` correspond 
to databases.

An example of Dore Manifest required to generate data for the Ecommerce schema above is shown below. Please refer
the [Explanation](./example_manifest_explained.md) section provided after the manifest to view details on the contents of the manifest.

```json title="ecommerce-dore-manifest.json" linenums="1"
{
  "id": "ecommerce-dore-manifest",   
  "datastores": {
    "ecommerce": {
      "protocol": "mysql",
      "properties": { 
        "database": "Ecommerce",
        "host": "127.0.0.1",
        "port": "3306",
        "user": "root",
        "password": "password"
      }
    }
  },
  "models": {
    "customer": {
      "records": 100,
      "datastore": "ecommerce",
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
      "records": 1000,
      "datastore": "ecommerce",
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
            "columnName": "customer",
            "columnType": "CHAR(50)"
          },
          "value": {
            "ref": "customer.customerId"
          }
        },
        "orderDate": {
          "properties": {
            "columnName": "order_date",
            "columnType": "date"
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
