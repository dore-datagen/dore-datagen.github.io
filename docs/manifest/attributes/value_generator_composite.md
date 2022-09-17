# Composite

* #### `composite`

**Manifest path: `$.models[*].attributes[*].value.composite`**

The composite attribute value generator is similar to the `ref` attribute value generator in the sense that you can 
have attributes of a model be dependent on other models. But, it is different in one major way: While you would use 
the `ref` attribute value generator when you want values of an attribute of a particular model be dependent on the 
values of another attribute of a different model, the `composite` attribute value generator lets you assign the 
value of an attribute to be an *entire record* of the dependent model.

 example 

```json title="Composite value generator" linenums="1"
{
  "value": {
    "composite": {
      "ref": "modelId
    }
  }
}
```

When an attribute uses a `composite` value generator, an entire record of the dependent model would be used as the 
value for the attribute. In other words, the attribute will have an *object* as a value and the value is a record of
the dependent model.

* #### `ref` (string) [required]
**Manifest path: `$.models[*].attributes[*].value.composite.ref`**

    Use ID of the referenced model as values here.
    A record of the referenced model will be used as value for this attribute.