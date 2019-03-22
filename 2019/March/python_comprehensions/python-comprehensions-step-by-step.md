*List Comprehensions* are a special kind of syntax that let us create lists out of other lists in a concise way ([Wikipedia](https://en.wikipedia.org/wiki/List_comprehension), [The Python Tutorial](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions)). They are incredible useful when dealing with numbers and with one or two level of nested for loops. Beyond that, they can become a little too hard to read.

In this short Article we are going to make some for loops and convert them, step by step, into *comprehensions*, and if everything goes well, at the end and as a bonus, we will understand [sets](https://www.pythoncheatsheet.org/#Set-comprehension) and [dicts](https://www.pythoncheatsheet.org/#Dictionaries-and-Structuring-Data) comprehensions too 🤓.

## Basics

We already said it: a *List Comprehension* allows us to create lists out of other lists. And even when they are not too complex, they are still a bit difficult to understand at first because, I think, they look... weird. Why? Well, the order in which they are written is the ***opposite*** of what we usually see in a *for loop*.

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

In this loop we have:

- `names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']` Defined the list we are going to work with.
- `for n in names:` Created a variable (`n`) that will contain each of the items in the `names` list.
- `print(n)` Done something with that variable. In this case, we just print the current value of `n`.

In a list comprehension we start at the very end of the for loop:

```python
names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']
[print(n) for n in names]

# Charles
# Susan
# Patrick
# George
# Carol
```

Notice how we inverted the order: First we defined what the output of the loop will be (`print(n)`), and then we created our variable and state the list we will work on (`for n in names`). Not that difficult right?

## Creating a new List from a Comprehension

This is how we create a new list from an existing collection with a for loop:

```python
names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']

new_list = []
for n in names:
    new_list.append(n)

print(new_list)
# ['Charles', 'Susan', 'Patrick', 'George', 'Carol']
```

And this is how we do the same with a list comprehension:

```python
names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']

new_list = [n for n in names]
print(new_list)
# ['Charles', 'Susan', 'Patrick', 'George', 'Carol']
```

We can assign it to `new_list` because a list comprehension standard behavior is to return a list:

```python
>>> names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']
>>> [n for n in names]
['Charles', 'Susan', 'Patrick', 'George', 'Carol']
```

Really nice right?

## Adding Conditionals

What if we want to append only the names that start with `C`? With a for loop we would do it like this:

```python
names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']

new_list = []
for n in names:
    if n.startswith('C'):
        new_list.append(n)

print(new_list)
# ['Charles', 'Carol']
```

In a list comprehension, we add the if statement at its ends:

```python
names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']

new_list = [n for n in names if n.startswith('C')]
print(new_list)
# ['Charles', 'Carol']
```

Isn't more readable this way? Comprehensions are the kings of short loops (!).

## Formating long List Comprehensions

This time, we want `new_list` to have not only the names that start with a `C` but also those that end with an` e` and contain a `k`:

```python
names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']

new_list = [n for n in names if n.startswith('C') or n.endswith('e') or 'k' in n]
print(new_list)
# ['Charles', 'Patrick', 'George', 'Carol']
```

Well, that is messy 🙄. Fortunately, it is possible to break comprehensions in different lines:

```python
new_list = [n for n in names if n.startswith('C')
            or n.endswith('e') or 'k' in n]
```

## sets and dict Comprehensions

If you have learned the basics of list comprehensions... Congratulations! you just have done it with [sets](https://www.pythoncheatsheet.org/#Set-comprehension) and [dicts](https://www.pythoncheatsheet.org/#Dictionaries-and-Structuring-Data)!


```python
>>> # set comprehension
>>> b = {"abc", "def"}
>>> {s.upper() for s in b}
{"ABC", "DEF}
>>>
>>> # dict comprehension
>>> c = {'name': 'Pooka', 'age': 5}
>>> {v, k for k, v in c.items()}
{'Pooka': 'name', 5: 'age'}
```

> Recommended Article: [Python Sets: What, Why and How ](https://www.pythoncheatsheet.org/blog/python-sets-what-why-how).

## Conclusion

I don't know about you, but every time I learn something new there is this urge to use it right away. When that happens (because it happens a lot in this field), I force myself to stop and think for a moment. And in this case, is it really ok to change this big, nested and already messy looking *for loop* to a comprehension? Probably not, because, you know:

> Readability counts (import this).

Any doubt or suggestion? Please leave a comment and have a nice day!