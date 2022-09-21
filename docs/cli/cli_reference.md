# CLI Reference

## Name

```shell
dore - config based fake data generator
```


## Synopsis

```shell
$ dore --manifest MANIFEST_FILE [OPTIONS]
```

## Description

*Dore* is a tool that generates fake data for you based on a config (known as the **manifest**). 
It can generate data for schemas with complex dependencies such as hierarchical schemas, schemas with PK/FK relations, 
nested values, and so on.

Dore leverages other fake data generation libraries (ex: Faker) and generates fake data for complex schemas with 
dependencies amongst them. While Faker allows you to do something like *generate a random UUID4 string*, with Dore, 
you could do something along the lines of *Generate a random UUID4 string as PK for a table and use these values as a 
FK in another table*.

## Options

* #### `--manifest` `MANIFEST_FILE`
    Absolute path to [Dore Manifest](../manifest/manifest.md) file.

* #### [`--help`]
    
    Show help for `dore` command.


* #### [`--scale-factor` `SCALE_FACTOR`]

    Scale factor for records generation. 
  
    *Accepted values:* `1`, `0.1`, `0.25`, `3`, etc (numeric values).

    *Default value*: `1`

* #### [`--seed` `SEED`]

    Seed value to use for generating fake data.

    *Accepted values:* `1512312`, `1234`, etc (integer values)

* #### [`--drop-conficting-models`]

    Drop any conflicting models (pre-existing models with identical names as those in the manifest) that Dore 
    encounters while executes.

    Please use this option with care as Dore will **delete existing models and re-create them** when it encounters any 
    pre-existing models in a datastore with names identical to those in the manifest.`

* #### [`--cache` `CACHE_TYPE`]

    Cache type.

    While generating data for schemas with dependencies amongst models, Dore caches records for dependent models in 
    order to avoid repeated DB calls.

    *Accepted values*: `local`, `redis`

    * ** `local` **
      
        When cache type is `local`, Dore uses a local Python dictionary based cache.
      
    * ** `redis` **
      
        When cache type is `redis`, Dore uses a redis cluster for caching.
  
    *Default value*: `local`

* #### [`--redis-host` `REDIS_HOST`]

    Host of the redis cluster which Dore uses for caching. 
  
    This is a required arg when `--cache` is `redis`.

    *Accepted values*: `127.0.0.1`, `redis15.localnet.org`, etc.

* #### [`--redis-port` `REDIS_PORT`]

    Port of the redis cluster which Dore uses for caching.
  
    This is a required arg when `--cache` is `redis`.

    *Accepted values*: `6379`, `1234`, etc.

* #### [`--profile`]

    Run Dore with profiling. The profile output is stored in a `.prof` file.

* #### [`--manifest_var=value`]

    Specify values for variables in the manifest.

    You can use variables in the manifest by using `{{manifest_var}}` in the manifest file and supply values to each
    of the variables while invoking `dore` using the above argument.
