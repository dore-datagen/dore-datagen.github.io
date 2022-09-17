# Attributes

**Manifest path: `$.models[*].attributes`**

All attribute definitions for a model go here.

You can think of an attribute as a *column* in a MySQL table, a *field* of
an Elasticsearch index, and so on.

## Attribute

**Manifest path: `$.models[*].attributes[*]`**

A model can have multiple attributes defined within it. Like datastores and models,  each attribute is defined as an 
object with key as the attribute's ID and value as the attribute definition.

Similar to datastores and models, an attribute can either be defined in-line in the manifest or in a separate file.

If you are defining the attribute in-line, refer to the [Attribute Definition](#attribute-definition-object) section.
If you are defining the attribute in a separate file file, refer to the [Attribute Reference](#attribute-reference-object)
section.

### Attribute Definition (object)

When defining an attribute, we mainly need to provide Dore details about how it should generate `value`(s) for the 
attribute. In case records generated for the model need to be persisted in a datastore, we also need to specify
*protocol specific* `properties` for the attribute.

* #### `value` (object) [required]

    **Manifest path: `$.models[*].attributes[*].value`**

    This config is used to specify how Dore should generate values for the attribute.

    Please refer [Attribute Value Generators](value_generators.md) for more details.
    
* #### `properties` (object)

	This config is used to specify protocol specifc properties for the attribute.

	Please refer [Attribute Properties](./attribute_properties.md) for more details.

### Attribute Reference (object) 

An attribute can be defined in a file separate from the manifest (or the model) file.

Use the `ref` field in the attribute definition and provde *absolute* path to the file that contains the
attribute definition.

??? example "Example:: Attribute reference"
	```json
	{
		"an_attribute": {
			"ref": "/abs/path/to/file.json"
		}
	}
	```

	The definition for `an_attribute` is present in a separate file and the 
	`ref`erence to that file is added in the manifest.

* #### `ref` (string) [required]

	**Manifest Path: `$.models[*].attributes[*].ref`**

	*Absolute* path to file that contains the [attribute definition](#attribute-definition-object).
