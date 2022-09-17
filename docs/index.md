# Welcome to Dore's documentation!

## Getting Started

*Dore* is a Python based CLI tool that generates fake data for you based on a config (known as the manifest). 
It can generate data for schemas with complex dependencies such as hierarchical schemas, schemas with PK/FK relations, 
nested values, and so on.

Dore leverages other fake data generation libraries (ex: Faker) which provide the ability to 
generate fake data for various data types and generate fake data for complex schemas with dependencies amongst them. 
While Faker allows you to do something like *generate a random UUID4 string*, with Dore, you could 
something along the lines of *Generate a random UUID4 string as PK for a table and use these values as a FK in another 
table*.

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

Follow our [E-Commerce example](./example.md) to get started with Dore!
