<a href="https://colab.research.google.com/github/theheking/intro-to-python/blob/gh-pages/1_Python_The_Basics_Filled.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

# Fundamentals of Python

# Objectives
- Understand the background of Python
- Understand the different data types and structures
- Be able to use Python like a calculator

Guido Van Rossum first created Python in 1991 with these key aims:
1. Suitable for day-to-day activities. Fast development time.
2. As simple and easy to understand as English
3. Open source so that everyone can contribute to the program

# What are the advantages of using Python compared to other languages?

## Advantages
- Open-source
- Available for iOS, Windows and Linux
- Designed for readability
- Large supportive community
- Third-party packages! 

## Disadvantages
- Speed
- High memory consumption
- Low execution speed


```python
import sys
print(sys.version)

```

    3.10.11 (main, Apr  5 2023, 14:15:10) [GCC 9.4.0]


The designer of Python is Guido van Rossum!
He used to be the BDFL which he retired from in 2018! Now 32 years later and on release 3.10.11


```python
#what mode are we using now 
#show example if you were to use as a script
```

# Using interactive Python in Jupyter-style notebooks
There are two methods for using Python:
- Interactive mode: similar to a scientific calculator, but you insert code into blocks within jupyter notebooks .ipynb.
- Scripting mode: save that same code into a file with the ending .py.


```python
print("Python is cool!")
```

    Python is cool!



```python
print("Python is rad")
```

    Python is rad


#Some easy shortcuts to note

Shift-Enter to run the contents of the cell

You can add new cells by either:
1.   Hovering in between two boxes and selecting code. 
2.   Selecting Insert then Insert code cell


NOTE: When the text on the left hand of the cell is: In [*] (with an asterisk rather than a number) --> cell is still running.

Let's begin writing some more code in our notebook.




```python
#assign a string to variable
name = "Garvan"
#print variable
print(name)
```

    Garvan


A hashtag (#) denotes a comment. The python interpreter ignores anything after that comment.


```python
#print(name)
print(name) 
```

    Garvan


# Variables and data types

## Integers, floats and strings
With 'Numeric' types, there are two key types integer and floats.

Other slightly less important types include `hex` for hexadecimal and `complex` for complex numbers!




```python
 #assign number to variable
 kinghorn = 1
 print(kinghorn)
```

    1



```python
#what type is it 
type(kinghorn)
```




    int




```python
#assign a decimal to variable
katherine = 1.01

```


```python
#what type is this 
type(katherine)
```




    float



### Poll Time 

What is the <b>type</b> of the variable letters defined below ?

letters = "ABACBS"


## Strings
`str` stands for "string". These hold sequences of characters. Characters are not limited to letters but, also numbers, punctuation and emojiis!


```python
words_words="Python strings are UTF-8 <3 "
```


```python
#print the string
print(words_words)
```

    Python strings are UTF-8 <3 



```python
#what type is it
type(words_words)
```




    str



# Operators 

We can perform mathematical calculations in Python using the basic operators such as: 

##### + - * / % **



```python
#addition
2+2
```




    4




```python
#multiplication
6*145
```




    870




```python
#power
8**789
```




    34514353004048826885504379648003866504545218716100012512887166177026352534370841541962887882501289866325841638561707331766897031691050608333957460427033539970294439535876702952471732553659998595663644745155016713628313452425984909782081990174307591624993749579100130456318398090982815078162452007632470130691334908608531591427734030915851830575474874482280253468219207395528369339077139237178924637556985496275398612686731128467281887462316631160226001821395479523833586086502488859219359045000405140507016244667252934364031433606290733177233518426837335038979332193267723253000815065275439846928505916844052298665056194386833699440777271073682443908318576459257064547325048882423449738412777426102675653869436928




```python
#Modulo
13%6
```




    1




```python
# int + int = ?
a=5
print(a+4)
type(a+4)
```

    9





    int




```python
# int + float = ?
a=3
print(a+3.2)
type(a+3.2)
```

    6.2





    float




```python
# int + str = ?
name="barbie"
print(name+1)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-35-bfb80f99988d> in <cell line: 3>()
          1 # int + str = ?
          2 name="barbie"
    ----> 3 print(name+1)
    

    TypeError: can only concatenate str (not "int") to str



```python
#str(int) + str =?
str(4)+ "ken"
```




    '4ken'




```python
# demonstrate int += 1
number=4
number+=1
print(number)
```

    5


## Boolean operators
Boolean logic means your result can one of two values, True or False. 

We can also use comparison and logic operators: <b> <, >, ==, !=, <=, >=  </b> and statements of identity such as <b> and, or, and not. </b> These will evaluate the two values and output True and False.


```python
 # > 
 ken=4
 barbie=6
 ken != barbie
```




    True




```python
ken = True

```


```python
#or
```

# Lists and sequence types


## Lists
Lists are a compound data type made up of smaller parts. 



```python
 #form a list of numbers
 numbers = [4,5,67]
```


```python
#find the length
len(numbers)
```




    3




```python
#lists can contain multiple data types
list_of_cats = ["Persian", 5, 6]
#write a mixed list including a list with a list
list_of_cats = ["Persian", 5, [6,4.3,5]]
len(list_of_cats)
```




    3




```python
#these can be retrieved by their index 
list_of_cats[1]
```




    5




```python
#in python the first item in an index is always zero
list_of_cats[0]
```




    'Persian'




```python
#you can assign a new value to any position on the list
list_of_cats[0] = "Siamese"
```


```python
#print  the new list
print(list_of_cats)
```

    ['Siamese', 5, [6, 4.3, 5]]



```python
#you can append items to the end of the list
list_of_cats.append("Fluffy")
```


```python
print(list_of_cats)
```

    ['Siamese', 5, [6, 4.3, 5], 'Fluffy']



```python
#you can add multiple items to the end of a list with extend
list_of_cats.extend([1,2])

print(len(list_of_cats))
print(list_of_cats)
```

    6
    ['Siamese', 5, [6, 4.3, 5], 'Fluffy', 1, 2]



```python
#assign a list of dog breeds to variable 
list_of_dogs = ["shitz tzu","golden retriever","chihauha"]
#print the third entry in the list of dogs
print(list_of_dogs[2])

```

    chihauha



```python
#assign a list of animals to variable list_of_safari
list_of_safari=["elephant","hippo","lion"]

#print the first entry in the list
print(list_of_safari[0])

#change the second entry in the list and print it
list_of_safari[1]="scottish_terrier"
print(list_of_safari[1])

```

    elephant
    scottish_terrier



```python
#you can also access the values from a negative index 
#for example list_of_safari can be accessed [-3] --> [-1]

#print of the second to last entry in the list

print(list_of_safari[-2])
```

    scottish_terrier


## Loops 

A **for loop** can be used to access the elements in a list or other Python data structure one at a time. We will learn about loops in another lesson.

Indentation is very important in Python. Note that the second line in the example above is indented, indicating the code that is the body of the loop.





```python
list_of_numbers=[6,4,5]
for num in list_of_numbers:
  print(num)
```

    6
    4
    5



```python
  type(list_of_numbers)
```




    list




To find out what methods are available for an object, we can use the built-in help command:




```python
#help of list
help(list_of_numbers)
```

    Help on list object:
    
    class list(object)
     |  list(iterable=(), /)
     |  
     |  Built-in mutable sequence.
     |  
     |  If no argument is given, the constructor creates a new empty list.
     |  The argument must be an iterable if specified.
     |  
     |  Methods defined here:
     |  
     |  __add__(self, value, /)
     |      Return self+value.
     |  
     |  __contains__(self, key, /)
     |      Return key in self.
     |  
     |  __delitem__(self, key, /)
     |      Delete self[key].
     |  
     |  __eq__(self, value, /)
     |      Return self==value.
     |  
     |  __ge__(self, value, /)
     |      Return self>=value.
     |  
     |  __getattribute__(self, name, /)
     |      Return getattr(self, name).
     |  
     |  __getitem__(...)
     |      x.__getitem__(y) <==> x[y]
     |  
     |  __gt__(self, value, /)
     |      Return self>value.
     |  
     |  __iadd__(self, value, /)
     |      Implement self+=value.
     |  
     |  __imul__(self, value, /)
     |      Implement self*=value.
     |  
     |  __init__(self, /, *args, **kwargs)
     |      Initialize self.  See help(type(self)) for accurate signature.
     |  
     |  __iter__(self, /)
     |      Implement iter(self).
     |  
     |  __le__(self, value, /)
     |      Return self<=value.
     |  
     |  __len__(self, /)
     |      Return len(self).
     |  
     |  __lt__(self, value, /)
     |      Return self<value.
     |  
     |  __mul__(self, value, /)
     |      Return self*value.
     |  
     |  __ne__(self, value, /)
     |      Return self!=value.
     |  
     |  __repr__(self, /)
     |      Return repr(self).
     |  
     |  __reversed__(self, /)
     |      Return a reverse iterator over the list.
     |  
     |  __rmul__(self, value, /)
     |      Return value*self.
     |  
     |  __setitem__(self, key, value, /)
     |      Set self[key] to value.
     |  
     |  __sizeof__(self, /)
     |      Return the size of the list in memory, in bytes.
     |  
     |  append(self, object, /)
     |      Append object to the end of the list.
     |  
     |  clear(self, /)
     |      Remove all items from list.
     |  
     |  copy(self, /)
     |      Return a shallow copy of the list.
     |  
     |  count(self, value, /)
     |      Return number of occurrences of value.
     |  
     |  extend(self, iterable, /)
     |      Extend list by appending elements from the iterable.
     |  
     |  index(self, value, start=0, stop=9223372036854775807, /)
     |      Return first index of value.
     |      
     |      Raises ValueError if the value is not present.
     |  
     |  insert(self, index, object, /)
     |      Insert object before index.
     |  
     |  pop(self, index=-1, /)
     |      Remove and return item at index (default last).
     |      
     |      Raises IndexError if list is empty or index is out of range.
     |  
     |  remove(self, value, /)
     |      Remove first occurrence of value.
     |      
     |      Raises ValueError if the value is not present.
     |  
     |  reverse(self, /)
     |      Reverse *IN PLACE*.
     |  
     |  sort(self, /, *, key=None, reverse=False)
     |      Sort the list in ascending order and return None.
     |      
     |      The sort is in-place (i.e. the list itself is modified) and stable (i.e. the
     |      order of two equal elements is maintained).
     |      
     |      If a key function is given, apply it once to each list item and sort them,
     |      ascending or descending, according to their function values.
     |      
     |      The reverse flag can be set to sort in descending order.
     |  
     |  ----------------------------------------------------------------------
     |  Class methods defined here:
     |  
     |  __class_getitem__(...) from builtins.type
     |      See PEP 585
     |  
     |  ----------------------------------------------------------------------
     |  Static methods defined here:
     |  
     |  __new__(*args, **kwargs) from builtins.type
     |      Create and return a new object.  See help(type) for accurate signature.
     |  
     |  ----------------------------------------------------------------------
     |  Data and other attributes defined here:
     |  
     |  __hash__ = None
    


## Tuples

A tuple is similar to a list in that it's an ordered sequence of elements. However, tuples can not be changed once created (they are "immutable"). Tuples are made by placing comma-separated values inside parentheses ().




```python
# tuples_are_immutable = ("bar", 100, 200, "foo")
tuples_example = ("bar", 100, 400, "help")
```


```python
#print one element of tuple
print(tuples_example[3])
```

    help



```python
#reassign a different value to element of a tuple
tuples_example[3]="hello"
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-60-d05b5a7a7b59> in <cell line: 2>()
          1 #reassign a different value to element of a tuple
    ----> 2 tuples_example[3]="hello"
    

    TypeError: 'tuple' object does not support item assignment


## Dictionary

Dictionaries are used to store key-value pairs. They are unordered.

The `items` method returns a sequence of the key-value pairs as tuples. `values` returns a sequence of just the values. `keys` returns a sequence of just the keys.





```python
dogma = {'DNA': 1, 'RNA': 2, 'Protein': 3, 'key':5}
dogma
```




    {'DNA': 1, 'RNA': 2, 'Protein': 3, 'key': 5}




```python
#print a value of the dictionary using the key
dogma['DNA']
```




    1




```python
#reassign a value of dictionary
dogma['RNA'] =16
```


```python
#print the values only
print(dogma)
```

    {'DNA': 1, 'RNA': 16, 'Protein': 3, 'key': 5}



```python
dogma.items()
```




    dict_items([('DNA', 1), ('RNA', 16), ('Protein', 3), ('key', 5)])




```python
#print the keys only
dogma.keys()
```




    dict_keys(['DNA', 'RNA', 'Protein', 'key'])




```python
#print the values only
dogma.values()
```




    dict_values([1, 16, 3, 5])




```python
#get the length of the dictionary
len(dogma)
```




    4




```python
dict_of_dicts = {'first': {1:2, 2: 4, 4: 8, 8: 16}, 'second': {'a': 2.2, 'b': 4.4}}
dict_of_dicts #an example of a more compliated dictionary
```




    {'first': {1: 2, 2: 4, 4: 8, 8: 16}, 'second': {'a': 2.2, 'b': 4.4}}




# Poll Time

jam_ratings = {'Plum': 6, 'Apricot': 2, 'Strawberry': 8}


How would you change the value associated with the key Apricot to 9?

- jam_ratings = {'apricot': 9}
- jam_ratings[9] = 'Apricot'
- jam_ratings['Apricot'] = 9
- jam_ratings[2] = 'Apricot'


```python
jam_ratings = {'Plum': 6, 'Apricot': 2, 'Strawberry': 8}
```


```python
jam_ratings['Apricot']=9
```


```python
print(jam_ratings)
```

    {'Plum': 6, 'Apricot': 9, 'Strawberry': 8}

