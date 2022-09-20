# Models

You can think of a model as a **MySQL table**, an **Elasticsearch index**, etc.

A manifest can have multiple models defined within it and each model is defined as an object with key as the model 
ID and value as the model definition.

## Example

```json title="Model example"
{
  "models": {
    "a_model": { // (1)
      "ref": "/abs/path/to/definition.js"
    },
    "another_model": { // (2)
      "records": 100,
      "persistence": "FULL",
      "datastore": "a_datastore",
      "properties": {
        "tableName": "anoter_model_tbl"
      },
      "attributes": {  // (3)
        // attribute definitions //
      }
    }
  }
}
```

1. Definition of a Model with ID `a_model`. View [Model Reference](./model_reference.md) for details.

2. Definition of a Model with ID `another_model`. View [Model Definition](./model_definition.md) for details.

3. Attributes for `another_model`. View [Attributes](../attributes/attributes.md) for further details.

## Fields

* ### `models` (object) [required]

    **Manifest path: `$.models`**

    This object is a container for all model definitions. Each model is defined within the `models` object of the 
    manifest and the keys act as their IDs.
  
    Accepted values for keys / model IDs are represented by the following regex:

    **`^[A-Za-z]+[A-Za-z0-9_\-]`**

    i.e, it should start with an alphabetical character and can be followed by any number of alpha-numeric characters, 
	hyphens, or underscores.
  
    #### In-line vs referenced definition

    A model can either be defined in-line in the manifest or in a separate file. You would generally want to define 
    each model in a separate file as it helps in keeping configs for each entity small and readable.
    
    * [Model Definition](./model_definition.md) (when defining the model in-line)
    * [Model Reference](./model_reference.md) (when defining the model in a separate file)
