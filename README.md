# Python 101

## Table of contents:

1. [Chapter 1: IDLE Programming](#Chapter1)
2. [Chapter 2: All About Strings](#Chapter2)
3. [Chapter 3: Lists, Tuples and Dictionaries](#Chapter3)
4. [Chapter 4: Conditional Statements](#Chapter4)

## Chapter 1: IDLE Programming<a name="Chapter1"></a>

IDLE is the code editor of python, although in linux based OS you can execute python to display a command line. Python is an interpreted language run in the python interpreter.i.e.

```python
print("Hello World!") # versions 2.x don't use the parentheses
```

Importing packages in a python script adds new features to it.

## Chapter 2: All About Strings<a name="Chapter2"></a>

There is a String module in python to support extra functionality. You can create strings in python with single, doubles (if you need to put single quotes inside the string), triple quotes (multiline Strings) or using the _str_ function (to cast other types into strings). Strings are immutable in python, in Python 2.x, strings can only contain ASCII characters. If you require unicode in Python 2.x (in 3.x all strings are unicode), then you will need to precede your string with a u. i.e. `u"The string"`.
The string concatenation is done with '+', all strings are objects in python, some of its methods:

    - 'upper()': To upper case
    - 'lower()': To lower case
    - 'strip()': Removes trailing and leading whitespaces
    
To get the list of methods of the object, you can execute `dir(<object_name>)`, and to see the help of the method, simply run `help(<object_name>.<method_name>)` (this feature about asking python about itself is called introspection).
Strings can be sliced into substring, for example to get the first character of a string, you can do `myString[0:1]` or also `myString[:1]` as we can omit the start and/or the end of the string. If we want to take a string up to the last two characters we can do `myString[0:-2]`. To access individual characters do `myString[4]` where the number is the index where the character is. String substitution can be done like this:

```python
varValue = "other String"
"The string is %s and %s" % "some String"  # This last bit can also be a variable
"The string is %s and %s" % ("some String", varValue)
```

You can also insert integers (using `%i`), floats (using `%f`) and even format this numbers. i.e.:

```python
"Some number is:%.2f" % (1.237) #Will print 'Some number is: 1.24' as it does rounding
```

Another way of doing substitution:

```python
# Substitutes the var 'lang' n times and the 'n' int variable once.
print("%(lang)s is fun! Say %(n)i more time: %(lang)s is fun!" % {"lang":"Python", "n":1})
```

We can also use the _format_ method in python:

```python
"Python is as simple as {0}, {1}, {2}".format("a", "b", "c")
# Using a dictionary
xy = {"x":0, "y":10}
print("Graph a point at where x={x} and y={y}".format(**xy))
```

## Chapter 3: Lists, Tuples and Dictionaries<a name"Chapter3"></a>
Other important data types in python are:

### Lists
Similar to arrays in other languages. To create an empty List we can do it with `my_list = []` or `my_list1 = List()`. To put elements inside the list, you can do it like this:

```python
my_list1 = ["1"]
my_list2 = ["a", 1, "Python", 5]
my_list3 = [my_list1, my_list2] # This will be [["1"], ["a", 1, "Python", 5]]
```

To combine two lists, we do it with the extend method like in `my_list1.extend(my_list2)` which is a flat map operation. A list can be sorted with `myList.sort()` which sort the current list (returns None, but the original list is affected). A list can be sliced in the same way than a string.

### Tuples
Similar to list, but these are immutable objects. To create them use parentheses instead of brackets, like in `myTuple = (1,2,3)` or with the tuple method `myTuple = tuple(["a","b","c"]) # This is an example of casting a List to a tuple`.

### Dictionaries
A dictionary is basically a hash table or a hash map where the keys are unordered immutable types. use `dic.keys` to return the list of keys and `key in dic` to search for the key named _key_ inside the _dic_ dictionary (in spark 2.3 the method is `dic has_key key`). To create an empty dictionary use `myDictionary = {}` or `myDictionary = dic()`. Example of accessing a value inside a dictionay:

```python
my_dict = {"name":"Mike", "address":"123 Happy Way"}
my_dict["name"] # Will print 'Mike'
```

The keys function returns a list in python 2, and a _view_ in python 3 that would change if the map does too.

## Chapter 4: Conditional Statements<a name="Chapter4"></a>