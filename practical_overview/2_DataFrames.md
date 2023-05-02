<a href="https://colab.research.google.com/github/theheking/intro-to-python/blob/gh-pages/2_DataFrames.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

## Introducing... the DataFrame 

Objectives:
- Familiarise ourselves with pandas
- Download data using a CSV file into a data frame
- Calculate statistics from the data frame




```python
# Download a file using python
import urllib.request # this is the library we need 

url = 'https://raw.githubusercontent.com/theheking/intro-to-python/gh-pages/docs/patient_data.csv'

#retrieve the file
urllib.request.urlretrieve(url, 'patient_data.csv')
```

Next let's install the required packages for this workshop, by using ! we download and install directly into the notebook.


```python
# ! pip install pandas matplotlib seaborn

```

Pandas is a package. Packages are where functions are stored. You have to load a package in order to use the functions found within it. 


```python
#import pandas as a package

#read in the patient data 

```


```python
#we have read it in we haven't saved it to an object 

# assigning it to a variable patient_df

# this prints out the first rows using head function


```


```python
# we can also check what type the DF is... 
# Can you guess?! print(type(patient_df)) 
# What data types does it contain print(patient_df.dtypes)
```

## Accessing the data from the data frame

Now we have the data, we need to use pandas to process it. Checking out the documentation is always super helpful (https://pandas.pydata.org/docs/)! 

Thankfully, with programming, you will never have a closed book test, so capitalise on the resources you have online. 



#### What we are doing next: 
1. Subset the first 20 rows of the data frame 
2. Subset the last 10 rows of the data frame
3. Finding the columns in the data frame


```python
#check the head function ? pd.DataFrame.head

```


```python
#print the top 20 rows

```


```python
#print the final 20 rows
```


```python
#print the columns 

```

## Calculating Statistics From Data

So now the fun begins! First, you have to handle columns depending on what is in the column.

1. Find the unique data within categorical columns
2. Find data summaries of numerical columns


```python
#find the unique values in the illness 
```


```python
#use value counts to find the number of times a unique value occurs
```


```python
# next we might want to "describe" the site id column 

```


```python
# extract specific values min, max, mean, std, and count for weight
```

## Creating stats

Next we might want to create statistics on a subset of the data, for example, what is the weight if we subset first by gender?


```python
# Group data by gender

# Summary statistics for all numeric columns by gender using describe()

```


```python
# Provide the mean for each numeric column by gender
# As above, only the last command shows output below - you can try the others above in new cells

```

## Poll

How many patients are female F and how many male M:  
```
A) 519 and 507
B) 507 and 519 
C) 509 and 507
D) 400 and 412
```

What happens when you group by two columns using the following syntax and then grab mean values:
```
grouped_data2 = patient_df.groupby(['site_id','gender'])
grouped_data2.mean()
```
Summarize weight values for each site in your data. HINT: you can use the following syntax to only create summary statistics for one column in your `data by_site['weight'].describe()`



## Summary Counts in Pandas
First, we number of patients for each. We can do this in a few ways, but we'll use `groupby` combined with a `count()` method. This is similar to value_counts.




```python
# Count the number of patients by illness patient_counts = patient_df.groupby('illness')['patient_id'].count()

```

## Basic Math Functions

The nice thing about data frames is that you can do the math on them quickly, which is fantastic! 

So we can calculate the difference between columns, multiply them etc.


```python
# Multiply all weight values by 2 but does not change the original weight data
```


```python
#Assign this value to a new column 

```
Adapted from Monash Data Science which was orginally adapted from the Data Carpentry - Python for Ecologists and Software Carpentry - Programming with Python (used under a CC-BY 4.0 license).

