# Python Comprehensions: A step by step Introduction

_List Comprehensions_ are a special kind of syntax that let us create lists out of other lists ([Wikipedia](https://en.wikipedia.org/wiki/List_comprehension), [The Python Tutorial](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions)). They are incredible useful when dealing with numbers and with one or two level of nested _for loops_, but beyond that, they can become a little too hard to read.

In this article, we are going to make some _For Loops_ and rewrite them, step by step, into _Comprehensions_.

## Basics

The truth is _List Comprehensions_ are not too complex, but they are still a bit difficult to understand at first because they may look a little weird. Why? Well, the order in which they are written is the **_opposite_** of what we usually see in a _For Loop_.

```python
names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']

for n in names:
    print(n)

# Charles
# Susan
# Patrick
# George
# Carol
```

To do the same but with a _List Comprehension_, we start at the very end of the _loop_:

```python
names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']
[print(n) for n in names]

# Charles
# Susan
# Patrick
# George
# Carol
```

Notice how we inverted the order:

- First, we determine what the output of the loop will be `[print(n) ...]`.
- And then we define the variable that will represent each of the items and state the [List](https://www.pythoncheatsheet.org/#Lists) (or [Set](https://www.pythoncheatsheet.org/#Set-comprehension)/[Dictionary](https://www.pythoncheatsheet.org/#Dictionaries-and-Structuring-Data)) we will work on `[... for n in names]`.

Not that difficult right?

## Creating a new List from a Comprehension

> This is the primary use of a _List Comprehension_. Other usages may result in a hard-to-read code for you and others.

This is how we create a new list from an existing collection with a _For Loop_:

```python
names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']

new_list = []
for n in names:
    new_list.append(n)

print(new_list)
# ['Charles', 'Susan', 'Patrick', 'George', 'Carol']
```

And this is how we do the same with a _List Comprehension_:

```python
names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']

new_list = [n for n in names]
print(new_list)
# ['Charles', 'Susan', 'Patrick', 'George', 'Carol']
```

The reason we can do this is that a _List Comprehension_ standard behavior is to return a list:

```python
>>> names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']
>>> [n for n in names]
['Charles', 'Susan', 'Patrick', 'George', 'Carol']
```

## Adding Conditionals

What if we want `new_list` to have only the names that start with `C`? With a _For Loop_ we would do it like this:

```python
names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']

new_list = []
for n in names:
    if n.startswith('C'):
        new_list.append(n)

print(new_list)
# ['Charles', 'Carol']
```

In a _List Comprehension_, we add the if statement at its end:

```python
names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']

new_list = [n for n in names if n.startswith('C')]
print(new_list)
# ['Charles', 'Carol']
```

A lot more readable, right?

## Formatting long List Comprehensions

This time, we want `new_list` to have not only the names that start with a `C` but also those that end with an `e` and contain a `k`:

```python
names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']

new_list = [n for n in names if n.startswith('C') or n.endswith('e') or 'k' in n]
print(new_list)
# ['Charles', 'Patrick', 'George', 'Carol']
```

Well, that is messy. Fortunately, it is possible to break _Comprehensions_ in different lines:

```python
new_list = [n for n in names
            if n.startswith('C')
            or n.endswith('e')
            or 'k' in n]
```

## Set and Dict Comprehensions

If you learned the basics of _List Comprehensions_... Congratulations! You just did it with [Sets](https://www.pythoncheatsheet.org/#Set-comprehension) and [Dictionaries](https://www.pythoncheatsheet.org/#Dictionaries-and-Structuring-Data)!

Set comprehension:

```python
my_set = {"abc", "def"}

# Here, we create a new set with uppercase elements with a for loop
new_set = set()
for s in my_set:
    new_set.add(s.upper())

print(new_set)
# {'DEF', 'ABC'}

# The same, but with a set comprehension
new_set = {s.upper() for s in my_set}
print(new_set)
# {'DEF', 'ABC'}
```

Dict comprehension:

```python
my_dict = {'name': 'Christine', 'age': 98}

# A new dictionary out of an existing one with a for loop
new_dict = {}
for key, value in my_dict.items():
    new_dict[key] = value

print(new_dict)
# {'name': 'Christine', 'age': 98}

# Using a dict comprehension
new_dict = {key: value for key, value in my_dict.items()}  # Notice the ":"
print(new_dict)
# {'name': 'Christine', 'age': 98}
```

> Recommended Article: [Python Sets: What, Why and How ](https://www.pythoncheatsheet.org/blog/python-sets-what-why-how).

## Conclusion

I don't know about you, but every time I learn something new there is this urge to use it right away. When that happens, I force myself to stop and think for a moment... Should I change this big, nested and already messy looking _For Loop_ to a _List Comprehension_? Probably not.

> Readability counts. [The Zen of Python](https://www.python.org/dev/peps/pep-0020/).

Any doubt or suggestion? Please leave a comment and have a nice day!
