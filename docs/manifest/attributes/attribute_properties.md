# Attribute Properties

* #### `properties` (object)

**Manifest path: `$.models[*].attributes[*].properties`**

This config is used to specify protocol specific attribute properties such as *column name* and *data type* for a 
MySQL column, *field name* and *field type* for an elasticsearch index, and so on.

Dore uses this config for creating models and querying them in the underlying
datastore.

Note that attribute `properties` are a required field only when the model associated with the attribute
needs to be persisted, i.e, has `"FULL"` `persistence`. The protocol applicable on an attribute is
the protocol which the *datastore* linked to the model associated with the attribute is using.

Since each protocol has different requirements for configuring an attribute,
this config varies from one protocol to the other. Please refer to the protocol specific sections below for further 
details.

* [MySQL attribute properties](./attribute_properties_mysql.md)
* [Postgres attribute properties](./attribute_properties_postgres.md)
* [MongoDB attribute properties](./attribute_properties_mongodb.md)
* [Elasticsearch attribute properties](./attribute_properties_elasticsearch.md)