# Datastore Reference

**Manifest path: `$.datastores[*]`**

A datastore can be defined in a file separate from the manifest file.

Use the `ref` field in the datastore definition and provide *absolute* path to the file that actually contains the
[Datastore Definition](./datastore_definition.md).

## Example

```json title="Datastore reference example"
{
	"a_datastore": {
		"ref": "/abs/path/to/file.json"
	}
}
```

The definition for `a_datastore` is present in a separate file located at `/abs/path/to/file.json` and a `ref`erence to 
that file is added in the manifest.

## Fields

* #### `ref` (string) [required]

	**Manifest Path: `$.datastores[*].ref`**

	*Absolute* path to file that contains the [Datastore Definition](./datastore_definition.md).
