# Selector

* #### `selector`

**Manifest path: `$.models[*].attributes[*].value.selector`**

Dore allows you to define a list of values from which a value is selected for an attribute during
record generation.

Consider an example where you have an attribute representing the size of a T-shirt and you wanted the value
of this attribute to be one of the following values: `"S"`, `"M"`, `"L"` picked at random for each record. You can
use the *Random Selector* for this. If, for example, you wanted the T-shirt size value to be picked from the list 
in a round robin fashion for each record, you can use the *Round Robin Selector*

Each section in the `selector` field below illustrates one of the various selector types supported
by Dore and contains details on how to use it.

=== "Random Selector"

    * #### `random`

    **Manifest path: `$.models[*].attributes[*].value.selector.random`**

    Selects values at random for an attribute from the list of values provided.

    ??? example "Example:: Random selector"
    
        ```json
        {
          "selector": {
            "random": {
              "items": [
                "item 1",
                "item 2",
                "item 3"
              ]
            }
          }
        }
        ```

        An item from the `items` array is picked at random during each record generation for the attribute
        value.

    Each value in the list is usually equally likely to be picked.

    * #### `items`

    **Manifest path: `$.models[*].attributes[*].value.selector.random.items`**

    List of values to select from. An item can be anumber ,a string, or an arbitrarily complext JSON
    object.

=== "Round Robin Selector"

    * #### `roundRobin`

    **Manifest path: `$.models[*].attributes[*].value.selector.roundRobin`**

    Selects values for an attribute from the list of values provided in a round robin fashion.

    ??? example "Example:: Round robin selector"

        ```json
        {
          "selector": {
            "roundRobin": {
              "items": [
                "item 1",
                "item 2",
                "item 3"
              ]
            }
          }
        }
        ```

        An item from the `items` array is picked in round robin fashion during each record generation for the 
        attribute value.

    * #### `items`

    **Manifest path: `$.models[*].attributes[*].value.selector.roundRobin.items`**

    List of values to select from. An item can be anumber ,a string, or an arbitrarily complext JSON
    object.

    When we do this, Dore uses the `Ecommerce.Customer` model's `customer_id` values as values for the 
    `customer_id` attribute for the `Ecommerce.Order` model.
