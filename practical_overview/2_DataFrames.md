<a href="https://colab.research.google.com/github/theheking/intro-to-python/blob/gh-pages/2_DataFrames.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

## Introducing... the DataFrame 

Objectives:
- Familiarise ourself with pandas
- Download data from a csv file into a dataframe
- Calculate statistics from the dataframe




```python
# Download a file using python woo!
import urllib.request # this is the library we need 

url = 'https://raw.githubusercontent.com/theheking/intro-to-python/gh-pages/docs/patient_data.csv'
# This is getting the file

urllib.request.urlretrieve(url, 'patient_data.csv')
```


```python
urllib.request.urlretrieve(url, 'patient_data.csv')
```

Next let's install the required packages for this workshop, by using ! we download and install directly into the notebook.


```python
! pip install pandas matplotlib seaborn

```

Pandas is a package. Packages are where functions are stored. You have to load a package in order to use the functions found within it. 


```python
#import pandas as a package

#read in the patient data but do not assign it to a variable
```


```python
#read in the patient data but do not assign it to a variable (patient_df)


```


```python
# check the type of the DF and its content using type and dtypes 

```

## Accessing the data from the data frame

Now we have the data, we need to use pandas as a way of processing it. Checking out the documentation is always super helpful (https://pandas.pydata.org/docs/)! 

Thankfully with programming you will not have a closed book test ever so really capitalise on the resources you have online. 





```python
? pd.DataFrame.head
```


```python
#Subset the first 20 rows of the dataframe 

```


```python
#Subset the last 10 rows of the dataframe

```


```python
#finding the columns in the dataframe
```

## Calculating Statistics From Data

So now the fun begins! You have to handle columns depending on what is in the column.


```python
# find unique data within categorical column-  illness using pd.unique

```


```python
#find the counts of all those unique values using value_counts()

```


```python
#find data summaries of site id column using describe 

```


```python
#  extract specific values from weight column using min, max, mean, std, count

```

## Creating stats

Next we might want to create statistics on a subset of the data, for example, what is the weight if we subset first by sex?


```python
# group data by sex and assign to new variable grouped_data

# Summary statistics for all numeric columns by sex
print(grouped_data.describe())

```


```python
# provide the mean for each numeric column by sex

```

## Challenge - Summary Data

How many patients are female F and how many male M:  
```
A) 519 and 507
B) 507 and 519 
C) 509 and 507
D) 400 and 412
```

What happens when you group by two columns using the following syntax and then grab mean values:
```
grouped_data2 = patient_df.groupby(['site_id','sex'])
grouped_data2.mean()
```
Summarize weight values for each site in your data. HINT: you can use the following syntax to only create summary statistics for one column in your `data by_site['weight'].describe()`




```python
grouped_data.describe()

grouped_data2 = patient_df.groupby(['site_id','sex'])
grouped_data2.mean()
grouped_data2['weight'].describe()
```

## Summary Counts in Pandas
First we number of patients for each . We can do this in a few ways, but we'll use groupby combined with a `count()` method.



```python
# Count the number of patients per illness using groupby and count

```

## Basic Math Functions

The nice thing about dataframes is that you can do math on them really easily which is awesome! 

So we can calculate the difference between columns, multiply them etc.


```python
# Multiply all weight values by 2 but do not change the original weight data
```


```python
#create a new column by multiplying together the weight and the site id

#print it off 
```
