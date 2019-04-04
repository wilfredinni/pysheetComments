Lorem ipsum dolor sit amet consectetur adipisicing elit. Laboriosam nostrum maxime hic quaerat rerum aspernatur similique voluptatum illum veritatis sint sequi fugiat odio, numquam saepe quisquam accusantium assumenda corporis soluta.

Laboriosam nostrum maxime hic quaerat rerum aspernatur similique voluptatum illum veritatis sint sequi fugiat odio, numquam saepe quisquam accusantium assumenda corporis soluta.

## Creating a Virtual Environment

We can start a new Python project with Poetry by using the `poetry new <project_name>` command:

```
$ poetry new how-long
```

This will create a basic project structure inside of `how-long` directory:

```
how-long
├── README.rst
├── how_long
│   └── __init__.py
├── pyproject.toml
└── tests
    ├── __init__.py
    └── test_how_long.py
```

### The pyproject.toml File

The *pyproject.toml* file contains all the details and dependencies of your project:

```
[tool.poetry]
name = "how-long"
version = "0.1.0"
description = "Simple decorator to measure a function execution time."
authors = ["wilfredinni <carlos.w.montecinos@gmail.com>"]

[tool.poetry.dependencies]
python = "^3.7"

[tool.poetry.dev-dependencies]
pytest = "^3.0"

[build-system]
requires = ["poetry>=0.12"]
build-backend = "poetry.masonry.api"
```

#### [tool.poetry]

All the details (if something is missing, you can manually fill it). Adding a [license](https://poetry.eustace.io/docs/pyproject/#license) and a [Readme](https://poetry.eustace.io/docs/pyproject/#readme) might be a good idea:

```
[tool.poetry]
...
license = "MIT"
readme = "README.rst"
```

#### [tool.poetry.dependencies]

First is the Python version we used to create the package. Basically, this says that our project will be compatible with Python 3.7 and up. And from now on, every package we install that is meant to be used in production will be listed here.

#### [tool.poetry.dev-dependencies]

Every package added in here will be used only in development, this means that they will be not included when we publish our package. Also, By default Poetry includes [pytest](https://docs.pytest.org/en/latest/), so we will use it to test our project.

### Poetry Install

Now, let's create our Virtual Environment and install *pytest* with the `poetry install` command:

```
$ poetry install
```

![poetry-install-command](https://raw.githubusercontent.com/wilfredinni/pysheetComments/master/unpublished/poetry_vscode_p1/poetry-install.png)

After is done, a new file, `poetry.lock` will be created.

> When Poetry has finished installing, it writes all of the packages and the exact versions of them that it downloaded to the poetry.lock file, locking the project to those specific versions. You should commit the poetry.lock file to your project repo so that all people working on the project are locked to the same versions of dependencies (more below).

## Dependency Management

We can add or remove dependencies directly from the *pyproject.toml* file and update our Virtual Environment with `poetry install`. But instead, we will use the `add` and `remove` commands to avoid manually modifying it.

### Adding Dependencies

Well add two packages to our project, *pendulum* and *coo*:

```
$ poetry add pendulum coo
```

![poetry-add-command](https://raw.githubusercontent.com/wilfredinni/pysheetComments/master/unpublished/poetry_vscode_p1/poetry-add.png)

Open *pyproject.toml* and *poetry.lock* and see how they have updated.

### Adding Dev Dependencies

This dependencies will be available only during development, but Poetry will not include them when building and publishing your project. We already installed *pytest*, but we will also use [flake8](http://flake8.pycqa.org/en/latest/) for linting and [mypy](http://mypy-lang.org/) for static typing:

```
$ poetry add -D flake8 mypy
```

Oh! I forgot to add a formatter, I will go with [black](https://black.readthedocs.io/en/stable/):

```
$ poetry add -D black
[ValueError]
Could not find a matching version of package black

add [-D|--dev] [--git GIT] [--path PATH] [-E|--extras EXTRAS] [--optional] [--python PYTHON] [--platform PLATFORM] [--allow-prereleases] [--dry-run] [--] <name> (<name>)...
```

This happens because *black* is in a pre release state, so Poetry cannot find any stable version for us. But I really want it so lets install it anyway:

```
$ poetry add -D black --allow-prereleases
```

![poetry-add-dev-command](https://raw.githubusercontent.com/wilfredinni/pysheetComments/master/unpublished/poetry_vscode_p1/poetry-add-dev.png)

### Removing Dependencies

You know what, i changed my mind, this project will use nor *coo* nor *mypy*. Well start removing *coo*, a normal dependency of our project:

```
$ poetry remove coo
```

Now *mypy* which is a dev dependency:

```
$ poetry remove -D mypy
```

## Conclusion

Lorem ipsum dolor sit amet consectetur adipisicing elit. Laboriosam nostrum maxime hic quaerat rerum aspernatur similique voluptatum illum veritatis sint sequi fugiat odio, numquam saepe quisquam accusantium assumenda corporis soluta.
