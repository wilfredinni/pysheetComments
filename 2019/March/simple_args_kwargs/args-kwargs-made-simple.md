I do not know about you, but every time I saw some function with `*args` and `**kwargs` as parameters, I'd get a little scared. I've even "used" them while doing some backend work with Django without understanding a thing. If you're a self-taught developer like me, I know you've been there too.

A few months ago I decided to stop being negligent and started to research it. To my surprise, they were very easy to grasp when playing with the interpreter but not so much when reading about them. So, I wrote this post trying to explain [args and kwargs](https://www.pythoncheatsheet.org/#args-and-kwargs) the way I would have liked someone explained them to me.

## Basics

The first thing you need to know is that args and kwargs lets you pass an undefined number of `arguments` and `keywords` when calling a [function](https://www.pythoncheatsheet.org/#Functions):

```python
def some_function(*args, **kwargs):
    pass

# call some_function with any number of arguments
some_function(arg1, arg1, arg2)

# call some_function with any number of keywords
some_function(key1=arg1, key2=arg2, key3=arg3)

# call both, arguments and keywords
some_function(arg, key1=arg1)

# or none
some_function()
```

Second, the words `args` and `kwargs` are conventions. This means they are not imposed by the interpreter, but considered good practice among the Python community:

```python
# This function would work just fine
def some_function(*arguments, **keywords):
    pass
```

So, how does Python know that we want our functions to accept multiple arguments and/or keywords? Yes, the answers are the `*` and `**` operators.

> A note about conventions:
>
> Even if the above function works, don't do it. Conventions are there to help you write readable code for you and anyone that might be interested in your project.
>
> Other conventions include the 4 space indentation, comments, and imports. If interested, check the [PEP 8 -- Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008/).

Now that you know the basics let's work with them.

## *Args

We now know how to pass multiple arguments using `*args` as a parameter to our functions, but, how do we work with them? Well, all the arguments are contained within the `args` variable as a [tuple](https://www.pythoncheatsheet.org/#Tuple-Data-Type):

```python
def some_function(*args):
    print(f'Arguments passed: {args} as {type(args)}')


some_function('arg1', 'arg2', 'arg3')
# Arguments passed: ('arg1', 'arg2', 'arg3') as <class 'tuple'>
```

We can iterate over them:

```python
def some_function(*args):
    for a in args:
        print(a)


some_function('arg1', 'arg2', 'arg3')
# arg1
# arg2
# arg3
```

Access the elements with an index:

```python
def some_function(*args):
    print(args[1])


some_function('arg1', 'arg2', 'arg3')  # arg1
```

Slice:

```python
def some_function(*args):
    print(args[0:2])


some_function('arg1', 'arg2', 'arg3')
# ('arg1', 'arg2')
```

Whatever you do with a [tuple](https://www.pythoncheatsheet.org/#Tuple-Data-Type), you can do it with `args`.

## **kwargs

While arguments are stored in the args variable as a tuple, keywords are stored within `kwargs`, but this time as a [dictionary](https://www.pythoncheatsheet.org/#Dictionaries-and-Structuring-Data) where the key is the keyword:

```python
def some_function(**kwargs):
    print(f'keywords: {kwargs} as {type(kwargs)}')


some_function(key1='arg1', key2='arg2', key3='arg3')
# keywords: {'key1': 'arg1', 'key2': 'arg2', 'key3': 'arg3'} as <class 'dict'>
```

Again, we can do with `kwargs` the same we would do with any [dictionary](https://www.pythoncheatsheet.org/#Dictionaries-and-Structuring-Data).

Iterate over:

```python
def some_function(**kwargs):
    for key, value in kwargs.items():
        print(f'{key}: {value}')


some_function(key1='arg1', key2='arg2', key3='arg3')
# key1: arg1
# key2: arg2
# key3: arg3
```

Use the get() method:

```python
def some_function(key, **kwargs):
    print(kwargs.get(key))


some_function('key3', key1='arg1', key2='arg2', key3='arg3')
# arg3
```

And a lot [more](https://www.pythoncheatsheet.org/#Dictionaries-and-Structuring-Data) =).

## Conclusion

`*args` and `**kwargs` may seem scary, but the true is that they are no that difficult to grasp and have the power to grant your functions with flexibility. If you feel like playing with them, [this](https://hub.mybinder.org/user/wilfredinni-python-cheatsheet-pjyv1in6/notebooks/jupyter_notebooks/18_args_and_kwargs.ipynb) is an online Jupyter Notebook for you to try.

Also, some examples make use of the `f-strings`, a relatively new way to format strings in Python (3.6+). If curious, [here](https://www.pythoncheatsheet.org/#Formatted-String-Literals-or-f-strings) you can read more about it.

If you have any doubt or suggestion, please leave a comment. Have a nice day!
