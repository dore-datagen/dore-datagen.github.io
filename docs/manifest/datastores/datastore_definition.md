# Datastore Definition

**Manifest path: `$.datastores[*]`**

You can think of a datastore as a **MySQL database**, an **Elasticsearch Cluster**, etc.

A datastore definition needs to specify which `protocol` the datastore uses (for ex: `"mysql"`) and certain *protocol
specific `properties`* of the datastore which Dore uses to interact with the underlying system.

## Example

```json title="Datastore Definition example"
{
	"protocol": "mysql",
	"properties": {
		"host": "127.0.0.1",
		"port": "3306",
		"user": "john_doe",
		"password": "yourpassword",
		"database": "foobar"
	}
}
```

## Fields

* ### `protocol` (string) [required]

	**Manifest Path: `$.datastores[*].protocol`**
  
	The protocol / type of system that the datastore represents.

	##### Allowed Values
	* `mysql`
	* `mongodb`
	* `postgres`
	* `elasticsearch7`
	* `elasticsearch8`


* ### `properties` (object) [required]

	**Manifest Path: `$.datastores[*].properties`**

	This config defines protocol specific properties for the datastore.
  
	Each protocol has a different way of implementing the datastore abstraction. Please refer to the
	protocol specific sections below for details:
  
	* [MySQL Datastore properties](./datastore_properties_mysql.md)
	* [Postgres Datastore properties](./datastore_properties_postgres.md)
	* [MongoDB Datastore properties](./datastore_properties_mongodb.md)
	* [Elasticsearch Datastore properties](./datastore_properties_elasticsearch.md)
	