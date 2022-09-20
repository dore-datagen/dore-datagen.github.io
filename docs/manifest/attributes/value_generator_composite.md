# Composite

** Manifest path: `$.models[*].attributes[*].value` **

The composite attribute value generator is similar to the `ref` attribute value generator in the sense that you can 
have attributes of a model be dependent on other models. But, it is different in one major way: While you would use 
the `ref` attribute value generator when you want values of an attribute of a particular model be dependent on the 
values of another attribute of a different model, the `composite` attribute value generator lets you assign the 
value of an attribute to be an *entire record* of the dependent model.

## Example

Consider the following schema where you want to generate records for a `customer` collection in MongoDB

<figure markdown>
  ![Manifest Mind Map](../../assets/dore-nested-docs.svg)
  <figcaption>Fig: Schema with nested attribute</figcaption>
</figure>

The first model / collection `customer` has a `shippingAddress` field whose values are nested objects of the 
`address` model. That is, the documents in `customer` collection would look something like the one shown below:

```json title="Dcouments in customer collection"
{
  "customer_id": 1,
  "shippingAddress": {
    "house": "foo house",
    "street": "bar street",
    "state": "baz state",
    "country": "Some Country
  }
}
```

In order to generate data for this schema with Dore, we can specify the value config for `shippingAddress` in the 
`customer` model as a `composite` value and provide a `ref` to the dependent model, which is the `address` model.

```json title="Composite value config for `customer` model" linenums="1"
{
  "value": {
    "composite": {
      "ref": "address"
    }
  }
}
```

When an attribute uses a `composite` value generator, an entire record of the dependent model would be used as the 
value for the attribute. In other words, the attribute will have an *object* as a value and the value is a record of
the dependent model.

## Fields

* ### `composite` (object)[required]

    ** Manifest path: `$.models[*].attributes[*].value.composite.composite` **
    
       The `composite` object inside value config indicates Dore that it needs to use Composite Value Geneartor to generate 
       values for the attribute.
 

    * ### `ref` (string) [required]
    
        ** Manifest path: `$.models[*].attributes[*].value.composite.ref` **
    
        Use ID of the referenced model as values here.
        A record of the referenced model (picked at random) will be used as value for this attribute.