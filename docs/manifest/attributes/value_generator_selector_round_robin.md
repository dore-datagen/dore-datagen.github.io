# Round Robin Selector

** Manifest path: `$.models[*].attributes[*].value.selector` **

Select values in a round-robin manner for the attribute from a list of values.

## Example

```json title="Round Robin selector example"
{
  "selector": {
    "roundRobin": {
      "items": [
        "S",
        "M",
        "L"
      ]
    }
  }
}
```

An item from the `items` array is picked in a round robin manner during each record generation for the attribute
value.

## Fields

* ### `roundRobin` (object)

    **Manifest path: `$.models[*].attributes[*].value.selector.roundRobin`**

    The `roundRobin` object inside `selector` config indicates Dore that it needs to use the Random Selector to 
    generate values for the attribute.

    * ### `items` (array) [required]

        **Manifest path: `$.models[*].attributes[*].value.selector.roundRobin.items`**
    
        List of values to select from. An item can be a number, a string, or an arbitrarily complex JSON object.