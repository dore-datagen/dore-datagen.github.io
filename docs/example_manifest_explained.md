# The E-commerce manifest

The E-Commerce manifest is shown here again for reference. Please scroll past the code snippet below
to view details of fields about the manifest. 

![E-Commerce schema](./assets/dore-example-usage.svg)


```json title="ecommerce-dore-manifest.json" linenums="1"
{
  "id": "ecommerce-dore-manifest",   
  "datastores": {  // (1)
    "ecommerce": {  // (2)
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
  "models": { // (3)
    "customer": {  // (4)
      "records": 100,  // (5)
      "datastore": "ecommerce",  //(6)
      "properties": {  // (7)
        "tableName": "Customer"
      },
      "attributes": {  // (8)
        "customerId": {  // (9)
          "properties": {  // (10)
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

1. **`$.datastores`**<br>
   **Datastores** correspond to databases. All datastores are defined within the `datastores` root object in the manifest
   and each datastore is defined with a key which acts as the datastore ID and can be used to refer to the datastore in 
   other parts of the manifest. <br><br>
   Please refer
   <a href="../manifest/datastores/datastores/" target="_blank">
   Datastores
   </a>
   for more details.
   
2. **`$.datastores.ecommerce`**<br>
   **E-Commerce database definition**<br>
   The `ecommerce` datastore definition. This object contains details for the E-commerce database. <br><br>
   Please refer
   <a href="" target="_blank">
   MySQL datastore
   </a>
   for more details.
   
3. **`$.models`**<br>
   **Models** correspond to tables. All models are defined within the `models` root
   object in the manifest. Each model is defined with with a key which acts as the model ID and value as the model 
   definition. <br>
   Based on the Ecommerce schema diagram, we need to define two models corresponding to the two tables in the schema 
    -- one for `Customer` and the other for `Order`. <br><br>
   Please refer
   <a href="../manifest/models/models" target="_blank">
   Models
   </a>
   for more details.
   
4. **`$.models.customer`**<br>
   **Customer model definition**<br>
   We define a model in the manifest which corresponds to the `Customer` table in the schema diagram.
   
5. **`$.models.customer.records`**<br>
   This specifies how many records should Dore generate for the model.
   
6. **`$.models.customer.datastore`**<br>
   The `datastore` field on a model tells Dore which datastore the model is associated with. <br>
   Based on the schema, both models are associated with the `Ecommerce` database (which is defined 
   in `$.datastores.ecommerce` in this manifest). Thus, we associate the `customer` model with the `ecommerce` 
   datastore.
   
7. **`$.models.customer.properties`**<br>
    MySQL specific properties for the model. <br>
    Please refer [MySQL model properties] for further details.
   
8. **`$.models.customer.attributes`**<br>
    Each model will generally have a set of attributes associated with it. You can think of an attribute as a
    *column* of a MySQL table where the model corresponds to the table. 
   
    A model's attributes are defined within the `attributes` field of the model. 
   
    Like datastores and models, each attribute is defined with a key which acts as the attribute ID and value as the
    attribute definition.
    
   
9. **`$.models.customer.attributes.customerId`**

    Details regarding the `Customer.customer_id` column.

    Please refer [Attributes] for further details.

10. **`$.models.customer.attributes.customerId.properties`**

    **Attribute Properties**

    Protocol
    

Explanations for the Manifest JSON above is provided below. Please click on the sections to view details of the
fields and refer to the manifest above to see how the details tie back to the manifest file.


??? note "[[Line 2]](#__codelineno-3-2) `id`"
    **Manifest ID**

    Although Dore doesn't use this ID, it proves helpful to have an ID to 
    improve readability of the manifest and has thus been kept as a required field of the manifest.
   
??? note "[[Line 3-14]](#__codelineno-3-3) `datastores`"
    **Datastores**

    Datastores correspond to databases. All datastores are defined within 
    the `datastores` root object in the manifest and each datastore is defined with a key which acts as the datastore 
    ID and can be used to refer to the datastore in other parts of the manifest (Ex: datastore reference in models
    at [line 18](#__codelineno-3-18) and [line 49](#__codelineno-3-49)). The value is the datastore definition.

    Based on the Ecommerce schema diagram, we need to define a datastore which will correspond to the Ecommerce
    MySQL database.

    ??? note "[[Line 4-13]](#__codelineno-3-4) `ecommerce`"
        **The `ecommerce` datastore definition**

        Here, we define a datastore with ID `ecommerce` and the definition as provided in [lines 5-11](#__codelineno-3-5)

        ??? note "[[Line 5]](#__codelineno-3-5) `protocol`"
            **Protocol**

            Each datastore definition must specify a **protocol**. Protocols correspond to 
            datastore system implementations. Ex: `mysql`, `mongodb`, `elasticsearch7` are all protocols.

        ??? note "[[Line 7-11]](#__codelineno-3-7) `properties`"
            **Datastore Properties**

            The `properties` object usually contains *protocol specific* properties for entities 
            in the manifest.
        
            You will notice the presence of the protocol specific `properties` object for `models` and `attributes` in 
            the manifest
            as well.
            
            For the MySQL database represented by the `ecommerce` datastore, we provide `mysql` specific `properties` 
            such as `database` name, `host`, `port`, etc.


??? note "[[Line 15-90]](#__codelineno-3-15) `models`"
    **Models**

    *Models* correspond to tables. All models are defined within the `models` root
    object in the manifest. Each model is defined with with a key which acts as the model ID and can be used to refer
    to the model in other parts of the manifest (Ex: `model.attribute` reference at [line 71](#__codelineno-3-71)). 
    The value is the model definition.
    
    Based on the Ecommerce schema diagram, we need to define two models corresponding to the two tables in the schema 
    -- one for `Customer` and the other for `Order`.

    Each model has a set of **attributes** associated with it. You can think of attributes as columns of a table where the
    table represents the model.

    ??? note "[[Line 15-90]](#__codelineno-3-15) `customer`"

        **The `customer` model**

        We define a model in the manifest which corresponds to the `Customer` table in the schema diagram. The following
        details need to be provided for a model:

        ??? note "[[Line 17]](#__codelineno-3-17) `records`"

            **Records**
    
            The value in this field specifies the count of records to be generated for the model. The actual count of 
            records generated might vary based on the `--scale-factor` provided during invocation. 

            In the manifest, we specify that Dore should generate 100 rows for the `Customer` table.

        ??? note "[[Line 18]](#__codelineno-3-17) `datastore`"

            **Datastore**

            This field determines which datastore the model belongs to.

            We specify that the `customer` model belongs to the `ecommerce` datastore defined in 
            [line 4](#__codelineno-3-4)

        ??? note "[[Line 19-21]](#__codelineno-3-19) `properties`"

            **Model Properties**

            Similar to the `properties` field for a datastore ([line 6](#__codelineno-3-6)), we use the `properties` 
            field in a model to specify *protocol specific* properties for the model.

            In this example, we use this field to specify the name of the MySQL table that the model corresponds to
            using the `tableName` property.

        ??? note "[[Line 22-45]](#__codelineno-3-22) `attributes`"

            **Attributes**

            Each model will generally have a set of attributes associated with it. You can think of an attribute as a
            *column* of a MySQL table where the model corresponds to the table.

            A model's attributes are defined within the `attributes` field of the model. 

            Like datastores and models, each attribute is defined with a key which acts as the attribute ID and can 
            be used to refer to the attribute in other parts of the manifest (Ex: `model.attribute` reference at 
            [line 71](#__codelineno-3-71). The value is the attribute definition.

            Each attribute definition usually comprises of two parts:

            1. `value`: which specifies how Dore should generate values for this attribute.

            2. `properties`: which specify the *protocol specific* properties for the attribute. For ex: the MySQL
            column name and data type.

            Dore generates fake data for tables / models by repeatedly generating fake values for each column / 
            attribute and combining them to form rows. The value generation is *protocol agnostic*, i.e, it
            does not vary across protocols.

            ??? note "[[Line 23-33]](#__codelineno-3-23) `customerId`"

                **The `customerId` attribute**

                This attribute corresponds to the `customer_id` column in the Ecommerce schema.

                ??? note "[[Line 24-27]](#__codelineno-3-24) `properties`"

                    **Attribute Properties**

                    Similar to the `properties` field for a datastore ([line 6](#__codelineno-3-6)) or a model 
                    ([line 19](#__codelineno-3-6)), we use the `properties` field of an attribute to specify 
                    *protocol specific* properties for the attribute. 

                    For MySQL, where attributes represent MySQL columns, we specify the `columnName` and `columnType` 
                    to specify the name of the MySQL column and the data type for the column.

                    Name of the MySQL column is `customer_id` and the data type for the column is `CHAR(50)`

                ??? note "[[Line 28-32]](#__codelineno-3-28) `value`"

                    **Attribute Value**

                    The `value` config on an attribute specifices how Dore should generate fake values for the 
                    attribute.

                    Dore supports various value generators that you can use to generate values for attributes.

                    Since the `customer_id` column is a primary key on the customer table, we want to 
                    generate unique values for each customer we create. 

                    We thus use Python Faker library's [`uuid4`](https://faker.readthedocs.io/en/master/providers/faker.providers.misc.html#faker.providers.misc.Provider.uuid4) method to generate UUID strings as
                    values for `customer_id` column.

            ??? note "[[Line 34-44]](#__codelineno-3-23) `customerName`"

                **The `customerName` attribute**

                This attribute corresponds to the `customer_name` column in the Ecommerce schema.

                ??? note "[[Line 35-38]](#__codelineno-3-24) `properties`"

                    **Attribute Properties**

                    Similar to the `properties` field for a datastore ([line 6](#__codelineno-3-6)) or a model 
                    ([line 19](#__codelineno-3-6)), we use the `properties` field of an attribute to specify 
                    *protocol specific* properties for the attribute. 

                    For MySQL, where attributes represent MySQL columns, we specify the `columnName` and `columnType` 
                    to specify the name of the MySQL column and the data type for the column.

                ??? note "[[Line 28-32]](#__codelineno-3-28) `value`"

                    **Attribute Value**

                    The `value` config on an attribute specifices how Dore should generate fake values for the 
                    attribute.

                    Dore supports various value generators that you can use to generate values for attributes.

                    Here, we use Python Faker library's [`name`](https://faker.readthedocs.io/en/master/providers/faker.providers.person.html#faker.providers.person.Provider.name) method to generate randon name strings as
                    values for `customer_name` column.

    ??? note "[[Line 47-88](#__codelineno-3-47)] `order`"

        **The `order` model**

        We define a model in the manifest which corresponds to the `Order` table in the schema diagram. Details of 
        the fields are similar to the ones in the `customer` model so we will be highlighting only the differences here.

        ??? note "[[Line 17]](#__codelineno-3-17) `records`"

            **Records**

            1000 rows should be generated for the `Order` table.

        ??? note "[[Line 18]](#__codelineno-3-17) `datastore`"

            **Datastore**

            The model belongs to the `ecommerce` datastore.

        ??? note "[[Line 19-21]](#__codelineno-3-19) `properties`"

            **Model Properties**

            The MySQL table should be named `Order`.
                
        ??? note "[[Line 22-45]](#__codelineno-3-22) `attributes`"

            **Attributes**

            ??? note "[[Line 23-33]](#__codelineno-3-23) `orderId`"

                **The `orderId` attribute**

                This attribute corresponds to the `order_id` column in the Ecommerce schema.

                ??? note "[[Line 24-27]](#__codelineno-3-24) `properties`"

                    **Attribute Properties**

                    Name of the MySQL column is `order_id` and the data type for the column is `CHAR(50)` 

                ??? note "[[Line 28-32]](#__codelineno-3-28) `value`"

                    **Attribute Value**

                    Use Python Faker library's [`uuid4`](https://faker.readthedocs.io/en/master/providers/faker.providers.misc.html#faker.providers.misc.Provider.uuid4) method to generate UUID strings as
                    values for `order_id` column.

            ??? note "[[Line 34-44]](#__codelineno-3-23) `customerId`"

                **The `customerId` attribute**

                This attribute corresponds to the `customer_id` column *of the Order table* in the Ecommerce schema.

                ??? note "[[Line 35-38]](#__codelineno-3-24) `properties`"

                    **Attribute Properties**

                    Name of the MySQL column is `customer_id` and the data type for the column is `CHAR(50)` 

                ??? note "[[Line 28-32]](#__codelineno-3-28) `value`"

                    **Attribute Value**

                    Since each order is associated with a customer (which is expressed by the FK relation in the 
                    schema diagram), the `customer_id` values of the Order table should be one of the `customer_id` 
                    values from the `Customer` table.

                    We can use Dore's `ref` value generator for this which accepts a string of the form 
                    `"model.attribute"`. 

                    This uses values of the `"attribute"` of `"model"` (provided in the ref string) as values for the 
                    attribute which uses the `ref` value generator.

            ??? note "[[Line 34-44]](#__codelineno-3-23) `orderDate`"

                **The `orderDate` attribute**

                This attribute corresponds to the `order_date` column of the Order table in the Ecommerce schema.

                ??? note "[[Line 35-38]](#__codelineno-3-24) `properties`"

                    **Attribute Properties**

                    Name of the MySQL column is `order_date` and the data type for the column is `DATE` 

                ??? note "[[Line 28-32]](#__codelineno-3-28) `value`"

                    **Attribute Value**

                    We use Python Faker library's [`date_between`](https://faker.readthedocs.io/en/master/providers/faker.providers.date_time.html#faker.providers.date_time.Provider.date_between)
                    method to use a random between today and the same day previous year as values for `order_date` column.
