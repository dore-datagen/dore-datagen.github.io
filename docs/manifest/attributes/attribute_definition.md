# Attribute Definition

**Manifest path: `$.models[*].attributes[*]`**

You can think of an attribute as a **MySQL column**, an **Elasticsearch Field**, etc.

An attribute definition needs to specify details about how Dore should generate values for it and also certain 
*protocol specific* `properties` for the attribute.

## Example

```json title="Attribute Definition example"

{
    "another_attribute": {
        "properties": {
            "columnName": "another_attribute_column",
            "columnType": "DATE"
        },
        "value": {
            "faker": {
                "date_between": {
                    "start_date": "2021-01-01",
                    "end_date": "2022-01-01"
                }
            }
        }
    }
}


```

## Fields

* ### `value` (object) [required]

    **Manifest path: `$.models[*].attributes[*].value`**
    
    This config is used to specify how Dore should generate values for the attribute.

    There are various attribute value generators that you can use to do things such as *generate
    date between a given range*, or *select a value at random from a predefined list of values*, etc.
  
    Please refer the value generators below for details:

    * [Faker](./value_generator_faker.md)
    * [Selector](./value_generator_selector.md)
    * [Ref](./value_generator_ref.md)
    * [Composite](./value_generator_composite.md)

* ### `properties` (object)

    **Manifest path: `$.models[*].attributes[*].properties`**

    This config is used to specify protocol specific properties for the attribute.
    
    Protocol specific properties of an attribute are required only when there is a need to persist the model associated 
    with it and its records in any datastore. That is, the model is linked to a datastore and `persistence` on the model is 
    set to `"FULL"` or is not explicitly mentioned in the manifest (as the Dore assumes the default `persistence` as 
    `"FULL"` if it is not specified).
    
    Since each protocol has different requirements for configuring an attribute, this config varies from one protocol to 
    the other. Please refer the protocol specific sections below for details:
  
    * [MySQL Attribute properties](./attribute_properties_mysql.md)
    * [Postgres Attribute properties](./attribute_properties_postgres.md)
    * [MongoDB Attribute properties](./attribute_properties_mongodb.md)
    * [Elasticsearch Attribute properties](./attribute_properties_elasticsearch.md)
    