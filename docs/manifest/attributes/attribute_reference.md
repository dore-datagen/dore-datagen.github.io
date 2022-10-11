# Attribute Reference

**Manifest path: `$.models[*].attributes[*]`**

An attribute can be defined in a file separate from the manifest (or the model) file.

Use the `ref` field in the attribute definition and provde *absolute* path to the file that contains the
[Attribute Definition](./attribute_definition.md).

## Example

```json linenums="1" title="Attribute Reference example"
{
  "an_attribute": {
    "ref": "/abs/path/to/file.json"
  }
}
```

The definition for `an_attribute` is present in a separate file and the 
`ref`erence to that file is added in the manifest.

## Fields

* ### `ref` (string) [required]

	**Manifest Path: `$.models[*].attributes[*].ref`**

	*Absolute* path to file that contains the [Attribute Definition](./attribute_definition.md).
