# Handling Model Conflicts

In the previous section, we invoked Dore a second time over the course of this tutorial and encountered the 
following logs:

```shell
[2022-10-11 00:50:44,326] [INFO] [dore.manifest.manifest_factory]: successfully loaded manifest [ecommerce-example] located at [/../dore-ecommerce-manifest.json]
[2022-10-11 00:50:44,326] [INFO] [dore.datastore.datastore_factory]: initializing datastore [ecommerce]
[2022-10-11 00:50:44,375] [INFO] [dore.protocol.mysql.mysql_datastore_exists]: checking if database [Dore_Ecommerce] exists
[2022-10-11 00:50:44,384] [INFO] [dore.protocol.mysql.mysql_model_exists]: checking existence for table [`Dore_Ecommerce`.`Customer`]
Traceback (most recent call last):
  File "/../venv/bin/dore", line 8, in <module>
    sys.exit(main())
  File "/../venv/lib/python3.9/site-packages/dore/__main__.py", line 50, in main
    engine()
  File "/../venv/lib/python3.9/site-packages/dore/engine/engine.py", line 90, in engine
    config, context = bootstrap()
  File "/../venv/lib/python3.9/site-packages/dore/engine/bootstrap.py", line 39, in bootstrap
    initialize_models(config, context)
  File "/../venv/lib/python3.9/site-packages/dore/engine/initialize_models.py", line 46, in initialize_models
    raise ModelConflictException(model.config().id(), datastore.id())
dore.exceptions.model_conflict_exception.ModelConflictException: conflicting model [customer] found in datastore [ecommerce]
```

Since the should table already exist after our first run from the 
[**Invoke Dore**](/tutorial/invoke_dore) section of the tutorial, Dore raises a 
`ModelConflictException` when it tries to create the `customer` table in the `ecommerce` database again. 

**!! Caution !!**

You can make Dore ignore this by providing the `--drop-conflicting-models` option while invoking Dore.

Please note that **using this flag allows Dore to drop/delete the conflicting models** in the database and 
create a fresh one. Since this will result in to deletion of data in your databases, **please be extremely careful 
while using this**.

You can invoke Dore by providing this flag as follows:

```shell title="Invoke dore with option to ignore conflicting models" hl_lines="4"
dore --manifest /abs/path/to/ecommerce-dore-manifest.json \
  --mysql-user=root \
  --mysql-password=password \
  --drop-conflicting-models
```

You should now be able to see a successful run. We've highlighted parts of the logs that indicate deletion of 
existing tables below:

```shell hl_lines="5 6 8 9"
[2022-10-11 00:48:22,612] [INFO] [dore.manifest.manifest_factory]: successfully loaded manifest [ecommerce-example] located at [/../dore-ecommerce-manifest.json]
[2022-10-11 00:48:22,613] [INFO] [dore.datastore.datastore_factory]: initializing datastore [ecommerce]
[2022-10-11 00:48:22,656] [INFO] [dore.protocol.mysql.mysql_datastore_exists]: checking if database [Dore_Ecommerce] exists
[2022-10-11 00:48:22,665] [INFO] [dore.protocol.mysql.mysql_model_exists]: checking existence for table [`Dore_Ecommerce`.`Customer`]
[2022-10-11 00:48:22,671] [INFO] [dore.protocol.mysql.mysql_delete_model]: dropping table [`Dore_Ecommerce`.`Customer`]
[2022-10-11 00:48:22,710] [INFO] [dore.protocol.mysql.mysql_create_model]: creating table [`Dore_Ecommerce`.`Customer`]
[2022-10-11 00:48:22,751] [INFO] [dore.protocol.mysql.mysql_model_exists]: checking existence for table [`Dore_Ecommerce`.`Order`]
[2022-10-11 00:48:22,758] [INFO] [dore.protocol.mysql.mysql_delete_model]: dropping table [`Dore_Ecommerce`.`Order`]
[2022-10-11 00:48:22,786] [INFO] [dore.protocol.mysql.mysql_create_model]: creating table [`Dore_Ecommerce`.`Order`]
[2022-10-11 00:48:22,845] [INFO] [dore.engine.engine]: generating records for model [customer]
100%|██████████████████████████████████████████████| 10/10 [00:00<00:00, 5106.91it/s]
[2022-10-11 00:48:22,885] [INFO] [dore.engine.engine]: [10] records generated for model [customer]
[2022-10-11 00:48:22,886] [INFO] [dore.engine.engine]: populating cache with records for [customer]
[2022-10-11 00:48:22,902] [INFO] [dore.engine.engine]: generating records for model [order]
100%|███████████████████████████████████████████| 100/100 [00:00<00:00, 15007.53it/s]
[2022-10-11 00:48:22,939] [INFO] [dore.engine.engine]: [100] records generated for model [order]
[2022-10-11 00:48:22,939] [INFO] [dore.engine.engine]: Clearing cache
```

We can see that Dore deleted the conflicting models from the datastore after checking for their existence and 
recreated them in the lines highlighted above.

<br>
<hr>

[ ➡ Next: Multi-File Manifest](/tutorial/multifile_manifest/){.md-button}

<hr>
