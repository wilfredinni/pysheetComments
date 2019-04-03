Lorem ipsum dolor sit amet consectetur adipisicing elit. Laboriosam nostrum maxime hic quaerat rerum aspernatur similique voluptatum illum veritatis sint sequi fugiat odio, numquam saepe quisquam accusantium assumenda corporis soluta.

Laboriosam nostrum maxime hic quaerat rerum aspernatur similique voluptatum illum veritatis sint sequi fugiat odio, numquam saepe quisquam accusantium assumenda corporis soluta.

## Creating a Virtual Environment

We can start a new Python project with Poetry by using the `poetry init` command to create a `pyproject.toml` file interactively. This is a good option if you already have a working project and want to switch from `Pipenv` or other dependency tool. The other

In this case, we will use `poetry new <project_name>` and create a basic project structure since we are starting from zero.

```
poetry new how-long
```

This will create a `how-long` folder ready for us to start coding:

```
├── README.rst
├── how_long
│   └── __init__.py
├── pyproject.toml
└── tests
    ├── __init__.py
    └── test_how_long.py
```

Open the `pyproject.toml` file, it will look like this:

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

- Under `[tool.poetry]` are the details of our project. If something is missing, you can fill it.
- In `[tool.poetry.dependencies]` is the python version we used to create the project (`python = "^3.7"`). Every package we install and use in production be listed in here.
- By default, Poetry add `pytest` in `[tool.poetry.dev-dependencies]`. Every package listed in here will be used only in development, but not included when we publish or package. Well see later on why this is a good thing.

For now, let's create our Virtual Environment and install `pytest` along with it.

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