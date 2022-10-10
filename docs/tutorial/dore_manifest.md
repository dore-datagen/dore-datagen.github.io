# Dore Manifest

To generate data for any schema with Dore, we need to create the [**Dore Manifest**](/manifest/manifest/) for the 
schema, which is a definition of the target data requirements.

Dore uses the manifest to create the required databases, tables, and columns, and fill the tables up with fake data 
as per the requirements.

Here's a short summary of what we'll be defining in the Manifest:

| What we're configuring                                                   | Field            | JSON Path in Manifest              |
|--------------------------------------------------------------------------|------------------|------------------------------------|
| Details of target databases                                              | Datastores       | `$.datastores`                     |
| Details of target tables                                                 | Models           | `$.models`                         |
| Details of columns of target tables                                      | Attributes       | `$.models[*].attributes`           |
| Details on attributes which define how Dore will generate value for them | Value Configs    | `$.models[*].attrributes[*].value` |



The fields mentioned above form the core of the Dore Manifest.

We will be creating a manifest for the ecommerce schema from scratch and learn how to define each of the above 
fields in the manifest.

<hr>

[ ➡ Next: Creating the Manifest](/tutorial/create_manifest/){.md-button}

<hr>
