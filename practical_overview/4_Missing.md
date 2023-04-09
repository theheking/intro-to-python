<a href="https://colab.research.google.com/github/theheking/intro-to-python/blob/gh-pages/4_Missing.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

## Dealing with missing data

Most real world data has lots of missing values and this can be an issue, in this notebook we'll go through how to deal with missing data.




```python
!pip install pandas matplotlib # install the packages directly into the notebook

```

Make sure the libraries are loaded and we have the data we need.



```python
# Download a file using python
import urllib.request # this is the library we need 

url = 'https://raw.githubusercontent.com/theheking/intro-to-python/gh-pages/docs/patient_data.csv'
#retrieve the file

urllib.request.urlretrieve(url, 'patient_data.csv')

#import pandas as a package
import pandas as pd 

#read in the patient data 
patient_df=pd.read_csv('patient_data.csv', sep=',')
```

### Finding Missing Values
Let's identify all locations in the survey data that have null (missing or NaN) data values. 


We can use the `isnull` method to do this. The `isnull` method will compare each cell with a null value. If an element has a null value, it will be assigned a value of `True` in the output object.


```python
# check what is null using isnull function 

```

## How to select rows with missing data

To select the rows where there are null values, we can use the mask as an index to subset our data as follows:




```python
#  select only the rows with NaN values, using the 'any(axis=1)' method
```

### Explaination
Notice that we have 444 observations/rows that contain one or more missing values. Thats roughly **37%** of data contains missing values.

We have used `[]` convension to select subset of data.

More information about slicing and indexing can be found out here.

`(axis=1)` is a numpy convention to specify columns.

Note that the weight column of our DataFrame contains many null or NaN values. Next, we will explore ways of dealing with this.

If we look at the weight column in the surveys data we notice that there are NaN (Not a Number) values. NaN values are undefined values that cannot be represented mathematically. Pandas, for example, will read an empty cell in a CSV or Excel sheet as a NaN. NaNs have some desirable properties: if we were to average the weight column without replacing our NaNs, Python would know to skip over those cells.






## Dealing with missing values.

Thoughts: 

1. What are some reasons why there might be missing data?
2. How would you deal with missing values?
3. Is it OK to ignore missing values when calculating the mean?
4. What effect do missing values have when you multiply 2 columns (either test this out or think about what would happen).


```python
## how many missing values are there in weight column
```


```python
# what are the number of rows have weight values len(patient_df[patient_df.weight> 0])

```

We can replace all NaN values with zeroes using the .fillna() method (after making a copy of the data so we don't lose our work): 


```python
# create a new DataFrame using copy

# fill all NaN values with fillna(0)

#print(patient_df['weight'].mean())

```

## Writing Out Data to CSV

Great, so you've filled out all your data but now you want to share it with your collaborators, to do that you can just write to a CSV as usual.


```python
# Write DataFrame to CSV use index=False
```

## Recap
What we've learned:

What NaN values are, how they might be represented, and what this means for your work
How to replace NaN values, if desired
How to use to_csv to write manipulated data to a file.

