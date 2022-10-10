# Multi-File Manifest

If we were to define all the models in a single Manifest like we have done so far, we can see how the manifest 
will soon become large and unreadable for larger schemas.

To overcome this, Dore allows you to split the manifest across multiple files. 

Each **Model**, **Datastore**, and **Attribute** definition can be stored in a different file. Typically, you would 
want to move each Model and Datastore definition to a separate file. You can choose to move attributes to 
separate files as well in case the model file itself starts getting large and unreadable.

Let's move the `ecommerce` datastore definition and the `customer` and `order` model definitions different files. The 
contents of these 
files are shown below.
<br>
<br>

### Ecommerce datastore

Let's move the `ecommerce` datastore definition, i.e, everything at `$.datastores['ecommerce']`, in our manifest to 
a new 
file 
`ecommerce-datastore.json`.

```shell title="ecommerce-datastore.json"
{
  "protocol": "mysql",
  "properties": { 
    "database": "Dore_Ecommerce",
    "host": "127.0.0.1",
    "port": "3306",
    "user": "{{mysql-user}}",
    "password": "{{mysql-password}}"
  }
}
```
<br>

### Customer model

Similarly, let's move the `customer` model definition, i.e, everything at `$.models['customer']`, in our manifest to a 
new file `customer-model.json`.

```shell title="customer-model.json"
{
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
}
```

### Order model

Next, let's move the `order` model definition, i.e, everything at `$.models['order']`, to a new file 
`order-model.json`

```shell title="order-model.json"
{
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
```

### Adding file references in Manifest

Finally, let's add references to the files above in our manifest. The new manifest should look like the one shown below:

```json linenums="1" title="dore-ecommerce-manifest.json" hl_lines="5 10 13"
{
  "id": "ecommerce-example",
  "datastores": {
    "ecommerce": {
      "ref": "/abs/path/to/ecommerce-datastore.json"
    }
  },
  "models": {
    "customer": {
      "ref": "/abs/path/to/customer-model.json"
    },
    "order": {
      "ref": "/abs/path/to/order-model.json"
    }
  }
}
```

## Invoke Dore

Let's invoke Dore in the same way as we did previously with the manifest above to ensure everything is working as 
expected:

```shell
dore --manifest /abs/path/to/ecommerce-dore-manifest.json \
  --mysql-user=root \
  --mysql-password=password \
  --drop-conflicting-models
```

We should be able to see a successful run again.

<hr>

[➡ **Next**: Conclusion](/tutorial/conclusion/){.md-button}

<hr>

