# Random Selector

** Manifest path: `$.models[*].attributes[*].value.selector` **

Select values at random for the attribute from a list of values.

## Example

```json title="Random selector example"
{
  "selector": {
    "random": {
      "items": [
        "S",
        "M",
        "L"
      ]
    }
  }
}
```

An item from the `items` array is picked at random during each record generation for the attribute
value.

## Fields

* ### `random` (object)

    **Manifest path: `$.models[*].attributes[*].value.selector.random`**

    The `random` object inside `selector` config indicates Dore that it needs to use the Random Selector to generate 
    values for the attribute.

    * ### `items` (array) [required]

        **Manifest path: `$.models[*].attributes[*].value.selector.random.items`**
    
        List of values to select from. An item can be a number, a string, or an arbitrarily complex JSON object.

        Each value in the list is usually equally likely to be picked.