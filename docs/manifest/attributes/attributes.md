# Attributes

You can think of an attribute as a **MySQL Column**, an **Elasticsearch Field**, etc.

In a manifest, each model can have multiple attributes defined within it and each attribute is defined as an object 
with key as the attribute ID and value as the attribute definition.

## Example

```json title="Attribute example"
{
	"attributes": {
		"an_attribute": { // (1)
			"ref": "/abs/path/to/definition.js"
		},
		"another_attribute": { // (2)
			"properties": {
				"columnName": "another_attribute_column",
				"columnType": "DATE"
			},
			"value": {  // (3)
				"faker": {
					"date_between": {
						"start_date": "2021-01-01",
						"end_date": "2022-01-01"
					}
				}
			}
		}
	}
}
```

1. Definition of an Attribute with ID `an_attribute`. View [Attribute Reference](./attribute_reference.md) for details.
   
2. Definition of an Attribute with ID `another_attribute`. View [Attribute Definition](./attribute_definition.md) 
   for details.
   
3. **Value** config for Attribute `another_attribute`. View [Attribute Value Generators](./value_generators.md) for 
   details.

## Fields

* ### `attributes` (object) [required]
	
	**Manifest path: `$.models[*].attributes`**

	This object is a container for all attribute definitions for a model. Each attribute is defined within the
  	`attributes` object of a model and the keys act as their IDs.
  
    Accepted values for keys / Attribute IDs are represented by the following regex:

    **`^[A-Za-z]+[A-Za-z0-9_\-]`**

    i.e, it should start with an alphabetical character and can be followed by any number of alpha-numeric characters, 
	hyphens, or underscores.
  
    #### In-line vs referenced definition

    An attribute can either be defined in-line in the manifest or in a separate file. Although we recommend 
  	spreading model and datastore definitions across different files, whether to move an attribute 
  	definition to a different file can be quite subjective. We recommend you take the call based on what seems more 
  	readable for you. 
    
    * [Attribute Definition](./attribute_definition.md) (when defining the attribute in-line)
    * [Attribute Reference](./attribute_reference.md) (when defining the attribute in a separate file)
    