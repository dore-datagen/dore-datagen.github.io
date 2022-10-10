# Invoke Dore

Let's invoke Dore with the Ecommerce Manifest file:

```shell
dore --manifest /abs/path/to/ecommerce-dore-manifest.json
```

If you were able to view logs that look like the one shown below, then take a moment to congratulate yourself for a 
successful Dore invocation! 

```shell
[2022-10-11 00:47:38,548] [INFO] [dore.manifest.manifest_factory]: successfully loaded manifest [ecommerce-example] located at [/../dore-ecommerce-manifest.json]
[2022-10-11 00:47:38,548] [INFO] [dore.datastore.datastore_factory]: initializing datastore [ecommerce]
[2022-10-11 00:47:38,586] [INFO] [dore.protocol.mysql.mysql_datastore_exists]: checking if database [Dore_Ecommerce] exists
[2022-10-11 00:47:38,593] [INFO] [dore.protocol.mysql.mysql_create_datastore]: creating database [Dore_Ecommerce]
[2022-10-11 00:47:38,614] [INFO] [dore.protocol.mysql.mysql_model_exists]: checking existence for table [`Dore_Ecommerce`.`Customer`]
[2022-10-11 00:47:38,623] [INFO] [dore.protocol.mysql.mysql_create_model]: creating table [`Dore_Ecommerce`.`Customer`]
[2022-10-11 00:47:38,663] [INFO] [dore.protocol.mysql.mysql_model_exists]: checking existence for table [`Dore_Ecommerce`.`Order`]
[2022-10-11 00:47:38,671] [INFO] [dore.protocol.mysql.mysql_create_model]: creating table [`Dore_Ecommerce`.`Order`]
[2022-10-11 00:47:38,730] [INFO] [dore.engine.engine]: generating records for model [customer]
100%|██████████████████████████████████████████████| 10/10 [00:00<00:00, 2936.98it/s]
[2022-10-11 00:47:38,768] [INFO] [dore.engine.engine]: [10] records generated for model [customer]
[2022-10-11 00:47:38,768] [INFO] [dore.engine.engine]: populating cache with records for [customer]
[2022-10-11 00:47:38,784] [INFO] [dore.engine.engine]: generating records for model [order]
100%|███████████████████████████████████████████| 100/100 [00:00<00:00, 13760.39it/s]
[2022-10-11 00:47:38,822] [INFO] [dore.engine.engine]: [100] records generated for model [order]
[2022-10-11 00:47:38,822] [INFO] [dore.engine.engine]: Clearing cache
```

Dore creates the required databases, tables, and generates data in the tables based on schema specified in the manifest.

We recommend you check out data created by Dore in your MySQL instance by running a few queries.

<br>
<hr>

[ ➡ Next: Manifest Variables](/tutorial/manifest_variables/){.md-button}

<hr>

