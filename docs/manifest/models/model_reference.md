# Model Reference

**Manifest path: `$.models[*]`**

A model can be defined in a file separate from the manifest file.

Use the `ref` field in the model definition and provide *absolute* path to the file that contains the
[Model Definition](./model_definition.md).

## Example

```json title="Model Reference example" linenums="1"
{
  "a_model": {
    "ref": "/abs/path/to/file.json"
  }
}
```

The definition for `a_model` is present in a separate file located at `/abs/path/to/file.json` and a 
`ref`erence to that file is added in the manifest.

## Fields

* ### `ref` (string) [required]

	**Manifest Path: `$.models[*].ref`**

	*Absolute* path to file that contains the [Model Definition](./model_definition.md).
