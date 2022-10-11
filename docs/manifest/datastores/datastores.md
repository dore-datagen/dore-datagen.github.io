# Datastores

You can think of a datastore as a **MySQL database**, an **Elasticsearch cluster**, etc.

A manifest can have multiple datastores defined within it and each datastore is defined as an object with key as the 
datastore's ID and value as the datastore definition.

## Example


```json title="Datastores example" linenums="1"
{
  "datastores": {
    "a_datastore": { // (1)
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

1. Definition of a datastore with ID `a_datastore`. View [Datastore Reference](./datastore_reference.md) for 
	details.
2. Definition of a datastore with ID `another_datastore`. View [Datastore Definition](./datastore_definition.md)
	for details.
   
In this example, we define two datastores in the manifest -- `a_datastore` and `another_datastore` within the 
`datastores` field of the manifest. `a_datastore` and `another_datastore` act as IDs for the datastores and the 
values are their definitions.


## Fields

* ### `datastores` (object) [required]

	**Manifest Path: `$.datastores`**

	This object is a container for all datastore definitions. Each datastore is defined within the `datastores` object
	of the manifest and the keys act as their IDs.
  
	Accepted values for keys / datastore IDs are represented by the following regex:

	**`^[A-Za-z]+[A-Za-z0-9_\-]`**

	i.e, it should start with an alphabetical character and can be followed by any number of alpha-numeric characters, 
	hyphens, or underscores.
  
	#### In-line vs referenced definition
	
	A datastore can either be defined in-line in the manifest or in a separate file and the file can then be referenced 
  	from the manifest. You would generally want to define each datastore in a separate file as it helps in keeping 
  	configs for each entity small and readable.
  
	* [Datastore Definition](./datastore_definition.md) (when defining the model in-line)
	* [Datastore Reference](./datastore_reference.md) (when defining the model in a separate file)
                   