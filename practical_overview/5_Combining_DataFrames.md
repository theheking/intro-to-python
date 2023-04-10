<a href="https://colab.research.google.com/github/theheking/intro-to-python/blob/gh-pages/5_Combining_DataFrames.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

# Learning How to Combine DataFrames
A common problem when dealing with is data is when you want combine two or more dataframes into one larger, more representative one.  Here we will learn how to both concatenate or merge two datasets using pandas.



```python
#make sure that libraries are currectly installed
!pip install pandas matplotlib
```


```python
import pandas as pd
import urllib.request
```


```python
url = 'https://ucsbcarpentry.github.io/truncated-python-ecology-lesson/data/yearly_files/surveys2001.csv'
urllib.request.urlretrieve(url, 'surveys2001.csv')
surveys_df = pd.read_csv("surveys2001.csv", keep_default_na=False, na_values=[""],index_col=0)
```


```python
# read in first 10 lines of surveys table
survey_sub = surveys_df.head(10)
# take the last 10 rows
survey_sub_last10 = surveys_df.tail(10)
# reset the index values- otherwise the the second dataframe will not append properly
# the flag, drop=True option avoids adding new index column with old index values
survey_sub_last10=survey_sub_last10.reset_index(drop=True)

```

There are two options for the axis flag.

- axis=0, detects same column names and stacks dataframes on top of one another
- axis=1, stacks the columns beside one another



```python
# stack the DataFrames on top of each other 
vertical_stack = pd.concat([survey_sub, survey_sub_last10], axis=0)

# place the DataFrames side by side using axis=1 naming it horizontal_stack

```


```python
#read in the second dataframe surverys 2002
url ='https://ucsbcarpentry.github.io/truncated-python-ecology-lesson/data/yearly_files/surveys2002.csv'
urllib.request.urlretrieve(url, 'surveys2002.csv')
surveys_df2 = pd.read_csv("surveys2002.csv", keep_default_na=False, na_values=[""], index_col=0)
```


```python
#print off the survey

```


```python
#assign the last ten of surveys_df2 to the survey_sub2_last10

```


```python
# Stack the DataFrames on top of each other
vertical_stack2 = pd.concat([surveys_df, surveys_df2], axis=0)

# Place the DataFrames side by side
```


```python
#find the mean year for each sex 
vertical_stack2.groupby('sex')['year'].mean()
```


```python
#save your vertical stack vertical_stack2

```

# Joining DataFrames

- We concatenated our DataFrames we simply added them to each other - stacking them either vertically or side by side

- We need to join the rows that are the same across both dataframes. 

- Combining DataFrames using a common field is called “joining”. 

- The columns containing the common values are called “join key(s)”. 

- Joining DataFrames in this way is often useful when one DataFrame is a “lookup table” containing additional data that we want to include in the other.

- For example, the species.csv file that we’ve been working with is a lookup table. It contains the genus, species and taxa code for 55 species, which is unique.

Storing data in this way has many benefits including:

- consistency
- easy for us to make changes to the species information once without having to find each instance of it in the larger survey data.
- optimizes the size of our data.



# Joining Two DataFrames

To better understand joins, let’s grab the first 10 lines of our data as a subset to work with


```python
# Read in first 10 lines of surveys table assign the survey_sub

```


```python
### Download speciesSubset.csv file from web
import urllib.request
url = 'https://bit.ly/2DfqN6C'
urllib.request.urlretrieve(url, 'speciesSubset.csv')

# import a small subset of the species data designed for this part of the lesson
# stored in the data folder.
species_sub = pd.read_csv('speciesSubset.csv', keep_default_na=False, na_values=[""])
species_sub
```


```python
#print what columns are the same across both dataframe

```

In this example, species_sub is the lookup table containing genus, species, and taxa names.

We want to join the data that contains all of the columns from both species_df and survey_df. The column that is the same in both dataframes is species_id. 


There are different type of joins! 


### A) Inner Join
- An inner join combines two DataFrames based on a join key and returns a new DataFrame that contains only those rows that have matching values in both of the original DataFrames.

- Inner joins yield a DataFrame that contains only rows where the value being joins exists in BOTH tables. 

An example of an inner join:
![img.png](https://drive.google.com/uc?id=1ZnVWxcmrXe4TySISayoLgShMS_UjCfbf)




```python
#choose the dataframe for the left, dataframe for the right name it merged inner

```


```python
# this case `species_id` is the only column name in  both dataframes, so if we skipped `left_on`
# `right_on` arguments we would still get the same result

```


> Note: that merged_inner has fewer rows than survey_sub. This is an indication that there were rows in surveys_df with value(s) for species_id that do not exist as value(s) for species_id in species_df.

# B) Left Joins

What if we want to add information from species_sub to survey_sub without losing any of the information from survey_sub? In this case, we use a different type of join called a “left outer join”, or a “left join”.

The result DataFrame from a left join looks similar to the result DataFrame from an inner join in terms of the columns it contains. However, unlike merged_inner, merged_left contains the same number of rows as the original survey_sub DataFrame.

> Note: a left join will still discard rows from the right DataFrame that do not have values for the join key(s) in the left DataFrame.



```python
#left join is performed in pandas by calling
#the same `merge` function used for inner join, but using the how='left' argument:


```


```python
#look at all the rows with null using merged_left[ pd.isnull(merged_left.genus) ]
```

These rows are the ones where the value of species_id from survey_sub (in this case, PF) does not occur in species_sub.

# Other join types

The `pandas` merge function supports two other join types:

- Right (outer) join: Invoked by passing how='right' as an argument. Similar to a left join, except all rows from the right DataFrame are kept, while rows from the left DataFrame without matching join key(s) values are discarded.
- Full (outer) join: Invoked by passing how='outer' as an argument. This join type returns the all pairwise combinations of rows from both DataFrames; i.e., the result DataFrame will NaN where data is missing in one of the dataframes. This join type is very rarely used.


# Extra Challenge

1. Create a new DataFrame by containing the individual organisms from `surveys2002.csv` that are the species found in `speciesSubset.csv`.

2. Calculate the mean hindfoot_length by sex. 




Adapted from Monash Data Science which was orginally adapted from the Data Carpentry - Python for Ecologists and Software Carpentry - Programming with Python (used under a CC-BY 4.0 license).
