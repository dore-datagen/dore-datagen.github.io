## Overview

Dore generates fake data for models of schemas by generating fake data for each of its attributes and combining them
to form records.

In order for Dore to generate value for an attribute, we need to configure details in the attribute using the
`value` object which defines how Dore generates value for it.

The **Value Definition** of an attribute should specify an
[**Attribute Value Generator**](/manifest/attributes/attribute_definition/#value-object-required), along with any parameters that it might
need, that Dore will use to generate values for the attribute.

Let's define value configs for each of the attributes we created in the previous section.

<br>
<hr>

## Customer Model

This section contains details of value definitions for attributes of the `customer` model.

### `customerId`

Since each customer ID needs to be a unique string, we can use `UUID` values for the `customer_id` column.

Dore supports various
[**Attribute Value Generators**](/manifest/attributes/attribute_definition#value-object-required)
that you can use to define how value for a particular attribute should to be generated.

In order to generate `UUID` values, we can use the
[**Faker Value Generator**](/manifest/attributes/value_generator_faker/). Let's provide the `value` definition
for `customerId` attribute to indicate that Dore should generate `UUID` values for this
column using the Faker Value Generator:

```json  linenums="1" title="dore-ecommerce-manifest.json" hl_lines="21 22 23 24 25"
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
        "customerId": {
          "value": {
            "faker": {
              "uuid4": {}
            }
          }
        },
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
<br>
<hr>

### `customerName`

For generating random names, we can use the [**Faker Value Generator**](/manifest/attributes/value_generator_faker/)
again and use the `name` method. Let's add the value definition for `customerName` attribute to our manifest:

```json  linenums="1" title="dore-ecommerce-manifest.json" hl_lines="28 29 30 31 32"
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
        "customerId": {
          "value": {
            "faker": {
              "uuid4": {}
            }
          }
        },
        "customerName": {
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
      "attributes": {
        "orderId": {},
        "customerId": {},
        "orderDate": {}
      }
    }
  }
}
```

<br>
<hr>

## Order Model

This section contains details of value definitions for attributes of the `order` model.

### `orderId`

The **Order ID**, similar to a **Customer ID**, uniquely defines an Oder. We can use `UUID` values for the
`order_id` column.

```json linenums="1" title="dore-ecommerce-manifest.json" hl_lines="41 42 43 44 45"
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
        "customerId": {
          "value": {
            "faker": {
              "uuid4": {}
            }
          }
        },
        "customerName": {
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
      "attributes": {
        "orderId": {
          "value": {
            "faker": {
              "uuid4": {}
            }
          }
        },
        "customerId": {},
        "orderDate": {}
      }
    }
  }
}
```
<br>

### `customerId`

Based on the [ecommerce schema]((/tutorial/ecommerce_schema)), The `customer_id` column of the **Order** table is a
Foreign Key which references the `customer_id` column of the **Customer** table.

You can use the [**Ref Value Generator**](/manifest/attributes/value_generator_ref/) to define that Dore should
generate values for an attribute by deriving its values of from values of another attribute. Such attributes are also
known as **Dependent Attributes**.

Since the value of `order.customerId` attribute is dependent on `customer.customerId` attribute, we can add value
definition for `order.customerId` as follows:

```json linenums="1" title="dore-ecommerce-manifest.json" hl_lines="48 49 50"
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
        "customerId": {
          "value": {
            "faker": {
              "uuid4": {}
            }
          }
        },
        "customerName": {
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
      "attributes": {
        "orderId": {
          "value": {
            "faker": {
              "uuid4": {}
            }
          }
        },
        "customerId": {
          "value": {
            "ref": "customer.customerId"
          }
        },
        "orderDate": {}
      }
    }
  }
}
```
<br>

### `orderDate`

For generating random dates, we can use the [**Faker Value Generator**](/manifest/attributes/value_generator_faker/)
again and use the [`date_between`](https://faker.readthedocs.io/en/master/providers/faker.providers.date_time.html#faker.providers.date_time.Provider.date_between)
method:

```json linenums="1" title="dore-ecommerce-manifest.json" hl_lines="53 54 55 56 57 58 59"
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
        "customerId": {
          "value": {
            "faker": {
              "uuid4": {}
            }
          }
        },
        "customerName": {
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
      "attributes": {
        "orderId": {
          "value": {
            "faker": {
              "uuid4": {}
            }
          }
        },
        "customerId": {
          "value": {
            "ref": "customer.customerId"
          }
        },
        "orderDate": {
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

We have defined the value config for `orderDate` attribute to be a random date in the last year

<hr>

[➡ **Next**: Protocol specific properties](/tutorial/model_and_attribute_properties/){.md-button}

<hr>
