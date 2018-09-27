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
9. [Chapter 9: Importing](#Chapter9)
10. [Chapter 10: Functions](#Chapter10)
11. [Chapter 11: Classes](#Chapter11)
12. [Chapter 12: Introspection](#Chapter12)
13. [Chapter 13: The csv Module](#Chapter13)
14. [Chapter 14: configparser](#Chapter14)
15. [Chapter 15: Logging](#Chapter15)
16. [Chapter 16: The os Module](#Chapter16)
17. [Chapter 17: The email/smtplib Module](#Chapter17)
18. [Chapter 18: The sqlite Module](#Chapter18)


## Chapter 1: IDLE Programming<a name="Chapter1"></a>

IDLE is the code editor of python, although in linux based OS you can execute python to display a command line. 
Python is an interpreted language run in the python interpreter.i.e.

```python
print("Hello World!") # versions 2.x don't use the parentheses
```

Importing packages in a python script adds new features to it.


## Chapter 2: All About Strings<a name="Chapter2"></a>

There is a String module in python to support extra functionality. You can create strings in python with single, 
doubles (if you need to put single quotes inside the string), triple quotes (multiline Strings) or using the _str_ 
function (to cast other types into strings). Strings are immutable in python, in Python 2.x, strings can only 
contain ASCII characters. If you require unicode in Python 2.x (in 3.x all strings are unicode), then you will need 
to precede your string with a u. i.e. `u"The string"`.
The string concatenation is done with '+', all strings are objects in python, some of its methods:

    - 'upper()': To upper case
    - 'lower()': To lower case
    - 'strip()': Removes trailing and leading whitespaces
    
To get the list of methods of the object, you can execute `dir(<object_name>)`, and to see the help of the method, 
simply run `help(<object_name>.<method_name>)` (this feature about asking python about itself is called introspection).
Strings can be sliced into substring, for example to get the first character of a string, you can do `myString[0:1]`
or also `myString[:1]` as we can omit the start and/or the end of the string. If we want to take a string up to the
last two characters we can do `myString[0:-2]`. To access individual characters do `myString[4]` where the number 
is the index where the character is (starting from 0). String substitution can be done like this:

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
Similar to arrays in other languages. To create an empty List we can do it with `my_list = []` or `my_list1 = List()`. 
To put elements inside the list, you can do it like this:

```python
my_list1 = ["1"]
my_list2 = ["a", 1, "Python", 5]
my_list3 = [my_list1, my_list2] # This will be [["1"], ["a", 1, "Python", 5]]
```

To combine two lists, we do it with the extend method like in `my_list1.extend(my_list2)` which is a flat map 
operation. A list can be sorted with `myList.sort()` which sort the current list (returns None, but the original 
list is affected). A list can be sliced in the same way than a string.

### Tuples
Similar to list, but these are immutable objects. To create them use parentheses instead of brackets, like in 
`myTuple = (1,2,3)` or with the tuple method `myTuple = tuple(["a","b","c"]) # Casting a List to a tuple`.

### Dictionaries
A dictionary is basically a hash table or a hash map where the keys are unordered immutable types. use `dic.keys` to 
return the list of keys and `key in dic` to search for the key named _key_ inside the _dic_ dictionary (in spark 2.3 
the method is `dic has_key key`). To create an empty dictionary use `myDictionary = {}` or `myDictionary = dic()`.
Example of accessing a value inside a dictionay:

```python
my_dict = {"name":"Mike", "address":"123 Happy Way"}
my_dict["name"] # Will print 'Mike'
```

The keys function returns a list in python 2, and a _view_ in python 3 that would change if the map does too.


## Chapter 4: Conditional Statements<a name="Chapter4"></a>

Python do not have the case/switch construction, but has the if/elif/else statement. Python cares about indentation 
(4 spaces by recomendation, not tabs), it might not run if the code is not properly indented:

```python
textVar=input("Introduce the value for someVar") #In python 2.x this function is called raw_input, takes the user input
someVar=int(textVar)
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

In python an empty string, tuple or list, None and False evaluates to False. Checking for equality between an empty 
List and Tuple, or an empty string, will return false. An important construct is this one here:

```python
if __name__ == "__main__":
    # Do Something
```
This tells Python that you only want to run the following code if this program is executed as a standalone file.


## Chapter 5: Loops<a name="Chapter5"></a>

Python has for and while loops. _range([<init value>], <end value>, [<step>])_ creates a list from the init value 
(optional) to the end value (not included), using the step (optional). This can be used in the for constructs:

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

In the statement above, the else in the loop is only printed if the loop completes successfully. Python has also the
 % (modulus) operator which returns the remainder of a division. The while loop is similar to the for:

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

To create a set (collection that does not allow duplicates) comprehension, we create like if it was a list, but replace 
the _\[_ and _\]_ characters by the _{_ and _}_ characters.

```python
my_list=[1,2,2,3,4,5,5,7,8]
my_set = {x for x in my_list} # This is similar to set(my_list) which yields set([1,2,3,4,5,7,8])
```


## Chapter 7: Exception Handling<a name="Chapter7"></a>

The most common Exceptions in python are:
    
    - Exception (this is what almost all the others are built off of)
    - AttributeError - Raised when an attribute reference or assignment fails.
    - IOError - Raised when an I/O operation (such as a print statement, the built-in open() function or a method of
     a file object) fails for an I/O-related reason, e.g., “file not found” or “disk full”.
    - ImportError - Raised when an import statement fails to find the module definition or when a from ... import fails
     to find a name that is to be imported.
    - IndexError - Raised when a sequence subscript is out of range.
    - KeyError - Raised when a mapping (dictionary) key is not found in the set of existing keys.
    - KeyboardInterrupt - Raised when the user hits the interrupt key (normally Control-C or Delete).
    - NameError - Raised when a local or global name is not found.
    - OSError - Raised when a function returns a system-related error.
    - SyntaxError - Raised when the parser encounters a syntax error.
    - TypeError - Raised when an operation or function is applied to an object of inappropriate type. The associated
     value is a string giving details about the type mismatch.
    - ValueError - Raised when a built-in operation or function receives an argument that has the right type but an 
    inappropriate value, and the situation is not described by a more precise exception such as IndexError.
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

Python has a built in function called _open_ to read from a file, the default mode is read only. Relative paths are 
to the script that is running. If we want to pass unescaped strings to the open method, we ned to prepend the string
 with an 'r'.

```python
# if not prepended with r, the string will print a tab in '(\t)est.txt', the second argument is to explicitly tell 
# python to open the file in read mode.
handle = open(r"C:\Users\mike\py101book\data\test.txt", "r")
# This reads all the file, returns a List of strings representing the lines
content = handle.read()
# This reads a single line
line = handle.readline()
# Always close the file after reading it
handle.close() 
``` 

The best way to read a file by lines is with a for loop:

```python
handle = open("MyFile.txt")
for line in handle:
    print(line)
handle.close()
```

Another way to read files is with a while loop, for example:

```python
handle = open("MyFile.pdf", "rb") #rb means read-binary
while True:
    data = handle.read(1024) #Reads 1024 bites of data
    if not data:
        break
```

A file can also be writen:

```python
try:
    handle = open("Test.txt", "w") #w for write mode and wb for write-binary
    handle.write("This is a test file")
except IOError:
    print("Something bad happened")
finally:
    handle.close() 
```

Python has a neat little builtin called _with_ which you can use to simplify reading and writing files. The _with_ 
operator creates what is known as a context manager in Python that will automatically close the file for you when 
you are done processing it:

```python
try:
    with open("test.txt") as file_handler:
        for line in file_handler:
            print(line)
except IOError:
    print("Something bad happened")
```


## Chapter 9: Importing<a name="Chapter9"></a>

A module is a single importable Python file whereas a package is made up of two or more modules. A package can be 
imported the same way a module is.

```python
import math
math.sqrt(4)
```

The syntax to use a module function is _module_name.method_name(argument)_. You can also import only some functions 
of a module:

```python
from math import sqrt, cos
from math import * # This is discouraged as it can lead to namespace collisions
```


## Chapter 10: Functions<a name="Chapter10"></a>

Example of function in python:

```python
def hello():
    print("Hello World")
```

It is possible to define an stub for a function, for example to derive the implementation to the future:

```python
def myFunc():
    pass # The pass statement is a null operation that doesn't do anything.
```

Functions can take parameters:

```python
def add(a,b):
    return a+b
```

All functions return something, if no return statement is provided, then the function will return None. When calling
 the function, you can pass positional arguments like in `add(2,3)`, or keyword arguments like in `add(b=1, a=2)`. 
 Default values can be specified in function creation like in:

```python
def add(a=1,b=2): #There is no need to define default values for all parameters add(a=1,b) is also valid
    return a+b
```
 
If the previous function is called without arguments, then a 3 will be returned. You can also set up functions to 
accept any number of arguments or keyword arguments:

```python
#The first is to define an infinite number of params and the second to define an infinite number of keyword params
def many(*args, **kwargs): 
    print(args)
    print(kwargs)

many(1, 2, 3, name="Mike", job="programmer") #Example of method call 
```

The scope of the variables defined in a function is local to the function.


## Chapter 11: Classes<a name="Chapter11"></a>

Everything in python is an object because everything is based on a class. An example of this is below:

```python
class Vehicle(object): 
    """docstring"""
def __init__(self):
    """Constructor"""
    pass
```

In the above example the object keyword after the class name is what the class is based on or inheriting from (the 
parent class). It the class does not inherit from other, you can leave out the parentheses and parent class: 
`class Veicle:...`. If we want the class to have attributes, we define them inside the `__init__` method:

```python
class Vehicle(object):
    """docstring"""

    def __init__(self, color, doors, tires, vType):
        """Constructor"""
        self.color = color
        self.doors = doors
        self.tires = tires
        self.vType = vType
    
    def drive(self):
       """
       Drive the car 
       """
       return "I'm driving!"
       
    def brake(self):
        """
        Stop the car 
        """
        return "%s braking" % self.vType
```

Python classes need a way to refer to themselves. The word self is a way to describe itself. Given the above, we can
 create subclasses that inherit the behaviour like in:

```python
class Car(Vehicle):

 def brake(self):
    """
    Stop the car 
    """
    return "Stopping the car"
```

In the above example, the car class inherits the `__init__` and `drive` methods from its parent.


## Chapter 12: Introspection<a name="Chapter12"></a>

Python can tell you what type of variable you have or what type is returned from a function:

```python
x="test"

type(x) # Returns <class 'str'>
```

The _dir_ keyword is used to tell the programmer what attributes and methods there are in the passed in object. You 
can also pass a module to the _dir_ function:

```python
dir("test") # Returns  ['__add__', '__class__', '__contains__', ...]
```

You can use the python _help_ utility to a shell (prepended by _>_ and not _>>>_) and get insights of the various 
modules, keywords and topics found in Python.


## Chapter 13: The csv Module<a name="Chapter13"></a>

There are two ways to read a CSV file. You can use the csv module’s reader function or you can use the DictReader class.

```python
import csv

# Function that accepts a file object
def csv_reader(file_obj): 
    """
    Read a csv file
    """
    reader = csv.reader(file_obj) # This returns a reader object 
    for row in reader:
        print(" ".join(row)) # Join the fields with an space

def csv_dict_reader(file_obj):
    """
    Read a CSV file using csv.DictReader
    """
    reader = csv.DictReader(file_obj, delimiter=',') # The delimiter parameter is not mandatory but desirable
    for line in reader: #  Each line in the reader object is a dictionary
        print(line["first_name"]),
        print(line["last_name"])

if __name__ == "__main__":
    csv_path = "someFile.csv" 
    with open(csv_path, "r") as f_obj:
        csv_reader(f_obj) # Example of how to call csv_reader function
        csv_dict_reader(f_obj) # Example of how to call csv_dict_reader function
```

As with the read functionality, the write functionality is available in both the _writer+ function or the _DictWriter_ 
class:

```python
import csv
# Data is a list of lists created at the bottom of this script 
def csv_writer(data, path): 
    """
    Write data to a CSV file path
    """
    # The csv_writer function opens the path that we pass in and creates a csv writer object. Then we loop over the 
    # nested list structure and write each line out to disk 
    with open(path, "w", newline='') as csv_file:
        writer = csv.writer(csv_file, delimiter=',') 
        for line in data:
            writer.writerow(line)
            
def csv_dict_writer(path, fieldnames, data): 
    """
    Writes a CSV file using DictWriter
    """
    with open(path, "w", newline='') as out_file:
        writer = csv.DictWriter(out_file, delimiter=',', fieldnames=fieldnames)
        writer.writeheader()
        for row in data:
            writer.writerow(row)

if __name__ == "__main__":
    # Example of how to write with the write object
    data = ["first_name,last_name,city".split(","),
            "Tyrese,Hirthe,Strackeport".split(","),
            "Jules,Dicki,Lake Nickolasville".split(","),
            "Dedric,Medhurst,Stiedemannberg".split(",")
            ]
    path = "output.csv"
    csv_writer(data, path)

    # Example of how to write with the dictWriter
    my_list = [] 
    fieldnames = data[0] 
    # This loop can be replaced by the writerows method in the DictWriter class
    for values in data[1:]:
        # Python builtins to create dictionary
        # The zip method takes two iterators and turn them into a list of tuples
        inner_dict = dict(zip(fieldnames, values))
        my_list.append(inner_dict)
    path = "dict_output.csv"
    csv_dict_writer(path, fieldnames, my_list)
```


## Chapter 14: configparser<a name="Chapter14"></a>

An example of how to create a config file:

```python
import configparser

def createConfig(path):
    """
    Create a config file
    """
    config = configparser.ConfigParser()
    config.add_section("Settings")
    config.set("Settings", "font", "Courier")
    config.set("Settings", "font_size", "10")
    config.set("Settings", "font_style", "Normal")
    config.set("Settings", "font_info", "You are using %(font)s at %(font_size)s pt")

    with open(path, "w") as config_file:
        config.write(config_file)
        
def crudConfig(path):
    """
    Create, read, update, delete config
    """
    if not os.path.exists(path):
        createConfig(path)
    
    config = configparser.ConfigParser()
    config.read(path)
    
    # read some values from the config
    font = config.get("Settings", "font")
    font_size = config.get("Settings", "font_size")
    
    # change a value in the config
    config.set("Settings", "font_size", "12")
    
    # delete a value from the config
    config.remove_option("Settings", "font_style")
    
    # write changes back to the config file
    with open(path, "w") as config_file:
        config.write(config_file)


if __name__ == "__main__":
    path = "settings.ini"
    createConfig(path)
    crudConfig(path)
```

The configparser module also allows interpolation, which means you can use some options to build another option:

```python
config = configparser.ConfigParser()
config.read(path)

print(config.get("Settings", "font_info")) # "You are using Courier at 12 pt" 
print(config.get("Settings", "font_info", vars={"font": "Arial", "font_size": "10"})) # "You are using Arial at 10 pt"
```


## Chapter 15: Logging<a name="Chapter15"></a>

Creating a log with the logging module is easy:

```python
import logging 

# If you don’t use basicConfig, then the logging module will output to the console / stdout.
logging.basicConfig(filename="sample.log", level=logging.INFO) # add filemode="w" to overwrite

logging.debug("This is a debug message") # Has modes 'debug', 'info', 'warning', 'error' and 'critical'

log = logging.getLogger("ex") # It is possible to get a logger object 
```

If you want all your modules to log in the same place, you can either configure it on the main method of the program 
and then call the logging method directly within the modules, or do it like this:

```python
logger = logging.getLogger("exampleApp")
logger.setLevel(logging.INFO)

# create the logging file handler
fh = logging.FileHandler("example.log")

formatter = logging.Formatter('%(asctime)s - %(name)s - %(levelname)s - %(message)s')
fh.setFormatter(formatter)

18 # add handler to logger object
logger.addHandler(fh)

logger.info("Program started")
result = otherMod2.add(7, 8)
logger.info("Done!")    
```

The previous example would print the name of the logger in each of the lines. You can configure it using methods 
(loggers, formatters, handlers), you can use a configuration file and pass it to `fileConfig()` or you can create a 
dictionary of configuration information and pass it to the `dictConfig()` function.


## Chapter 16: The os Module<a name="Chapter16"></a>

The os module has many modules, which deals with the operating system functions. To use the module import _os_. Example:

```python
os.name # This tells us that our Python instance is running on a Windows box
os.environ # Returns a dictionary of the user’s env variables. Access individual variables like os.environ["TMP"]
os.getenv("TMP") # Equivalent to os.environ["TMP"]
os.chdir(r"/tmp") # Function allows us to change the directory that we’re currently running our Python session in
os.getcwd() # Returns the current dir
os.mkdir("test") # Creates a folder test in the current directory. Absolute paths are accepted too
os.mkdirs("/tmp/test/folder") # Creates all intermediate folders in the provided path
os.remove("test.txt") # Deletes the file test.txt
os.rmdir("pytest") # Deletes the folder pytest
os.rename(src, dst) # Renames the folder/file src to dst
os.startfile(file) # Method allows us to “start” a file with its associated program. Like double click in a program
os.walk(path) # Used to get access to all its sub-directories and files

# Functionality contained in the os.path module
os.path.basename(path) # Returns the filename of a path
os.path.dirname(path) # Returns just the directory portion of the path
os.path.exists(path) # Returns a boolean indicating if the file or folder exists or not
os.path.isdir(path) # Returns a boolean indicating if the content of the variable path is a directory
os.path.isfile(path) # Returns a boolean indicating if the content of the variable path is a file
os.path.join(path1, path2) # Joins one or more path components together using the appropriate separator
os.path.split(path) # Split a path into a tuple that contains the directory and the file
```


## Chapter 17: The email/smtplib Module<a name="Chapter17"></a>

Python provides  the email and smtplib modules to deal with emails. Here is an example of how to send an email:

```python
import smtplib

# Most of this configuration can come from a config file
HOST = "mySMTP.server.com"
SUBJECT = "Test email from Python"
# To send this email to multiple accounts, just join the emails with a comma without spaces like email1,email2...
TO = "mike@someAddress.org"
FROM = "python@mydomain.com"
CC = "email1@email.com" # Optional parameter
BCC = "email2@email.com" # Optional parameter
text = "Python 3.4 rules them all!"

# These lines are combined using a carriage return "\r" plus a new line "\n"
BODY = "\r\n".join(("From: %s" % FROM, "To: %s" % TO,"CC: %s" % CC,"BCC: %s" % BCC, "Subject: %s" % SUBJECT , "", text))

server = smtplib.SMTP(HOST)
# If your server requires authentication, then you’ll need to add this code here: server.login(username, password)
server.sendmail(FROM, [TO], BODY)
server.quit()
```

It is also possible to add attachments to the emails, for that we use the python's email module:

```python
from email import encoders
from email.mime.text import MIMEText
from email.mime.base import MIMEBase
from email.mime.multipart import MIMEMultipart
from email.utils import formatdate

# We need to define the attachment, the variable file_to_attach is the path to the file
header = 'Content-Disposition', 'attachment; filename="%s"' % file_to_attach


# create the message
msg = MIMEMultipart()
msg["From"] = from_addr
msg["Subject"] = subject
msg["Date"] = formatdate(localtime=True)
if body_text:
    msg.attach( MIMEText(body_text) )

msg["To"] = ', '.join(to_emails)
msg["cc"] = ', '.join(cc_emails)

attachment = MIMEBase('application', "octet-stream")
try:
    with open(file_to_attach, "rb") as fh:
        data = fh.read()
        attachment.set_payload( data )
        encoders.encode_base64(attachment)
        attachment.add_header(*header)
        msg.attach(attachment)
except IOError:
    msg = "Error opening attachment file %s" % file_to_attach
    print(msg)
    
server.sendmail(from_addr, emails, msg.as_string())
```


## Chapter 18: The sqlite Module<a name="Chapter18"></a>
