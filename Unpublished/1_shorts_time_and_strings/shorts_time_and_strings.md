# Python Strings and Datetime Objects

Python make it easy to transform between _strings_, _datetime objects_ and vice versa, just take a good look at the `datetime` module included in the standard library.

## From Datetime object to String

```python
date_object.strftime(format)
```

Examples

```python
from datetime import datetime

# get the current datetime
now = datetime.now()
print(now)
# output: 2021-07-12 14:38:37.816707

print(type(now))
# output: <class 'datetime.datetime'>

# Lets start transforming datetime objects to strings
example_1 = now.strftime("%d-%b-%Y")
print(example_1)
# output: '12-Jul-2021'
print(type(example_1))
# output: <class 'str'>

example_2 = now.strftime("%d-%m-%Y")
# output: '12-07-2021'

example_3 = now.strftime("%m-%d-%Y")
# output: '07-12-2021'

example_4 = now.strftime("%m/%d/%Y")
# output: '07/12/2021'

example_5 = now.strftime("%b/%d/%Y - %H:%M:%S")
# output: 'Jul/12/2021 - 14:38:37'
```

## From String to Datetime object

This time we need to pass two parameters to `strptime()`, **the date as a string** and **the format**:

```python
datetime.strptime(date_string, format)
```

Examples

```python
from datetime import datetime

datetime_str = '12-Jul-2021'
datetime.strptime(datetime_str, '%d-%b-%Y')
# output: datetime.datetime(2021, 7, 12, 0, 0)

datetime_str = 'Jul/12/2021 - 14:38:37'
datetime.strptime(datetime_str, "%b/%d/%Y - %H:%M:%S")
# output: datetime.datetime(2021, 7, 12, 14, 38, 37)
```

## strftime() and  strptime() Format Codes

| Directive | Meaning                                                                                                                                                                          | Example                                               |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| `%a`      | Weekday as locale’s abbreviated name.                                                                                                                                            | Sun, Mon, …, Sat (en_US)                              |
| `%A`      | Weekday as locale’s full name.                                                                                                                                                   | Sunday, Monday, …, Saturday (en_US)                   |
| `%w`      | Weekday as a decimal number, where 0 is Sunday and 6 is Saturday.                                                                                                                | 0, 1, …, 6                                            |
| `%d`      | Day of the month as a zero-padded decimal number.                                                                                                                                | 01, 02, …, 31                                         |
| `%b`      | Month as locale’s abbreviated name.                                                                                                                                              | Jan, Feb, …, Dec (en_US)                              |
| `%B`      | Month as locale’s full name.                                                                                                                                                     | January, February, …, December (en_US)                |
| `%m`      | Month as a zero-padded decimal number.                                                                                                                                           | 01, 02, …, 12                                         |
| `%y`      | Year without century as a zero-padded decimal number.                                                                                                                            | 00, 01, …, 99                                         |
| `%Y`      | Year with century as a decimal number.                                                                                                                                           | 0001, 0002, …, 2013, 2014, …, 9998, 9999              |
| `%H`      | Hour (24-hour clock) as a zero-padded decimal number.                                                                                                                            | 00, 01, …, 23                                         |
| `%I`      | Hour (12-hour clock) as a zero-padded decimal number.                                                                                                                            | 01, 02, …, 12                                         |
| `%p`      | Locale’s equivalent of either AM or PM.                                                                                                                                          | AM, PM (en_US)                                        |
| `%M`      | Minute as a zero-padded decimal number.                                                                                                                                          | 00, 01, …, 59                                         |
| `%S`      | Second as a zero-padded decimal number.                                                                                                                                          | 00, 01, …, 59                                         |
| `%f`      | Microsecond as a decimal number, zero-padded on the left.                                                                                                                        | 000000, 000001, …, 999999                             |
| `%z`      | UTC offset in the form `±HHMM[SS[.ffffff]]` (empty string if the object is naive).                                                                                               | (empty), +0000, -0400, +1030, +063415, -030712.345216 |
| `%Z`      | Time zone name (empty string if the object is naive).                                                                                                                            | (empty), UTC, GMT                                     |
| `%j`      | Day of the year as a zero-padded decimal number.                                                                                                                                 | 001, 002, …, 366                                      |
| `%U`      | Week number of the year (Sunday as the first day of the week) as a zero padded decimal number. All days in a new year preceding the first Sunday are considered to be in week 0. | 00, 01, …, 53                                         |
| `%W`      | Week number of the year (Monday as the first day of the week) as a decimal number. All days in a new year preceding the first Monday are considered to be in week 0.             | 00, 01, …, 53                                         |
| `%c`      | Locale’s appropriate date and time representation.                                                                                                                               | Tue Aug 16 21:30:00 1988 (en_US)                      |
| `%x`      | Locale’s appropriate date representation.                                                                                                                                        | 08/16/88 (None)                                       |
| `%X`      | Locale’s appropriate time representation.                                                                                                                                        | 21:30:00 (en_US)                                      |
| `%%`      | A literal `'%'` character.                                                                                                                                                       | %                                                     |

Read more at the [Python documentation](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes).
