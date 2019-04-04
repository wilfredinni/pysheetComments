Lorem ipsum dolor sit amet consectetur adipisicing elit. Laboriosam nostrum maxime hic quaerat rerum aspernatur similique voluptatum illum veritatis sint sequi fugiat odio, numquam saepe quisquam accusantium assumenda corporis soluta.

Laboriosam nostrum maxime hic quaerat rerum aspernatur similique voluptatum illum veritatis sint sequi fugiat odio, numquam saepe quisquam accusantium assumenda corporis soluta.

## Creating a Virtual Environment

We can start a new Python project with Poetry by using the `poetry new <project_name>` command:

```
poetry new how-long
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

The `pyproject.toml` file contains all the details and dependencies of your project:

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

All the details (if something is missing, you can fill it). Adding a [license](https://poetry.eustace.io/docs/pyproject/#license) and a [Readme](https://poetry.eustace.io/docs/pyproject/#readme) might be a good thing:

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

Now, let's create our Virtual Environment and add `pytest` to it with the `poetry install` command:

```
poetry install
```

![poetry-install-shell](https://raw.githubusercontent.com/wilfredinni/pysheetComments/master/unpublished/poetry_vscode/poetry-install.png)

After is done, a new file, `poetry.lock` will appear.

> When Poetry has finished installing, it writes all of the packages and the exact versions of them that it downloaded to the poetry.lock file, locking the project to those specific versions. You should commit the poetry.lock file to your project repo so that all people working on the project are locked to the same versions of dependencies (more below).

## Dependency Management

Lorem ipsum dolor sit amet consectetur adipisicing elit. Laboriosam nostrum maxime hic quaerat rerum aspernatur similique voluptatum illum veritatis sint sequi fugiat odio, numquam saepe quisquam accusantium assumenda corporis soluta.

### Adding Dependencies

Lorem ipsum dolor sit amet consectetur adipisicing elit. Laboriosam nostrum maxime hic quaerat rerum aspernatur similique voluptatum illum veritatis sint sequi fugiat odio, numquam saepe quisquam accusantium assumenda corporis soluta.

### Adding Dev Dependencies

Lorem ipsum dolor sit amet consectetur adipisicing elit. Laboriosam nostrum maxime hic quaerat rerum aspernatur similique voluptatum illum veritatis sint sequi fugiat odio, numquam saepe quisquam accusantium assumenda corporis soluta.

### Removing Dependencies

Lorem ipsum dolor sit amet consectetur adipisicing elit. Laboriosam nostrum maxime hic quaerat rerum aspernatur similique voluptatum illum veritatis sint sequi fugiat odio, numquam saepe quisquam accusantium assumenda corporis soluta.

## Setting Up Poetry on VSCode

Lorem ipsum dolor sit amet consectetur adipisicing elit. Laboriosam nostrum maxime hic quaerat rerum aspernatur similique voluptatum illum veritatis sint sequi fugiat odio, numquam saepe quisquam accusantium assumenda corporis soluta.

## Publishing our Project to Pypi

Lorem ipsum dolor sit amet consectetur adipisicing elit. Laboriosam nostrum maxime hic quaerat rerum aspernatur similique voluptatum illum veritatis sint sequi fugiat odio, numquam saepe quisquam accusantium assumenda corporis soluta.

## Conclusion

Lorem ipsum dolor sit amet consectetur adipisicing elit. Laboriosam nostrum maxime hic quaerat rerum aspernatur similique voluptatum illum veritatis sint sequi fugiat odio, numquam saepe quisquam accusantium assumenda corporis soluta.