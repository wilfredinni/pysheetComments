In the [first part](https://www.pythoncheatsheet.org/blog/python-projects-with-poetry-and-vscode-part-1), we learned what is the `pyproject.toml` file and how to use it, used [Poetry](https://poetry.eustace.io/) to start a new project, create a Virtual Environment and add and remove dependencies. We did all of this with the following commands:

| Command                           | Description                                            |
| --------------------------------- | ------------------------------------------------------ |
| `poetry new [package-name]`       | Start a new Python Project.                            |
| `poetry init`                     | Create a *pyproject.toml* file interactively.          |
| `poetry install`                  | Install the packages inside the *pyproject.toml* file. |
| `poetry add [package-name]`       | Add a package to a Virtual Environment.                |
| `poetry add -D [package-name]`    | Add a dev package to a Virtual Environment.            |
| `poetry remove [package-name]`    | Remove a package from a Virtual Environment.           |
| `poetry remove -D [package-name]` | Remove a dev package from a Virtual Environment.       |

In this second part we'll:

- Add our virtual Environment to [VSCode](https://code.visualstudio.com/).
- Integrate our dev dependencies with the editor.
  - *Flake8*
  - *Black*
  - *Pytest*

Before we start, make sure you have installed [VSCode](https://code.visualstudio.com/), added the [Python](https://marketplace.visualstudio.com/itemdetails?itemName=ms-python.python) extension and that you have followed and/or understood the [first part](https://www.pythoncheatsheet.org/blog/python-projects-with-poetry-and-vscode-part-1) of this article.

## Setting Up Poetry on VSCode 

A few days have passed since the first part, so it may be a good idea to check for new versions of our dependencies. Open your terminal and navigate inside your project folder and type the `poetry update` command:

![poetry update](img/update.png)

Ok, to this day there are no new versions available.

When you create a Virtual Environment with the *venv* command, VSCode will automatically add it as the default Python Environment for that project. When working With *Poetry*, the first time we will need to open the terminal and inside our project folder:

```
$ poetry shell
$ code .
```

The first command, `poetry shell`, will spawn us inside our virtual environment, and `code .` will open the current folder inside VSCode.

![vscode](img/vscode.png)

Open the *how-long* folder (or the one with your project name) using the left panel and alongside to `__init__.py`, create a `how-long.py` file. In the bottom left corner you'll see the current Python Environment:

![python version](img/python-code.png)

Click it and a list of available Python Environments will display. Choose the one that has the name of your project in it:

![choose python](img/choose-environment.png)

Now, let's integrate our dev dependencies, *Flake8*, *Black*, and *Pytest* to Visual Studio Code.

### Flake8

*Flake8* will provide our projects with *linting* capabilities. In other words, syntax and style errors, and thanks to VSCode, we will know them as we type.

By default, the Python extension comes with *Pylint* enabled, which is powerful but complex to configure. To change to *Flake8* make a change to any Python file and save it, in the bottom right corner a popup message will show:

![flake8](img/select-linter.png)

Click on select linter and choose *flake8* from the list. Now, VSCode will tell us our syntax style problems, in green or red depending on its severity, always with a nice description of what is wrong:

![linting](img/linting.png)

Seems like we have two problems: we are missing a blank line at the end of our file (style) and we forgot to add quotes to our *Hello, World*. Fix these errors and all the warnings will disappear.

### Black

*Black* is a code formatter, a tool that will look at our code and automatically format it in compliance with the [PEP 8](https://www.python.org/dev/peps/pep-0008/) style guide, the same *PEP* that uses *Flake8* to lint our style errors.

Hold `shift + cmd/ctrl + p` to open the Command Palette, type *format document*, and press enter. A new popup message will appear:

![black formatter popup](img/format-popup.png)

Select *Use Black*. Now copy this poorly formatted code into your python file:

```python
for i in range(5):         # this comment has too many spaces
      print(i)  # this line has 6 space indentation.
```

What an ugly and full of errors piece of s***... code. Try formatting it again and see how Black fixes all of them for you!

Another thing we can do is to configure VSCode so that every time we save, *Black* will automatically format our code. Hold `cmd/ctrl + ,` to open the Settings. Make sure you are in the *Workspace Settings*, search for *format on save* and activate the checkbox:

![format on save](img/format-on-save.png)

Lastly, *Black* defaults to 88 characters per line in contrast with the 80 allowed by *Flake8*, so to avoid conflicts, open `.vscode` folder and add the following at the end of the *settings.json* file:

```json
{
    ...
    "python.linting.flake8Args": [
        "--max-line-length=88"
    ],
}
```

![black-settings](img/black-settings.png)

### Pytest

If you are serious about programming, it is crucial for you to learn how to test your projects. It's an incredibly useful skill that will allow you to write and deliver programs with confidence by reducing the possibility of catastrophic bugs appearing after shipping.

[Pytest](https://docs.pytest.org/en/latest/) is a very popular and user-friendly framework for writing tests. We [already installed](https://www.pythoncheatsheet.org/blog/python-projects-with-poetry-and-vscode-part-1#Dependency-Management) it so we will also integrate it with *VSCode*.

Open the *tests* folder and select the `test_how_long.py` file. *Poetry* already gives us our first test:

```python
# test_how_long.py
from how_long import __version__


def test_version():
    assert __version__ == '0.1.0'
```

This test import the `__version__` variable from the `__init__.py` file that is inside the *how_long* folder and asserts that the current version is *0.1.0*. Open your integrated terminal by going to *Terminal > New Terminal* and type:

```
$ pytest
```

The Output will look like this:

![pytest](img/pytest-terminal.png)

Ok, everything is fine. Open your Command Palette with `cmd/ctrl + p`:

- Write *unit* and select *Python: Configure Unit Tests*.
- Select *pytest*.
- Choose the directory in which the test are stored, *tests* in our case.

Three things happened:

- A new button appeared at the status bar: *Run Tests*. This is the same as typing *pytest* in the terminal. Press it and select *Run All Unit Tests*. When finished, it will inform you the number of tests that passed and the tests that not.

    ![test status bar](img/test-statusbar.png)

- A new icon at the left bar. If you click on it a panel displaying all the test and letting you run them individually will appear.

    ![test side panel](img/test-side-panel.png)

- Inside the test file, new options will be displayed before every function: a check icon will appear if is ok, and an *x* otherwise. It also allow you to run specific tests.

    ![test inline](img/test-inline.png)

## Conclusion

This was originally a two part article, 