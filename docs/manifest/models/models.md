# Models

**Manifest path: `$.models`**

All model definitions go here.

You can think of a model as *table* in MySQL, an *index* in Elasticsearch, a *collection* in MongoDB, and so on.

## Model

**Manifest path: `$.models[*]`**

A manifest can have multiple models defined within it. Like datastores, each model is defined as an
object with key as the model's ID and value as the model definition.

A model can either be defined in-line in the manifest or in a separate file. You would generally want to define 
each model in a separate file. It is recommended to spread out different parts of the manifest such as models and 
datastores across different files in order to kee peach config small and readable.

If you are defining the model in-line, refer to the [Model Definition](#model-definition-object) section. 
If you are defining the model in a separate file, refer to the [Model Reference](#model-reference-object) section 
instead.

### Model Definition (object)

In a model definition, we specify details about `attributes` of the model, *protocol specific* `properties` 
for the model, and some additional information.

* #### `attributes` (object)[required]

    **Manifest path: `$.models[*].attributes`**

    Each model will generally have a set of attributes associated with it.

    Please refer to the [Attributes](../attributes/attributes.md) page for further details.


* #### `properties` (string)

    **Manifest path: `$.models[*].properties`**

    This config is used to specify protocol specific model properties such as table properties in MySQL, index properties
    in Elasticsearch, etc. 
  
    As protocol specific properties of a model are required only when there is a need to persist 
    the model and its records in any datastore, the `properties` field is a **required** field only 
    when the model is linked to a datastore and `persistence` on the model is set to `"FULL"` or is not explicitly 
    mentioned in the manifest as the Dore assumes the default `persistence` as `"FULL"` if not specified.
  
    Since each protocol has different requirements for configuring a model, this config varies from one protocol to the 
    other. Please refer to the protocol specific sections below to view which fields are required for a particular 
    protocol.
  
    === "MySQL"

        This schema is applicable when `protocol` for linked datastore is `"mysql"`.
  
        ??? example "Example:: MySQL model properties"
  
            ```json
            {
                "properties": {
                    "tableName": "foobar"
                }
            }
            ```

        * **`tableName` (string)[required]**
  
            **Manifest path: `$.models[*].properties.tableName`**
  
            Name of the MySQL table that the model corresponds to.

            While interacting with the MySQL table corresponding to the model, Dore uses this `tableName`
            to refer to the model in the MySQL database. 

    === "MongoDB"

        This schema is applicable when `protocol` for lined datastore is `"mongodb"`.

        ??? example "Example:: MongoDB model properties"

            ```json
            {
                "properties": {
                    "collectionName": "foobar"
                }
            }
            ```
  
        * **`collectionName` (string)[required]**
  
            **Manifest path: `$.models[*].properties.collectionName`**

            Name of the MongoDB collection that the model corresponds to.
    
            While interacting with the MongoDB collection corresponding to the model, Dore uses this `collectionName`
            to refer to the model in the MongoDB database. 
            

    === "PostgreSQL"

        This schema is applicable when `protocol` is `"postgres"`.

        ??? example "Example:: PostgreSQL model properties"

            ```json
            {
                "properties": {
                    "tableName": "foobar",
                    "schemaName":" baz"
                }
            }
            ```

        * **`tableName` (string)[required]**

            **Manifest path: `$.models[*].properties.tableName`**

            Name of the PostgreSQL table that the model corresponds to.

            While interacting with the PostgreSQL table corresponding to the model, Dore uses this `tableName`
            to refer to the model in the PostgreSQL database.

        * **`schemaName` (string)[required]**

            **Manifest path: `$.models[*].properties.schemaName`**

            Name of the PostgreSQL *schema* that the model corresponds to.

            While interacting with the PostgreSQL table corresponding to the model, Dore uses this `schemaName`
            to refer to the schema in the PostgreSQL database.

            

    === "Elasticsearch"

        This schema is applicable when `protocol` is `"elasticsearch7"` or `"elasticsearch8"`.

        * **`indexName` (string)[required]**

            **Manifest path: `$.models[*].properties.indexName`**

            ??? example "Example:: Index name"

                ```json
                {
                    "properties": {
                        "indexName": "foobar"
                    }
                }```

            Name of the Elasticsearch *index* that the model corresponds to.

            While interacting with the Elasticsearch indexes corresponding to the model, Dore uses this `schemaName`
            to refer to the schema in the Elasticsearch database.


* #### `persistence` (string)
    
    **Manifest path: `$.models[*].persistence`**

    Dore allows you to specify various persistence levels for models.

	??? example "Example:: Model persistence"
		```json
  		{ 
  			"persistence": "FULL"
  		}
  		```

    Please refer [model persistence](./model_persistence.md) for more details.
  
	??? info "Allowed values"

		| Allowed values for `protocol` |
		|-------------------------------|
		| `FULL` [default]              |
		| `MEMORY_ONLY`                 |
		| `NO_PERSIST`                  |
  

* #### `records` (integer)

    **Manifest path: `$.models[*].records`**

    We can use this field to specify the number of records Dore should generate for the model.

	??? example "Example:: Model records"
		```json
  		{ 
  			"records": 10000
  		}
  		```

    ??? note "Note: The actual count may vary"

        The actual number of records that Dore generates for a model will depend on the value provided here as well as 
        the `--scale-factor` value provided during invocation.

        For example, if a model has `records` as `10000`, and we provide a `--scale-factor` value of `0.1` when
        invoking Dore, the actual number of records generated by Dore will be `10000 * 0.1 = 1000`.

* #### `datastore` (string)

    **Manifest path: `$.models[*].datastore`**

    ID of the datastore to which this model belongs. This is a required field in cases of models that have `FULL`
    persistence levels.
  
    ??? example "Example:: Model datastore"
        ```json
        {
            "datastore": "a_datastore"
        }
        ```
  


### Model Reference (object)

A model can be defined in a file separate from the manifest file.

Use the `ref` field in the model definition and provide *absolute* path to the file that actually contains the
model definition.

??? example "Example:: Model reference"
	```json
	{
		"a_model": {
			"ref": "/abs/path/to/file.json"
		}
	}
	```

	The definition for `a_model` is present in a separate file and the 
	`ref`erence to that file is added in the manifest.

* #### `ref` (string) [required]

	**Manifest Path: `$.models[*].ref`**

	*Absolute* path to file that contains the [model definition](#model-definition-object).