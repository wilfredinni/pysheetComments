So far we have:

- [Started a new project](https://www.pythoncheatsheet.org/blog/python-projects-with-poetry-and-vscode-part-1#Starting-a-New-Project).
- [Created a Virtual Environment](https://www.pythoncheatsheet.org/blog/python-projects-with-poetry-and-vscode-part-1#Creating-a-Virtual-Environment) with *Poetry*.
- [Added, Deleted and Updated](https://www.pythoncheatsheet.org/blog/python-projects-with-poetry-and-vscode-part-1#Dependency-Management) dependencies.
- Added our [Virtual Environment to VSCode](#Setting-Up-Poetry-on-VSCode).
- [Configured *Flake8*](#Flake8) to *lint* our code as we type.
- Choose [*Black*](#Black) as the formatter.
- And [included *Pytest*](#Pytest) to run our tests in a visual way.

And finally, we will write, build and publish our project to [Pypi](https://pypi.org)!

## The Project

As mentioned earlier, this will be a very simple decorator that the only thing it does is print to the console how long it takes for a function to run. It will work like this:

```python
from how_long import timer

@timer
def test_function():
    [i for i in range(10000)]

test_function()
# Execution Time: 955 ms.
```

In the end, the project directory will look, more or less, like this:

```
how-long
├── how_long
│   ├── how_long.py
│   └── __init__.py
├── how_long.egg-info
│   ├── dependency_links.txt
│   ├── PKG-INFO
│   ├── requires.txt
│   ├── SOURCES.txt
│   └── top_level.txt
├── LICENSE
├── poetry.lock
├── pyproject.toml
├── README.rst
└── tests
    ├── __init__.py
    └── test_how_long.py

```

Before we start, check for package updates with the `poetry update` command:

![poetry update](img/poetry_update.png)

Ok, now add a short description of the project in the `README.rst`:

```rst
how_long
========

Simple Decorator to measure a function execution time.

Example
_______

.. code-block:: python

    from how_long import timer


    @timer
    def some_function():
        return [x for x in range(10_000_000)]
```

Navigate to `how_long/how_long.py`:

```python
# how_long.py
from functools import wraps

import pendulum


def timer(function):
    """
    Simple Decorator to measure a function execution time.
    """

    @wraps(function)
    def function_wrapper():
        start = pendulum.now()
        function()
        ellapsed_time = pendulum.now() - start
        print(f"Execution Time: {ellapsed_time.microseconds} ms.")

    return function_wrapper
```

In `how_long/__init__.py`:

```python
from .how_long import timer

__version__ = "0.1.1"
```

And finally, the `tests/test_how_long.py` file:

```python
from how_long import __version__
from how_long import timer


def test_version():
    assert __version__ == "0.1.1"


def test_wrap():
    @timer
    def wrapped_function():
        return

    assert wrapped_function.__name__ == "wrapped_function"
```

You can now enter `poetry install` on your terminal to install and prove your package locally. Activate your virtual environment if you haven't and in the Python interactive shell:

```python
>>> from how_long import timer
>>>
>>> @timer
... def test_function():
...     [i for i in range(10000)]
...
>>> test_function()
Execution Time: 705 ms.

```

Run the tests and if everything is fine, move on.

## Building and Publishing

Finally, the time to make this project available to the world has come! First, make sure you have an account on [Pypi](https://pypi.or), and if not, [register](https://pypi.org/account/register/) one. Remember that the package name must be unique, if unsure go and use the [search](https://pypi.org/search/?q=) to check it out.

### Build

The `poetry build` command builds the source and wheels archives that will letter be uploaded as the source of the project:

![poetry build](img/poetry_build.png)

The *how_long.egg-info* directory will be created.

## Publish

This command publishes the package to *Pypi* and automatically register it before uploading if this is the first time it is submitted:

![poetry publish](img/poetry_publish.png)

Enter your credentials and if everything is ok, [browse](https://pypi.org/project/how-long/) your project and you'll see something like this:

![pipy how-long](img/pypi.png)

Congratulations!! you can now `poetry add how-long` or `pip install how-long` or `pipenv install how-long`.

## Conclusion

| Command                           | Description                                            |
| --------------------------------- | ------------------------------------------------------ |
| `poetry new [package-name]`       | Start a new Python Project.                            |
| `poetry init`                     | Create a *pyproject.toml* file interactively.          |
| `poetry install`                  | Install the packages inside the *pyproject.toml* file. |
| `poetry add [package-name]`       | Add a package to a Virtual Environment.                |
| `poetry add -D [package-name]`    | Add a dev package to a Virtual Environment.            |
| `poetry remove [package-name]`    | Remove a package from a Virtual Environment.           |
| `poetry remove -D [package-name]` | Remove a dev package from a Virtual Environment.       |
| `poetry update`                   | Get the latest versions of the dependencies            |
| `poetry shell`                    | Spawns a shell within the virtual environment.         |
| `poetry build`                    | builds the source and wheels archives.                 |
| `poetry publish`                  | Publishes the package to Pypi.                         |
| `poetry self:update`              | Update poetry to the latest stable version.            |