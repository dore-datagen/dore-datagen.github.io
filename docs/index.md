```text

8 888888888o.           ,o888888o.      8 888888888o.    8 888888888888
8 8888    `^888.     . 8888     `88.    8 8888    `88.   8 8888
8 8888        `88.  ,8 8888       `8b   8 8888     `88   8 8888
8 8888         `88  88 8888        `8b  8 8888     ,88   8 8888
8 8888          88  88 8888         88  8 8888.   ,88'   8 888888888888
8 8888          88  88 8888         88  8 888888888P'    8 8888
8 8888         ,88  88 8888        ,8P  8 8888`8b        8 8888
8 8888        ,88'  `8 8888       ,8P   8 8888 `8b.      8 8888
8 8888    ,o88P'     ` 8888     ,88'    8 8888   `8b.    8 8888
8 888888888P'           `8888888P'      8 8888     `88.  8 888888888888


                   SCHEMA BASED FAKE DATA GENERATOR
```


# Welcome to Dore's documentation!

## Getting Started

*Dore* is a tool that generates fake data for you based on a config (known as the **manifest**). 
It can generate data for schemas with complex dependencies such as hierarchical schemas, schemas with PK/FK relations, 
nested values, and so on.

Dore leverages other fake data generation libraries (ex: Faker) and generates fake data for complex schemas with 
dependencies amongst them. While Faker allows you to do something like *generate a random UUID4 string*, with Dore, 
you could do something along the lines of *Generate a random UUID4 string as PK for a table and use these values as a FK in another 
table*.

You can use Dore for local development as well as in CI/CD pipelines.

## Installation

*Optional*: Create/Use a virtual env with python [venv](https://docs.python.org/3/library/venv.html) before installing
anything.

```console
foo@bar:$ python3 -m venv dore-venv && source dore-venv/bin/activate
```

Install the `dore` package with [pip](https://pypi.org/project/dore/).

```console
foo@bar:(dore-venv)$ pip install dore
```

## Next Steps

Once the installation is complete, and if this is the first time you're trying out Dore, we recommend you check out our
[E-Commerce example](./example.md) to get hands on with Dore.

## Documentation

### Usage

```shell
$ dore --manifest MANIFEST_FILE [OPTIONS]
```

Please refer [CLI Reference](./cli/cli_reference.md) to view details on usage of the `dore` command.

### Manifest

Please refer [Manifest Reference](./manifest/manifest.md) to view documentation on Dore Manifest.


