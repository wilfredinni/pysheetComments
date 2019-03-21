A *list comprehension* is a special syntax that let us create lists out of other lists in a concise way ([Wikipedia](https://en.wikipedia.org/wiki/List_comprehension), [The Python Tutorial](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions) ). They are incredible useful when dealing with numbers and one or two level of nested for loops. Beyond that, they become a little too harder to read.

In this short article we are going to make some for loops and convert them, step by step, into comprehension. At the end and as a bonus, we will understand [sets](https://www.pythoncheatsheet.org/#Set-comprehension) and [dicts](https://www.pythoncheatsheet.org/#Dict-comprehension) comprehensions.

## Basics

I think the reason why list comprehensions are a bit difficult to understand at first is because they look... weird. Why? The ***order*** in which they are written is ***inverted*** with respect to a for loop.

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

We have:

- `names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']`: Defined the list we are going to work with.
- `for n in names:`: Created a variable (`n`) that will contain each of the items in the `names` list.
- `print(n)`: Then, we do something with it. In this case, we just print the current value of `n`.

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

## Appending values to a new List

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

We can assign it to a variable because a list comprehension standard behavior is to return a list:

```python
>>> names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']
>>> [n for n in names]
['Charles', 'Susan', 'Patrick', 'George', 'Carol']
```

Really nice.

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

## Formating long List Comprehensions

This time we want our new list to have not only the names that start with a `C` but also those that end with an` e` and contain a `k`:

```python
names = ['Charles', 'Susan', 'Patrick', 'George', 'Carol']

new_list = [n for n in names if n.startswith('C') or n.endswith('e') or 'k' in n]
print(new_list)
# ['Charles', 'Patrick', 'George', 'Carol']
```

Well, that is messy. Fortunately, it is possible to break comprehensions in different lines:

```python
new_list = [n for n in names if n.startswith('C')
            or n.endswith('e') or 'k' in n]
```

## What about sets and dictionaries

If you have learned the basics of list comprehensions... Congratulations! you just have done it with list and sets!

```python
# set comprehension
>>> b = {"abc", "def"}
>>> {s.upper() for s in b}
{"ABC", "DEF}

# dict comprehension
>>> c = {'name': 'Pooka', 'age': 5}
>>> {v, k for k, v in c.items()}
{'Pooka': 'name', 5: 'age'}
```

> Recommended Article: [Python Sets: What, Why and How ](https://www.pythoncheatsheet.org/blog/python-sets-what-why-how).

## Conclusion

Every time we learn something new there is this natural behavior that urges us to use it right away. When that happens (because it happens a lot in this field) we have to stop for a moment and think... Is really ok to change this big, nested and already messy looking *for loop* to a comprehension? Probably not, because you know:

> Readability counts (import this).

Any doubt or suggestion? Please leave a comment and have a nice day!
