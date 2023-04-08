# Fundamentals of Python

# Objectives
Assign value to variables

Guido Van Rossum first created Python in 1991 with key aims:

1. Good for day to day activities. Less development time.
2. As simple and easy to understand as english
3. Open source so that everyone can contirbute to the program

# What are the advantages of using Python compared to other languages?

## Advantages....
- Open-source
- Available for iOS, Windows and Linux
- Designed for readability
- Large supportive community
- Third party packages! 

## Disadvantages....
- Speed
- High memory consumption
- Low execution speed


```python
import sys
print(sys.version)

```

    3.7.13 (default, Apr 24 2022, 01:04:09) 
    [GCC 7.5.0]


The designer of Python is Guido van Rossum!
He used to be the BDFL which he retired from in 2018! Now 31 years later and on release 3.10.6

# Using interactive Python in Jupyter-style notebooks
There are two methods to use python
- interactive mode: similar to a scientific calculator, but you insert code into blocks within jupyter notebooks `.ipynb`. 
- scripting mode: save that same code into a file with the ending `.py`. 


```python
#print something in interactively in shell
```

#Some easy shortcuts to note

Shift-Enter to run the contents of the cell

You can add new cells by either 
a) hovering in between two boxes and selecting code. 
b) Insert then insert code cell

NOTE: When the text on the left hand of the cell is: In [*] (with an asterisk rather than a number) --> cell is still running.

Let's begin writing some code in our notebook.




```python
#assign a string to variable

#print variable
```

    Garvan


A hash tag (#) denotes a comment anything after that comment is ignored by the the python intepreter


```python
#show a comment
```

    Garvan


# Variables and data types

## Integers, floats and strings
Of the 'Numeric' types. There are two key types integer and floats.

Other (slightly less important types include `hex` for hexadecamil and `complex` for complex numbers!




```python
 #assign number to variable

 #print variable

```

    1



```python
#check type of variable

```




    int




```python
#assign a decimal to variable


```


```python
#check type of variable

```




    float



5 min into groups 
### Poll Time 
#### Your vote counts!!!! 🗳️ 

What is the <b>type</b> of the variable letters defined below ?

letters = "ABACBS"


## Strings
`str` stands for "string". These hold sequences of characters. Characters are not limited to letts but, also numbers, punctuation and emojiis!


```python
#create a variable of characters
```


```python
#print the string
```

    Python strings are UTF-8 <3 



```python
#what type is it
```




    str



# Operators 

We can perform mathematical calculations in Python using the basic operators such as: 

##### + - * / % **



```python
#addition
```




    4




```python
#multiplication 
```




    870




```python
#power
```




    34514353004048826885504379648003866504545218716100012512887166177026352534370841541962887882501289866325841638561707331766897031691050608333957460427033539970294439535876702952471732553659998595663644745155016713628313452425984909782081990174307591624993749579100130456318398090982815078162452007632470130691334908608531591427734030915851830575474874482280253468219207395528369339077139237178924637556985496275398612686731128467281887462316631160226001821395479523833586086502488859219359045000405140507016244667252934364031433606290733177233518426837335038979332193267723253000815065275439846928505916844052298665056194386833699440777271073682443908318576459257064547325048882423449738412777426102675653869436928




```python
#modulo (finds the remainder) using %
```




    1




```python
# int + int = ? & what type 

```

    9





    int




```python
# int + float = ? & what type 
```

    6.2





    float




```python
# int + str = ? & what type 
```

    barbie1



```python
#str(int) + str =?
```




    '4ken'




```python
# demonstrate int += 1
```

    5


## Boolean operators
Boolean logic means your result can one of two values, True or False. 

We can also use comparison and logic operators: <b> <, >, ==, !=, <=, >=  </b> and statements of identity such as <b> and, or, and not. </b> These will evaluate the two values and output True and False.


```python
 # show that the string t-cell does not equal b-cell
```




    True




```python
# show that 
```

# Lists and sequence types


## Lists
Lists are a compound data type made up of smaller parts. 



```python
 #form a list of numbers
```


```python
#find the length of that list 
```




    3




```python
#lists can contain multiple data types e.g. cats

#write a mixed list including a list with a list
```




    3




```python
#subset the a value from the list
```




    5




```python
#subset the first value from the list
```




    'Persian'




```python
#assign a new value to any position on the list
```


```python
#print  the new list
```

    ['Siamese', 5, [6, 4.3, 5]]



```python
#append an item to the end of the list

#print off the new list
```


```python
# add multiple items to the end of a list with extend and another list

#check the new length
```


```python
#assign a list of dog breeds to variable 

#print the third entry in the list of dogs

```

    chihauha
    scottish_terrier



```python
#assign a list of animals to variable list_of_safari

#print the first entry in the list

#change the second entry in the list and print it

```

    elephant
    scottish_terrier



```python
#you can also access the values from a negative index 
#for example list_of_safari can be accessed [-3] --> [-1]

#print of the second to last entry in the list

```

    scottish_terrier


## Loops 

A for loop can be used to access the elements in a list or other Python data structure one at a time. We will learn about loops in another lesson.

Indentation is very important in Python. Note that the second line in the example above is indented, indicating the code that is the body of the loop.





```python
list_of_numbers=[6,4,5]
for num in list_of_numbers:
  print(num)
```

    6
    4
    5



To find out what methods are available for an object, we can use the built-in help command:




```python
#help of list
help(list_of_numbers)
```

## Tuples

A tuple is similar to a list in that it's an ordered sequence of elements. However, tuples can not be changed once created (they are "immutable"). Tuples are created by placing comma-separated values inside parentheses ().




```python
# create a new tuple e.g. tuples_are_immutable = ("bar", 100, 200, "foo")

```


```python
#print one element of tuple
```

    help



```python
#reassign a different value to element of a tuple
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-92-d05b5a7a7b59> in <module>
          1 #reassign a different value to element of a tuple
    ----> 2 tuples_example[3]="hello"
    

    TypeError: 'tuple' object does not support item assignment


## Dictionary

Dictionaries are a container that store key-value pairs. They are unordered.

The `items` method returns a sequence of the key-value pairs as tuples. `values` returns a sequence of just the values. `keys` reutrns a sequence of just the keys.





```python
#form a new dictionary e.g. dogma = {'DNA': 1, 'RNA': 2, 'Protein': 3, 'key':5}

```




    {'DNA': 1, 'RNA': 2, 'Protein': 3, 'key': 5}




```python
#print the value of the dictionary using the key DNA
```




    1




```python
#reassign the value of RNA in the dictionary
```


```python
#print the values only
```

    dict_values([1, 2, 3, 5])



```python
#print the items in the list
```




    dict_items([('DNA', 1), ('RNA', 2), ('Protein', 3), ('key', 5)])




```python
#print the keys only
```




    dict_keys(['DNA', 'RNA', 'Protein', 'key'])




```python
#get the length of the dictionary
```




    4




```python
# create a layered dictionary e.g. dict_of_dicts = {'first': {1:2, 2: 4, 4: 8, 8: 16}, 'second': {'a': 2.2, 'b': 4.4}}
```




    {'first': {1: 2, 2: 4, 4: 8, 8: 16}, 'second': {'a': 2.2, 'b': 4.4}}



5 min into groups

Poll Time
Your vote counts!!!! 🗳️
 
jam_ratings = {'Plum': 6, 'Apricot': 2, 'Strawberry': 8}


How would you change the value associated with the key Apricot to 9.

- jam_ratings = {'apricot': 9}
- jam_ratings[9] = 'Apricot'
- jam_ratings['Apricot'] = 9
- jam_ratings[2] = 'Apricot'
