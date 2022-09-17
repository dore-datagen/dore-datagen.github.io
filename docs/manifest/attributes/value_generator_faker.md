# Faker

* #### `faker`

** Manifest path: `$.models[*].attributes[*].value.faker`**

With Dore, you can leverage the capabilities that <a href="https://faker.readthedocs.io/en/master/" target="_blank"> 
Python's Faker library </a> provides in order to generate values for attributes.

```json linenums="1"
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

You can invoke faker methods without any params by providing an empty params object as shown below

```json linenums="1"
{
  "faker": {
    "uuid": {}
  }
}
```

Python's Faker library uses the concept of 
<a href="https://faker.readthedocs.io/en/master/providers/baseprovider.html" target="_blank">
providers 
</a> 
which **provide** methods to a faker instance. These methods, when invoked, generate a value.

For example, the 
<a href="https://faker.readthedocs.io/en/master/providers/faker.providers.misc.html?highlight=uuid#faker.providers.misc.Provider" target="_blank"> 
`misc` provider
</a>
provides a method
<a href="https://faker.readthedocs.io/en/master/providers/faker.providers.misc.html?highlight=uuid#faker.providers.misc.Provider" target="_blank">
`uuid4`
</a>
that allows you to generate UUID4 strings. In a Python program, you can invoke this method by calling `fake.uuid4()`
to get a randomly generated UUID4 string.

In Dore manifest, Faker based attribute value configs have the following general structure:

```json linenums="1"
{
  "value": { // (1)
    "faker": {  // (2)
      "faker_method_name": {
        ... faker method params ...
      }
    }
  }
}
```

1. `value` config for the attribute at `$.models[*].attributes[*].value`
2.  Use `"faker"` to indicate that we want to use the faker value generator