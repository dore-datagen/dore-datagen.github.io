# Faker

** Manifest path: `$.models[*].attributes[*].value` **

With Dore, you can leverage the capabilities that <a href="https://faker.readthedocs.io/en/master/" target="_blank"> 
Python's Faker library </a> provides in order to generate values for attributes.

## Example

```json title="Faker value config example" linenums="1"
{
  "faker": {
    "pyint": {
      "min_value": 1,
      "max_value": 3
    }
  }
}
```

This is identical to invoking the
<a href="https://faker.readthedocs.io/en/master/providers/faker.providers.python.html#faker.providers.python.Provider.pyint" target="_blank">
pyint
</a>
method for generating values for the attribute.

Python's Faker library uses the concept of 
<a href="https://faker.readthedocs.io/en/master/providers/baseprovider.html" target="_blank">
providers 
</a> 
which **provide** methods to a faker instance. These methods, when invoked, generate a value.

## Fields

* ### `faker` (object) [required]

    ** Manifest path: `$.models[*].attributes[*].value.faker`**

    The `faker` object inside value config indicates Dore that it needs to use Faker to generate values for the 
    attribute.

    In a Dore manifest, Faker based attribute value configs have the following general structure:
    
    ```json title="General structure of a faker config" linenums="1"
    {
      "value": { // (1)
        "faker": {  // (2)
          "faker_method_name": { // (3)
            ... faker method params ...
          }
        }
      }
    }
    ```
    
    1. `value` config for the attribute at `$.models[*].attributes[*].value`
    2.  Use `"faker"` to indicate that we want to use the faker value generator
    3. The faker method to use. Example: [`pyint`](https://faker.readthedocs.io/en/master/providers/faker.providers.misc.html#faker.providers.misc.Provider.uuid4), 
       [`uuid4`](https://faker.readthedocs.io/en/master/providers/faker.providers.misc.html#faker.providers.misc.Provider.uuid4), 
       etc.