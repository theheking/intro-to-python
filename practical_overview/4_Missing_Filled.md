<a href="https://colab.research.google.com/github/theheking/intro-to-python/blob/gh-pages/4_Missing_Filled.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

## Dealing with missing data

Most real world data has lots of missing values and this can be an issue, in this notebook we'll go through how to deal with missing data.




```python
!pip install pandas matplotlib # install the packages directly into the notebook

```

    Looking in indexes: https://pypi.org/simple, https://us-python.pkg.dev/colab-wheels/public/simple/
    Requirement already satisfied: pandas in /usr/local/lib/python3.7/dist-packages (1.3.5)
    Requirement already satisfied: matplotlib in /usr/local/lib/python3.7/dist-packages (3.2.2)
    Requirement already satisfied: python-dateutil>=2.7.3 in /usr/local/lib/python3.7/dist-packages (from pandas) (2.8.2)
    Requirement already satisfied: numpy>=1.17.3 in /usr/local/lib/python3.7/dist-packages (from pandas) (1.21.6)
    Requirement already satisfied: pytz>=2017.3 in /usr/local/lib/python3.7/dist-packages (from pandas) (2022.2.1)
    Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.7/dist-packages (from python-dateutil>=2.7.3->pandas) (1.15.0)
    Requirement already satisfied: cycler>=0.10 in /usr/local/lib/python3.7/dist-packages (from matplotlib) (0.11.0)
    Requirement already satisfied: pyparsing!=2.0.4,!=2.1.2,!=2.1.6,>=2.0.1 in /usr/local/lib/python3.7/dist-packages (from matplotlib) (3.0.9)
    Requirement already satisfied: kiwisolver>=1.0.1 in /usr/local/lib/python3.7/dist-packages (from matplotlib) (1.4.4)
    Requirement already satisfied: typing-extensions in /usr/local/lib/python3.7/dist-packages (from kiwisolver>=1.0.1->matplotlib) (4.1.1)


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
pd.isnull(patient_df).head()

```





  <div id="df-231c6e6f-743c-4428-8e8d-2013525a1ebd">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>patient_id</th>
      <th>site_id</th>
      <th>sex</th>
      <th>time</th>
      <th>year</th>
      <th>month</th>
      <th>day</th>
      <th>illness</th>
      <th>weight</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-231c6e6f-743c-4428-8e8d-2013525a1ebd')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-231c6e6f-743c-4428-8e8d-2013525a1ebd button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-231c6e6f-743c-4428-8e8d-2013525a1ebd');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




## How to select rows with missing data

To select the rows where there are null values, we can use the mask as an index to subset our data as follows:




```python
# To select only the rows with NaN values, we can use the 'any()' method
patient_df[pd.isnull(patient_df).any(axis=1)]
```





  <div id="df-37b060a3-94bd-4b19-8967-bc51d2d483eb">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>patient_id</th>
      <th>site_id</th>
      <th>sex</th>
      <th>time</th>
      <th>year</th>
      <th>month</th>
      <th>day</th>
      <th>illness</th>
      <th>weight</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>3</td>
      <td>M</td>
      <td>7:26 pm</td>
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>NaN</td>
      <td>36.0</td>
    </tr>
    <tr>
      <th>13</th>
      <td>14</td>
      <td>8</td>
      <td>NaN</td>
      <td>11:35 pm</td>
      <td>2022.0</td>
      <td>3.0</td>
      <td>12.0</td>
      <td>fall</td>
      <td>21.0</td>
    </tr>
    <tr>
      <th>18</th>
      <td>19</td>
      <td>4</td>
      <td>NaN</td>
      <td>3:18 pm</td>
      <td>2022.0</td>
      <td>5.0</td>
      <td>12.0</td>
      <td>mva</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>19</th>
      <td>20</td>
      <td>11</td>
      <td>F</td>
      <td>5:34 pm</td>
      <td>2022.0</td>
      <td>5.0</td>
      <td>12.0</td>
      <td>NaN</td>
      <td>26.0</td>
    </tr>
    <tr>
      <th>22</th>
      <td>23</td>
      <td>13</td>
      <td>M</td>
      <td>11:13 am</td>
      <td>2022.0</td>
      <td>6.0</td>
      <td>12.0</td>
      <td>faint</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1176</th>
      <td>1177</td>
      <td>14</td>
      <td>M</td>
      <td>7:49 pm</td>
      <td>2022.0</td>
      <td>12.0</td>
      <td>2.0</td>
      <td>MVA</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1177</th>
      <td>1178</td>
      <td>16</td>
      <td>M</td>
      <td>10:30 am</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>16.0</td>
      <td>diabetic ketoacidosois</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1179</th>
      <td>1180</td>
      <td>4</td>
      <td>F</td>
      <td>2:30 pm</td>
      <td>2022.0</td>
      <td>10.0</td>
      <td>29.0</td>
      <td>NaN</td>
      <td>39.0</td>
    </tr>
    <tr>
      <th>1184</th>
      <td>1185</td>
      <td>1</td>
      <td>F</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>1187</th>
      <td>1188</td>
      <td>1</td>
      <td>M</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>nstemi</td>
      <td>35.0</td>
    </tr>
  </tbody>
</table>
<p>444 rows × 9 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-37b060a3-94bd-4b19-8967-bc51d2d483eb')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-37b060a3-94bd-4b19-8967-bc51d2d483eb button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-37b060a3-94bd-4b19-8967-bc51d2d483eb');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




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
## Where Are the NaN's?

## how many missing values are there in weight column
len(patient_df[pd.isnull(patient_df.weight)])
```




    217




```python
# number of rows have weight values
len(patient_df[patient_df.weight> 0])
```




    974



We can replace all NaN values with zeroes using the .fillna() method (after making a copy of the data so we don't lose our work): 


```python
# create a new DataFrame using copy
df1 = patient_df.copy()

# fill all NaN values with 0
df1['weight'] = df1['weight'].fillna(0)

print(patient_df['weight'].mean())
print(df1['weight'].mean())
```

    33.063655030800824
    27.039462636439968



```python
# Fill all NaN values with mean
df1 = patient_df.copy()
df1['weight'] = df1['weight'].fillna(patient_df['weight'].mean())

#check the mean 
print(patient_df['weight'].mean())
print(df1['weight'].mean())
```

    33.063655030800824
    33.063655030800824


## Writing Out Data to CSV

Great, so you've filled out all your data but now you want to share it with your collaborators, to do that you can just write to a CSV as usual.


```python
# Write DataFrame to CSV
df1.to_csv('surveys_complete.csv', index=False)
```

## Recap
What we've learned:

What NaN values are, how they might be represented, and what this means for your work
How to replace NaN values, if desired
How to use to_csv to write manipulated data to a file.

