# Manifest Variables

Let's look at the definition for `ecommerce` Datastore in our Manifest. We see that we have added database 
credentials: `user` and `password`, in plain text in the manifest file.

```json linenums="1" title="ecommerce Datastore in dore-ecommerce-manifest.json" hl_lines="10 11"
{
  "id": "ecommerce-example",
  "datastores": {
    "ecommerce": {
      "protocol": "mysql",
      "properties": { 
        "database": "Dore_Ecommerce",
        "host": "127.0.0.1",
        "port": "3306",
        "user": "root",
        "password": "password"
      }      
    }
  }
}
```

Ideally, we would not want to store database credentials in the Manifest this way as it leads to security 
concerns. A better approach could perhaps be to use a variables as a placeholder in the manifest for the `user` and 
`password` fields and provide those values while invoking Dore.

Dore supports specifying variables in the manifest using the [pystache](https://github.com/defunkt/pystache) 
library (which supports the [mustache](https://mustache.github.io/) syntax) and providing values to those variables 
while invoking Dore.

The mustache syntax for specifying variables is `{{variable_name}}`.

Let's change the datastore definition to use variables for `user` and `password` instead of the actual values as 
mentioned in the previous snippet.

```json linenums="1" title="Using variables in Manifest" hl_lines="10 11"
{
  "id": "ecommerce-example",
  "datastores": {
    "ecommerce": {
      "protocol": "mysql",
      "properties": { 
        "database": "Dore_Ecommerce",
        "host": "127.0.0.1",
        "port": "3306",
        "user": "{{mysql-user}}",
        "password": "{{mysql-password}}"
      }      
    }
  }
}
```

You can provide values for variables while invoking Dore as follows:

```shell
dore --manifest MANIFEST_FILE [OPTIONS] \
  --varname1=value \
  --varname2=value
```

Let's try invoking Dore once again by providing values for the `mysql-user` and `mysql-password` variables above and 
ensure everything works fine:

```shell title="Invoke dore with values for manifest variables" hl_lines="2 3"
dore --manifest /abs/path/to/ecommerce-dore-manifest.json \
  --mysql-user=root \
  --mysql-password=password
```

If you’re using the same database as you previously used and nothing changed in MySQL, you should see the 
following in Dore logs:

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

Head over to the next section to learn what the exception means and how to fix it.

<br>
<hr>

[ ➡ Next: Handling Model Conflicts](/tutorial/handling_model_conflicts/){.md-button}

<hr>
