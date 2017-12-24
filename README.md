# Python 101

## Table of contents:

1. [Chapter 1: IDLE Programming](#Chapter1)
2. [Chapter 2: All About Strings](#Chapter2)
3. [Chapter 3: Lists, Tuples and Dictionaries](#Chapter3)
4. [Chapter 4: Conditional Statements](#Chapter4)
5. [Chapter 5: Loops](#Chapter5)
6. [Chapter 6: Python Comprehensions](#Chapter6)
7. [Chapter 7: Exception Handling](#Chapter7)
8. [Chapter 8: Working with Files](#Chapter8)

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

Python do not have the case/switch construction, but has the if/elif/else statement. Python cares about indentation (4 spaces by recomendation, not tabs), it might not run if the code is not properly indented:

```python
textVar = input("Introduce the value for someVar") #In python 2.x this function is called raw_input, takes the user input
someVar= int(textVar)
if someVar > 2:
    print("someVar is greater than 2")
elif 1 <= someVar <= 2:
    print("someVar is in between 1 and 2")
else:
    print("someVar is less than 1")
    
my_list=[1,2,3,4]
x=10
z=11
if x not in my_list and z!=10:
    print("This is True!")
```

In python an empty string, tuple or list, None and False evaluates to False. Checking for equality between an empty List and Tuple, or an empty string, will return false. An important construct is this one here:

```python
if __name__ == "__main__":
    # Do Something
```
This tells Python that you only want to run the following code if this program is executed as a standalone file.

## Chapter 5: Loops<a name="Chapter5"></a>

Python has for and while loops. _range([<init value>], <end value>, [<step>])_ creates a list from the init value (optional) to the end value (not included), using the step (optional). This can be used in the for constructs:

```python
for number in range(5):
    print(number)
```

Dictionaries can be iterated too:

```python
myDir={"one": 1, "two": 2, "three": 3}
for key in myDir:
    if key == "two":
        break
else:        
    print("Key two not found") 
```

In the statement above, the else in the loop is only printed if the loop completes successfully. Python has also the % (modulus) operator which returns the remainder of a division. The while loop is similar to the for:

```python
number=0
while number < 10:
    print(number)
    if number==5: 
        break # Exits the while loop. Use 'continue' to jump to the next iteration
    number +=1 # python also supports -= and *=
```

## Chapter 6: Python Comprehensions<a name="Chapter6"></a>

A list comprehension is basically a one line for loop that produces a Python list data structure:

```python
x=[i for i in range(5)]

y = ['1', '2', '3', '4', '5']
z = [int(i) for i in y if i %2 == 0]
```

It can be handy to use this to do a flat map:

```python
vec = [[1,2,3], [4,5,6], [7,8,9]]
flattenList=[num for elem in vec for num in elem] # creates [1,2,3,4,5,6,7,8,9]
```

Dictionary comprehensions started life in Python 3.0, but were backported to Python 2.7. An example:

```python
print( {i: str(i) for i in range(5)} ) # Creates a dictionary with {0: '0', 1: '1', 2: '2', 3: '3', 4: '4'}
```

To create a set (collection that does not allow duplicates) comprehension, we create like if it was a list, but replace the _\[_ and _\]_ characters by the _{_ and _}_ characters.

```python
my_list=[1,2,2,3,4,5,5,7,8]
my_set = {x for x in my_list} # This is similar to set(my_list) which yields set([1,2,3,4,5,7,8])
```

## Chapter 7: Exception Handling<a name="Chapter7"></a>

The most common Exceptions in python are:
    
    - Exception (this is what almost all the others are built off of)
    - AttributeError - Raised when an attribute reference or assignment fails.
    - IOError - Raised when an I/O operation (such as a print statement, the built-in open() function or a method of a file object) fails for an I/O-related reason, e.g., “file not found” or “disk full”.
    - ImportError-Raisedwhenanimportstatementfailstofindthemoduledefinition or when a from ... import fails to find a name that is to be imported.
    - IndexError - Raised when a sequence subscript is out of range.
    - KeyError - Raised when a mapping (dictionary) key is not found in the set of existing keys.
    - KeyboardInterrupt - Raised when the user hits the interrupt key (normally Control-C or Delete).
    - NameError - Raised when a local or global name is not found.
    - OSError - Raised when a function returns a system-related error.
    - SyntaxError - Raised when the parser encounters a syntax error.
    - TypeError - Raised when an operation or function is applied to an object of inappropriate type. The associated value is a string giving details about the type mismatch.
    - ValueError - Raised when a built-in operation or function receives an argument that has the right type but an inappropriate value, and the situation is not described by a more precise exception such as IndexError.
    - ZeroDivisionError - Raised when the second argument of a division or modulo operation is zero.
    
The construct in python is the following:

```python
try:
    # some operation
except ExceptionType1:
    # The code to execute
except (ExceptionType2, ExceptionType3):
    # Multi exception catch 
finally:
    # Some code to execute
```

The try/except statement also has an else clause. The else will only run if there are no errors raised.

```python
my_dict = {"a":1, "b":2, "c":3}
try:
    value = my_dict["a"]
except KeyError:
    print("A KeyError occurred!")
else:
    print("No error occurred!")
finally:
    print("The finally statement ran!")
```

## Chapter 8: Working with Files<a name="Chapter8"></a>
