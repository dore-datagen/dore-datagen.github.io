# Selector

**Manifest path: `$.models[*].attributes[*].value`**

Dore allows you to define a list of values from which a value is selected for an attribute during
record generation.

Consider an example where you have an attribute representing the size of a T-shirt and you wanted the value
of this attribute to be one of the following values: `"S"`, `"M"`, `"L"` picked at random for each record. You can
use the *Random Selector* for this. If, for example, you wanted the T-shirt size value to be picked from the list 
in a round robin fashion for each record, you can use the *Round Robin Selector*

## Example

```json title="Selector example" linenums="1"
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

## Fields

* ### `selector` (object)

    ** Manifest path: `$.models[*].attributes[*].value.selector` **

    The `selector` object inside `value` config indicates Dore that it needs to use a Selector to generate values for 
    the attribute.


    Dore supports the following selector types. Please visit the selector specific documentation to view details on how 
    to use a particular selector.

    * [Random Selector](/attribute_value_generators/random_selector/)
    * [Round Robin Selector](/attribute_value_generators/round_robin_selector/)
