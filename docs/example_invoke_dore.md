### Invoke Dore

Once the manifest is defined, we invoke Dore with it.

```console
foo@bar:(dore-venv)$ dore --manifest /abs/path/to/ecommerce-dore-manifest.json
```

That's it!

We can head over to our MySQL instance and verify that Dore created the necessary databases, tables, and populated
them with fake data as per the schema.