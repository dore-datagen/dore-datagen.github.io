# Datastores

**Manifest Path: `$.datastores`**

All datastore definitions go here.

You can think of a datastore as a **MySQL database**, a **MongoDB database**,  an **Elasticsearch cluster**, etc.

??? example "Example:: Datastores"

	```json
	{
		"datastores": {	// (1)
			"a_datastore": {
				"ref": "/abs/path/to/definition.js"
			},
			"another_datastore": { // (2)
				"protocol": "mysql",
				"properties": {
					"host": "127.0.0.1",
					"port": "3306",
					"user": "john_doe",
					"password": "yourpassword",
					"database": "foobar"
				}
			}
		}
	}
	```

	1. Definition of a datastore with ID `a_datastore`. View [Datastore Reference](#datastore-reference-object) for 
		details.
	2. Definition of a datastore with ID `another_datastore`. View [Datastore Definition](#datastore-definition-object)
		for details.

	In this example, we define two datastores -- `a_datastore` and `another_datastore` within the `datastores`
	field of the manifest. They keys are datastore IDs and the values are datastore definitions. Please refer
	[Datastore](#datastore) section for details.

## Datastore
**Manifest Path: `$.datastores[*]`**

A manifest can have multiple datastores defined within it. 
Each datastore is defined as an object with key as the datastore's ID and value as the datastore definition.

A datastore can either be defined in-line in the manifest or in a separate file. You would generally want to define
each datastore in a separate file. It is recommended to spread different parts of the manifest such as models 
and datastores across different files in order to keep each config small and readable.

If you are defining the datastore in place, refer to the [Datastore Definition](#datastore-definition) section.
If you are defining the datastore in a separate file, refer to the [Datastore Reference](#datastore-reference) section  
instead.

### Datastore Definition (object)

In a datastore definition, we specify which `protocol` the datastore uses (for ex: `"mysql"`) and certain *protocol
specific `properties`* of the datastore which Dore uses to interact with the underlying system.

??? example "Example:: Datastore Definition"
	```json
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

* #### `protocol` (string)

	**Manifest Path: `$.datastores[*].protocol`**
  
	The protocol / type of system that the datastore represents.

	??? example "Example:: Datastore protocol"
		```json
  		{ 
  			"protocol": "mysql"
  		}
  		```
  
	??? info "Allowed values"

		| Allowed values for `protocol`         |
		|------------------|
		| `mysql`          |
		| `mongodb`        |
		| `postgres`       |
		| `elasticsearch7` |
		| `elasticsearch8` |

* #### `properties` (object)

	**Manifest Path: `$.datastores[*].properties`**
  
	Each protocol has a different way of implementing the datastore abstraction. Please refer to the
	protocol specific documentation below to see what fields are required in the `properties` object for a particular
  	protocol.

	=== "MySQL"

		This schema is applicable when `protocol` is `"mysql"`.
  
		??? example "Example:: MySQL datastore properties"

			```json linenums="1"
  			{
            	"properties": {
                	"host": "127.0.0.1",
                	"port": "3306",
                	"user": "john_doe",
                	"password": "yourpassword",
                	"database": "foobar"
            	}
        	}
			```

		* **`host` (string)** [required]
  	
			**Manifest path: `$.datastores[*].properties.host`**
  
  			MySQL host.
  
  		* **`port` (string)** [required]
  
			**Manifest path: `$.datastores[*].properties.port`**
  	
			MySQL port.
	
  		* **`user` (string)** [required]
  
			**Manifest path: `$.datastores[*].properties.user`**
  			
  			MySQL username for connecting to the database.
		
  		* **`password` (string)** [required]
  
			**Manifest path: `$.datastores[*].properties.password`**

  			MySQL password for connecting to the database.

  		* **`database` (string)** [required]
  
			**Manifest path: `$.datastores[*].properties.database`**

			Name of the MySQL database to connect to.


	=== "MongoDB"

		This schema is applicable when `protocol` is `"mongodb"`.
  
		??? example "Example:: MongoDB datastore properties"

			```json linenums="1"
  			{
            	"properties": {
                	"host": "127.0.0.1",
                	"port": "27101",
                	"user": "john_doe",
                	"password": "yourpassword",
                	"database": "foobar"
            	}
        	}
			```

		* **`host` (string)** [required]
  	
			**Manifest path: `$.datastores[*].properties.host`**
  
  			MongoDB host.
  
  		* **`port` (string)** [required]
  
			**Manifest path: `$.datastores[*].properties.port`**
  	
			MongoDB port.
	
  		* **`user` (string)** [required]
  
			**Manifest path: `$.datastores[*].properties.user`**
  			
  			MongoDB username for connecting to the database.
		
  		* **`password` (string)** [required]
  
			**Manifest path: `$.datastores[*].properties.password`**

  			MongoDB password for connecting to the database.

  		* **`database` (string)** [required]
  
			**Manifest path: `$.datastores[*].properties.database`**

			Name of the MongoDB database to connect to.
	

	=== "PostgreSQL"

		This schema is applicable when `protocol` is `"postgres"`.

		??? example "Example:: PostgreSQL datastore properties"

			```json linenums="1"
  			{
            	"properties": {
                	"host": "127.0.0.1",
                	"port": "5432",
                	"user": "john_doe",
                	"password": "yourpassword",
                	"database": "foobar"
            	}
        	}
			```

		* **`host` (string)** [required]
  	
			**Manifest path: `$.datastores[*].properties.host`**
  
  			PostgreSQL host.
  
  		* **`port` (string)** [required]
  
			**Manifest path: `$.datastores[*].properties.port`**
  	
			PostgreSQL port.
	
  		* **`user` (string)** [required]
  
			**Manifest path: `$.datastores[*].properties.user`**
  			
  			PostgreSQL username for connecting to the database.
		
  		* **`password` (string)** [required]
  
			**Manifest path: `$.datastores[*].properties.password`**

  			PostgreSQL password for connecting to the database.

  		* **`database` (string)** [required]
  
			**Manifest path: `$.datastores[*].properties.database`**

			Name of the PostgreSQL database to connect to.
		

	=== "Elasticsearch"

		This schema is applicable when `protocol` is `"elasticsearch7"` or `"elasticsearch8"`.

		??? example "Example:: Elasticsearch datastore properties"

			```json linenums="1"
  			{
            	"properties": {
                	"host": "127.0.0.1",
                	"port": "9001",
                	"user": "john_doe",
                	"password": "yourpassword"
            	}
        	}
			```

		* **`host` (string)** [required]
  	
			**Manifest path: `$.datastores[*].properties.host`**
  
  			Elasticsearch host.
  
  		* **`port` (string)** [required]
  
			**Manifest path: `$.datastores[*].properties.port`**
  	
			Elasticsearch port.
	
  		* **`user` (string)** [required]
  
			**Manifest path: `$.datastores[*].properties.user`**
  			
  			Elasticsearch username for connecting to the database.
		
  		* **`password` (string)** [required]
  
			**Manifest path: `$.datastores[*].properties.password`**

  			Elasticsearch password for connecting to the database.




### Datastore Reference (object)

A datastore can be defined in a file separate from the manifest file.

Use the `ref` field in the datastore definition and provide *absolute* path to the file that actually contains the
datastore definition.

??? example "Example:: Datastore reference"
	```json
	{
		"a_datastore": {
			"ref": "/abs/path/to/file.json"
		}
	}
	```

	The definition for `a_datastore` is present in a separate file and the 
	`ref`erence to that file is added in the manifest.

* #### `ref` (string) [required]

	**Manifest Path: `$.datastores[*].ref`**

	*Absolute* path to file that contains the datastore definition.

                   