<a href="https://colab.research.google.com/github/theheking/intro-to-python/blob/gh-pages/1_Python_The_Basics.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

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
# import sys as a package 
# print the version  by using sys.version
```

The designer of Python is Guido van Rossum!
He used to be the BDFL which he retired from in 2018! Now 32 years later and on release 3.10.11

# Using interactive Python in Jupyter-style notebooks
There are two methods for using Python:
- Interactive mode: similar to a scientific calculator, but you insert code into blocks within jupyter notebooks .ipynb.
- Scripting mode: save that same code into a file with the ending .py.


```python
# use print to print a string
```


```python
# what mode are we using now 
```

#Some easy shortcuts to note

Shift-Enter to run the contents of the cell

You can add new cells by either:
1.   Hovering in between two boxes and selecting code. 
2.   Selecting Insert then Insert code cell


NOTE: When the text on the left hand of the cell is: In [*] (with an asterisk rather than a number) --> cell is still running.

Let's begin writing some more code in our notebook.




```python
#assign a string to variable

#print variable

```

A hashtag (#) denotes a comment. The python interpreter ignores anything after that comment.


```python
#print(name)

```

# Variables and data types

## Integers, floats and strings
With 'Numeric' types, there are two key types integer and floats.

Other slightly less important types include `hex` for hexadecimal and `complex` for complex numbers!




```python
 #assign number to variable

```


```python
#what type is it 

```


```python
#assign a decimal to variable

```


```python
#what type is this 

```

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

```


```python
#what type is it

```

# Operators 

We can perform mathematical calculations in Python using the basic operators such as: 

##### + - * / % **



```python
#addition 
```


```python
#multiplication using *
```


```python
#power using **
```


```python
#modulo using %
```


```python
# int + int = ?
```


```python
# int + float = ?
```


```python
# int + str = ?
#str(int) + str =?
```


```python
# assign a value 
# demonstrate int += 1
```

## Boolean operators
Boolean logic means your result can one of two values, True or False. 

We can also use comparison and logic operators: <b> <, >, ==, !=, <=, >=  </b> and statements of identity such as <b> and, or, and not. </b> These will evaluate the two values and output True and False.


```python
 #test out which variables of integers is larger than another 

```

# Lists and sequence types


## Lists
Lists are a compound data type made up of smaller parts. 



```python
 #form a list of numbers
```


```python
#find the length
```


```python
#lists can contain multiple data types

#write a mixed list including a list with a list
```


```python
#these can be retrieved by their index 
```


```python
#in python the first item in an index is always zero
```


```python
#you can assign a new value to any position on the list 
```


```python
#print  the new list
```


```python
#you can append items to the end of the list

```


```python
#you can add multiple items to the end of a list with extend list.extend(anotherlist)

```

# DIY 
1. Assign a list of your choosing (e.g. safari animals) to a variable
2. Print the third entry in the list
3. Change the second entry in the list to "puggle".
Extension: 
- You can access the values from a negative index. It can be accessed from [-3] to [-1]
Print off the second to last entry in your list. 

## Loops 

A **for loop** can be used to access the elements in a list or other Python data structure one at a time. We will learn about loops in another lesson.

Indentation is very important in Python. Note that the second line in the example above is indented, indicating the code that is the body of the loop.





```python
list_of_numbers=[6,4,5]
for num in list_of_numbers:
  print(num)
```


```python
  type(list_of_numbers)
```


To find out what methods are available for an object, we can use the built-in help command:




```python
#help of list
help(list_of_numbers)
```

## Tuples

A tuple is similar to a list in that it's an ordered sequence of elements. However, tuples can not be changed once created (they are "immutable"). Tuples are made by placing comma-separated values inside parentheses ().




```python
# example tuple tuples_are_immutable = ("bar", 100, 200, "foo")
```


```python
#print one element of tuple
```


```python
#reassign a different value to element of a tuple
```

## Dictionary

Dictionaries are used to store key-value pairs. They are unordered.

The `items` method returns a sequence of the key-value pairs as tuples. `values` returns a sequence of just the values. `keys` returns a sequence of just the keys.





```python
dogma = {'DNA': 1, 'RNA': 2, 'Protein': 3, 'key':5}
dogma
```


```python
#print a value of the dictionary using the key 
```


```python
#reassign a value of dictionary
```


```python
#print the items 
```


```python
#print the keys only
```


```python
#print the values only
```


```python
#get the length of the dictionary
```


```python
#if you want to have more fun
dict_of_dicts = {'first': {1:2, 2: 4, 4: 8, 8: 16}, 'second': {'a': 2.2, 'b': 4.4}}
dict_of_dicts #an example of a more compliated dictionary
```


# Poll Time

jam_ratings = {'Plum': 6, 'Apricot': 2, 'Strawberry': 8}


How would you change the value associated with the key Apricot to 9?

- jam_ratings = {'apricot': 9}
- jam_ratings[9] = 'Apricot'
- jam_ratings['Apricot'] = 9
- jam_ratings[2] = 'Apricot'

 
 
 
 
 Adapted from Monash Data Science which was orginally adapted from the Data Carpentry - Python for Ecologists and Software Carpentry - Programming with Python (used under a CC-BY 4.0 license).

