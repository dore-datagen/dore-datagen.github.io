### Invoke Dore

Once the manifest is defined, we invoke Dore with it.

```console
foo@bar:(dore-venv)$ dore --manifest /abs/path/to/ecommerce-dore-manifest.json
```

??? note "`dore` command usage"

    Please refer [CLI Reference](./cli/cli_reference.md) to view details on usage of the `dore` command

That's it!

You should be able to see logs that look something like this:

```shell
[2022-09-17 18:54:14,174] [INFO] [dore.engine.engine]: generating records for model [customer]
100%|████████████████████████████████████████████| 100/100 [00:00<00:00, 8997.56it/s]
[2022-09-17 18:54:14,228] [INFO] [dore.engine.engine]: [100] records generated for model [customer]
[2022-09-17 18:54:14,228] [INFO] [dore.engine.engine]: populating cache with records for [customer]
[2022-09-17 18:54:14,240] [INFO] [dore.engine.engine]: generating records for model [order]
100%|█████████████████████████████████████████| 1000/1000 [00:00<00:00, 19471.98it/s]
[2022-09-17 18:54:14,350] [INFO] [dore.engine.engine]: [1000] records generated for model [order]
[2022-09-17 18:54:14,350] [INFO] [dore.engine.engine]: Clearing cache
```

Dore creates the required databases, tables, and generates data in the tables based on schema specified in the manifest.

You can refer to [Manifest Explained](./example_manifest_explained.md) view details about the manifest created in the 
previous section.
