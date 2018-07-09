# Python Sets: What, Why and How

![sets](sets.png)

Python comes equipped with several built-in data types to help us organize our data. These structures include lists, dictionaries, tuples and **sets**.

From the Python 3 documentation:

> A set is an _unordered collection_ with no _duplicate elements_. Basic uses include _membership testing_ and _eliminating duplicate entries_. Set objects also support mathematical operations like _union_, _intersection_, _difference_, and _symmetric difference_.

In this article, we are going to review and see examples of every one of the elements listed in the above definition. Let's start right away and see how we can create them.

### Initializing a Set

There are two ways to create a set: one is to provide the built-in function `set()` with a list of elements, and the other is to use the curly braces `{}`. 

Initializing a set using the `set()` built-in function:

```python
>>> s1 = set([1, 2, 3])
>>> s1
{1, 2, 3}
>>> type(s1)
<class 'set'>
```

Initializing a set using curly braces `{}`

```python
>>> s2 = {3, 4, 5}
>>> s2
{3, 4, 5}
>>> type(s2)
<class 'set'>
>>>
```

As you can see, both options are valid. The problem comes when what we want is an empty one:

```python
>>> s = {}
>>> type(s)
<class 'dict'>
```
That's right, we will get a dictionary instead of a set if we use empty curly braces =)

It's a good moment to mention that for the sake of simplicity, all the examples provided in this article will use single digit integers, but sets can have all the [hashtable](https://docs.python.org/3/glossary.html#term-hashable) data types that Python support. In other words, integers, strings and tuples, but not _mutable_ items like _lists_ or _dictionaries_:

```python
>>> s = {1, 'coffee', [4, 'python']}
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'
```

Now that you know how to create a set and what type of elements it can contain, let's continue and see _why_ we should always have them in our toolkit.

## Why You Should Use Them

When writing code, you can do it in more than a single way. Some are considered to be pretty bad, and others, _clear, concise and maintainable_. Or "[_pythonic_](http://docs.python-guide.org/en/latest/writing/style/)". 

From the [The Hitchhiker’s Guide to Python](http://docs.python-guide.org/en/latest/):

> When a veteran Python developer (a Pythonista) calls portions of code not “Pythonic”, they usually mean that these lines of code do not follow the common guidelines and fail to express its intent in what is considered the best (hear: most readable) way.

Now, let's start exploring the way that Python sets can help us not just with readability, but also speeding up our programs execution time.

### Unordered Collection of Elements

First things first: you can't access a set element using indexes.

```python
>>> s = {1, 2, 3}
>>> s(0)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'set' object is not callable
>>>
```

Or modify them with slices:

```python
>>> s[0:2]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'set' object is not subscriptable
```

BUT, if what we need is to remove duplicates, or do mathematical operations like combining lists (unions), we can, and _SHOULD_ always use Sets. 

I have to mention that when iterating over, sets are outperformed by lists, so prefer them if that is what you need. Why? well, this article does not intend to explain the inner workings of sets, but if you are interested, here are a couple of links where you can read about it: 

- [TimeComplexity](https://wiki.python.org/moin/TimeComplexity)
- [How is set() implemented?](https://stackoverflow.com/questions/3949310/how-is-set-implemented)
- [Python Sets vs Lists](https://stackoverflow.com/questions/2831212/python-sets-vs-lists)
- [Is there any advantage or disadvantage to using sets over list comps to ensure a list of unique entries?](https://mail.python.org/pipermail/python-list/2011-June/606738.html)

### No Duplicate Items

While writing this I cannot stop thinking in all the times I used the _for_ loop and the _if_ statement to check and remove duplicate elements in a list. My face turns red remembering that, more than once, I wrote something like this:

```python
>>> my_list = [1, 2, 3, 2, 3, 4]
>>> no_duplicate_list = []
>>> for item in my_list:
...     if item not in no_duplicate_list:
...             no_duplicate_list.append(item)
...
>>> no_duplicate_list
[1, 2, 3, 4]
```

Or used a list comprehension:

```python
>>> my_list = [1, 2, 3, 2, 3, 4]
>>> no_duplicate_list = []
>>> [no_duplicate_list.append(item) for item in my_list if item not in no_duplicate_list]
[None, None, None, None]
>>> no_duplicate_list
[1, 2, 3, 4]
```

But it's ok, nothing of that matters anymore because we now have the sets in our arsenal:

```python
>>> my_list = [1, 2, 3, 2, 3, 4]
>>> no_duplicate_list = list(set(my_list))
>>> no_duplicate_list
[1, 2, 3, 4]
>>>
```

Now let's use the _timeit_ module and see the excecution time of lists and sets when removing duplicates:

```python
>>> from timeit import timeit
>>> def no_duplicates(list):
...     no_duplicate_list = []
...     [no_duplicate_list.append(item) for item in list if item not in no_duplicate_list]
...     return no_duplicate_list
...
>>> # first, let's see how the list perform:
>>> print(timeit('no_duplicates([1, 2, 3, 1, 7])', globals=globals(), number=10000))
0.01879758248981034
```

```python
>>> from timeit import timeit
>>> # and the set:
>>> print(timeit('list(set([1, 2, 3, 1, 2, 3, 4]))', number=1000))
0.0010220493243764395
>>> # faster and cleaner =)
```

Not only we write _fewer lines_ with sets than with lists comprehensions, we also obtain more _readable_ and _performant_ code.

From the [Zen of Python](https://www.python.org/dev/peps/pep-0020/):

> Beautiful is better than ugly. <br>
Explicit is better than implicit.<br>
Simple is better than complex.<br>
Flat is better than nested.

Aren't sets are just Beautiful, Explicit, Simple and Flat?  =) 

### Membership  Tests

Every time we use an _if_ statement to check if an element is, for example, in a list, you are doing a membership test:

```python
my_list = [1, 2, 3]
>>> if 2 in my_list:
...     print('Yes, this is a membership test!')
...
Yes, this is a membership test!
```

And sets are more performant than lists when doing them:

```python
>>> from timeit import timeit
>>> def in_test(iterable):
...     for i in range(1000):
...             if i in iterable:
...                     pass
...
>>> timeit('in_test(iterable)',
... setup="from __main__ import in_test; iterable = list(range(1000))",
... number=1000)
12.459663048726043
```

```python
>>> from timeit import timeit
>>> def in_test(iterable):
...     for i in range(1000):
...             if i in iterable:
...                     pass
...
>>> timeit('in_test(iterable)',
... setup="from __main__ import in_test; iterable = set(range(1000))",
... number=1000)
0.12354438152988223
>>>
```
Note: the avove tests come from [this](https://stackoverflow.com/questions/2831212/python-sets-vs-lists) StackOverflow thread.

So if you are doing comparisons like this in huge lists, it should speed you a good bit if you convert that list into a set.

## How to Use Them

Now that you know what a set is and why you should use them, let's do a quick tour and see how can we modify and operate with them.

### Adding Elements

Depending on the number of elements to add, we will have to choose between the  `add()` and `update()` methods.

`add()` will add a single element:

```python
>>> s = {1, 2, 3}
>>> s.add(4)
>>> s
{1, 2, 3, 4}
```

And `update()` multiple ones:

```python
>>> s = {1, 2, 3}
>>> s.update([2, 3, 4, 5, 6])
>>> s
{1, 2, 3, 4, 5, 6} 
```

Remember, sets remove duplicates.

### Removing Elements

If you want to be alerted when your code tries to remove an element that is not in the set, use `remove()`. Otherwise, `discard()` provides a good alternative:

```python
>>> s = {1, 2, 3}
>>> s.remove(3)
>>> s
{1, 2}
>>> s.remove(3)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 3
```

`discard()` won't raise any errors:

```python
>>> s = {1, 2, 3}
>>> s.discard(3)
>>> s
{1, 2}
>>> s.discard(3)
>>> # nothing happens!
```

We can also use `pop()` to randomly discard an element:

```python
>>> s = {1, 2, 3, 4, 5}
>>> s.pop()  # removes an arbitrary element
1
>>> s
{2, 3, 4, 5}
```

Or `clear()` to remove all the values from a set:

```python
>>> s = {1, 2, 3, 4, 5}
>>> s.clear()  # discard all the items
>>> s
set()
```

### union()

`union()` or `|` will create a new set that contains all the elements from the sets we provide:

```python
>>> s1 = {1, 2, 3}
>>> s2 = {3, 4, 5}
>>> s1.union(s2)  # or 's1 | s2'
{1, 2, 3, 4, 5}
```

### intersection()

`intersection`  or `&`  will return a set containing only the elements that are common in all of them:

```python
>>> s1 = {1, 2, 3}
>>> s2 = {2, 3, 4}
>>> s3 = {3, 4, 5}
>>> s1.intersection(s2, s3)  # or 's1 & s2 & s3'
{3}
```

### difference()

Using `diference()` or `-`, creates a new set with the values that are in "s1" but not in "s2":

```python
>>> s1 = {1, 2, 3}
>>> s2 = {2, 3, 4}
>>> s1.difference(s2)  # or 's1 - s2'
{1}
```

### symmetric_diference()

`symetric_difference` or `^` will return all the values that are not common between the sets.

```python
>>> s1 = {1, 2, 3}
>>> s2 = {2, 3, 4}
>>> s1.symmetric_difference(s2)  # or 's1 ^ s2'
{1, 4}
```

## Conclusions

I hope that after reading this article you know what a set is, how to manipulate their elements and the operations they can perform. Knowing when to use a set will definitely help you write cleaner code and speed up your programs.

If you have any doubts, please leave a comment and I will gladly try to answer them. Also, don´t forget that if you already understand sets, they have their own [place](https://www.pythoncheatsheet.org/#sets) in the [Python Cheatsheet](https://www.pythoncheatsheet.org/), where you can have a quick reference and refresh what you already know.