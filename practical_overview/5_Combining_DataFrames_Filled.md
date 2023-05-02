<a href="https://colab.research.google.com/github/theheking/intro-to-python/blob/gh-pages/5_Combining_DataFrames_Filled.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

# Learning How to Combine DataFrames

A common problem when dealing with is data is when you want to combine two or more data frames into one larger, more representative one.  Here we will learn how to concatenate or merge two datasets using pandas.

Objectives 
- Be able to merge two dataframes using pandas using different methods 
- Be able to concatenate two dataframes together 


We will be using two model datasets from the UCSB python ecology workshop.


```python
#make sure that libraries are currectly installed
!pip install pandas matplotlib
```

    Looking in indexes: https://pypi.org/simple, https://us-python.pkg.dev/colab-wheels/public/simple/
    Requirement already satisfied: pandas in /usr/local/lib/python3.9/dist-packages (1.4.4)
    Requirement already satisfied: matplotlib in /usr/local/lib/python3.9/dist-packages (3.7.1)
    Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.9/dist-packages (from pandas) (2022.7.1)
    Requirement already satisfied: python-dateutil>=2.8.1 in /usr/local/lib/python3.9/dist-packages (from pandas) (2.8.2)
    Requirement already satisfied: numpy>=1.18.5 in /usr/local/lib/python3.9/dist-packages (from pandas) (1.22.4)
    Requirement already satisfied: cycler>=0.10 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (0.11.0)
    Requirement already satisfied: pyparsing>=2.3.1 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (3.0.9)
    Requirement already satisfied: pillow>=6.2.0 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (8.4.0)
    Requirement already satisfied: importlib-resources>=3.2.0 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (5.12.0)
    Requirement already satisfied: kiwisolver>=1.0.1 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (1.4.4)
    Requirement already satisfied: fonttools>=4.22.0 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (4.39.3)
    Requirement already satisfied: contourpy>=1.0.1 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (1.0.7)
    Requirement already satisfied: packaging>=20.0 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (23.0)
    Requirement already satisfied: zipp>=3.1.0 in /usr/local/lib/python3.9/dist-packages (from importlib-resources>=3.2.0->matplotlib) (3.15.0)
    Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.9/dist-packages (from python-dateutil>=2.8.1->pandas) (1.16.0)



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

# place the DataFrames side by side
horizontal_stack = pd.concat([survey_sub, survey_sub_last10], axis=1)

```


```python
#read in the second dataframe surveys 2002
url ='https://ucsbcarpentry.github.io/truncated-python-ecology-lesson/data/yearly_files/surveys2002.csv'
urllib.request.urlretrieve(url, 'surveys2002.csv')
surveys_df2 = pd.read_csv("surveys2002.csv", keep_default_na=False, na_values=[""], index_col=0)
```


```python
#print off the survey
surveys_df2
```





  <div id="df-65a153c5-f965-4ff3-a706-28bf01d12579">
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
      <th>record_id</th>
      <th>month</th>
      <th>day</th>
      <th>year</th>
      <th>site_id</th>
      <th>species_id</th>
      <th>sex</th>
      <th>hindfoot_length</th>
      <th>weight</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>33320</th>
      <td>33321</td>
      <td>1</td>
      <td>12</td>
      <td>2002</td>
      <td>1</td>
      <td>DM</td>
      <td>M</td>
      <td>38.0</td>
      <td>44.0</td>
    </tr>
    <tr>
      <th>33321</th>
      <td>33322</td>
      <td>1</td>
      <td>12</td>
      <td>2002</td>
      <td>1</td>
      <td>DO</td>
      <td>M</td>
      <td>37.0</td>
      <td>58.0</td>
    </tr>
    <tr>
      <th>33322</th>
      <td>33323</td>
      <td>1</td>
      <td>12</td>
      <td>2002</td>
      <td>1</td>
      <td>PB</td>
      <td>M</td>
      <td>28.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>33324</th>
      <td>33325</td>
      <td>1</td>
      <td>12</td>
      <td>2002</td>
      <td>1</td>
      <td>DO</td>
      <td>M</td>
      <td>35.0</td>
      <td>29.0</td>
    </tr>
    <tr>
      <th>33325</th>
      <td>33326</td>
      <td>1</td>
      <td>12</td>
      <td>2002</td>
      <td>2</td>
      <td>OT</td>
      <td>F</td>
      <td>20.0</td>
      <td>26.0</td>
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
      <th>35540</th>
      <td>35541</td>
      <td>12</td>
      <td>31</td>
      <td>2002</td>
      <td>15</td>
      <td>PB</td>
      <td>F</td>
      <td>24.0</td>
      <td>31.0</td>
    </tr>
    <tr>
      <th>35541</th>
      <td>35542</td>
      <td>12</td>
      <td>31</td>
      <td>2002</td>
      <td>15</td>
      <td>PB</td>
      <td>F</td>
      <td>26.0</td>
      <td>29.0</td>
    </tr>
    <tr>
      <th>35542</th>
      <td>35543</td>
      <td>12</td>
      <td>31</td>
      <td>2002</td>
      <td>15</td>
      <td>PB</td>
      <td>F</td>
      <td>27.0</td>
      <td>34.0</td>
    </tr>
    <tr>
      <th>35546</th>
      <td>35547</td>
      <td>12</td>
      <td>31</td>
      <td>2002</td>
      <td>10</td>
      <td>RM</td>
      <td>F</td>
      <td>15.0</td>
      <td>14.0</td>
    </tr>
    <tr>
      <th>35547</th>
      <td>35548</td>
      <td>12</td>
      <td>31</td>
      <td>2002</td>
      <td>7</td>
      <td>DO</td>
      <td>M</td>
      <td>36.0</td>
      <td>51.0</td>
    </tr>
  </tbody>
</table>
<p>2078 rows × 9 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-65a153c5-f965-4ff3-a706-28bf01d12579')"
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
          document.querySelector('#df-65a153c5-f965-4ff3-a706-28bf01d12579 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-65a153c5-f965-4ff3-a706-28bf01d12579');
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





```python
#get the last ten 
survey_sub2_last10 = surveys_df2.tail(10)
```


```python
# Stack the DataFrames on top of each other
vertical_stack2 = pd.concat([surveys_df, surveys_df2], axis=0)

# Place the DataFrames side by side
horizontal_stack2 = pd.concat([surveys_df, surveys_df2], axis=1)
```


```python
#find the mean year for each sex 
vertical_stack2.groupby('sex')['year'].mean()
```




    sex
    F    2001.611141
    M    2001.570054
    Name: year, dtype: float64




```python
#save your vertical stack 
vertical_stack2.to_csv('vertical.csv')
```

# Joining DataFrames

We concatenated our DataFrames and added them to each other, stacking them vertically or side by side.

- We need to join the duplicate rows across both data frames. 

- Combining DataFrames using a common field is called “joining”. 

- The columns containing the same values are called “join key(s)”. 

- Joining DataFrames in this way is often useful when one data frame is a “lookup table” containing additional data that we want to include in the other.

- For example, the species.csv file we’ve been working with is a lookup table. It contains the genus, species, and taxa code for 55 species, which is unique.

Storing data in this way has many benefits, including:
- consistency
- easy for us to change the species information once without finding each instance of it in the more extensive survey data.
- optimizes the size of our data.



# Joining Two DataFrames

To better understand joins, let’s grab the first 10 lines of our data as a subset to work with


```python
# Read in first 10 lines of surveys table
survey_sub = surveys_df.head(10)
survey_sub
```





  <div id="df-1c7b6b53-0009-4b31-b2be-14f96a5c0266">
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
      <th>record_id</th>
      <th>month</th>
      <th>day</th>
      <th>year</th>
      <th>site_id</th>
      <th>species_id</th>
      <th>sex</th>
      <th>hindfoot_length</th>
      <th>weight</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>31710</th>
      <td>31711</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>1</td>
      <td>PB</td>
      <td>F</td>
      <td>26.0</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>31711</th>
      <td>31712</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>1</td>
      <td>DM</td>
      <td>M</td>
      <td>37.0</td>
      <td>43.0</td>
    </tr>
    <tr>
      <th>31712</th>
      <td>31713</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>1</td>
      <td>PB</td>
      <td>M</td>
      <td>29.0</td>
      <td>44.0</td>
    </tr>
    <tr>
      <th>31713</th>
      <td>31714</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>1</td>
      <td>DO</td>
      <td>M</td>
      <td>34.0</td>
      <td>53.0</td>
    </tr>
    <tr>
      <th>31714</th>
      <td>31715</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>2</td>
      <td>OT</td>
      <td>M</td>
      <td>20.0</td>
      <td>27.0</td>
    </tr>
    <tr>
      <th>31715</th>
      <td>31716</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>2</td>
      <td>RM</td>
      <td>M</td>
      <td>17.0</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>31716</th>
      <td>31717</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>2</td>
      <td>NL</td>
      <td>M</td>
      <td>33.0</td>
      <td>121.0</td>
    </tr>
    <tr>
      <th>31717</th>
      <td>31718</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>2</td>
      <td>DM</td>
      <td>F</td>
      <td>34.0</td>
      <td>44.0</td>
    </tr>
    <tr>
      <th>31718</th>
      <td>31719</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>2</td>
      <td>PB</td>
      <td>M</td>
      <td>26.0</td>
      <td>42.0</td>
    </tr>
    <tr>
      <th>31719</th>
      <td>31720</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>2</td>
      <td>PB</td>
      <td>M</td>
      <td>27.0</td>
      <td>41.0</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-1c7b6b53-0009-4b31-b2be-14f96a5c0266')"
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
          document.querySelector('#df-1c7b6b53-0009-4b31-b2be-14f96a5c0266 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-1c7b6b53-0009-4b31-b2be-14f96a5c0266');
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





  <div id="df-ea6a1804-c577-4f98-a8dc-3fbe004e4c1f">
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
      <th>species_id</th>
      <th>genus</th>
      <th>species</th>
      <th>taxa</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>DM</td>
      <td>Dipodomys</td>
      <td>merriami</td>
      <td>Rodent</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NL</td>
      <td>Neotoma</td>
      <td>albigula</td>
      <td>Rodent</td>
    </tr>
    <tr>
      <th>2</th>
      <td>PE</td>
      <td>Peromyscus</td>
      <td>eremicus</td>
      <td>Rodent</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-ea6a1804-c577-4f98-a8dc-3fbe004e4c1f')"
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
          document.querySelector('#df-ea6a1804-c577-4f98-a8dc-3fbe004e4c1f button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-ea6a1804-c577-4f98-a8dc-3fbe004e4c1f');
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





```python
#check what columns are the same across both dataframe
print(species_sub.columns)
# check the column
print(surveys_df.columns)

```

    Index(['species_id', 'genus', 'species', 'taxa'], dtype='object')
    Index(['record_id', 'month', 'day', 'year', 'site_id', 'species_id', 'sex',
           'hindfoot_length', 'weight'],
          dtype='object')


In this example, species_sub is the lookup table containing genus, species, and taxa names.

We want to join the data containing all the columns from species_df and survey_df. The column that is the same in both data frames is species_id. 


There are different type of joins! 


### A) Inner Join
- An inner join combines two DataFrames based on a join key and returns a new DataFrame containing only those rows with matching values in both of the original DataFrames.

- Inner joins yield a DataFrame that contains only rows where the value being joins exists in BOTH tables. 

Examples of all the methods to join together two data frames:
![img.png](https://drive.google.com/uc?id=1ZnVWxcmrXe4TySISayoLgShMS_UjCfbf)




```python
#choose the dataframe for the left, dataframe for the right
merged_inner = pd.merge(left=survey_sub, 
                        right=species_sub, 
                        left_on='species_id', 
                        right_on='species_id')
# this case `species_id` is the only column name in  both dataframes, so if we skipped `left_on`
# `right_on` arguments we would still get the same result

```





  <div id="df-4a3d1b22-5f3e-4c6e-928f-8a8f3d4cf8e2">
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
      <th>record_id</th>
      <th>month</th>
      <th>day</th>
      <th>year</th>
      <th>site_id</th>
      <th>species_id</th>
      <th>sex</th>
      <th>hindfoot_length</th>
      <th>weight</th>
      <th>genus</th>
      <th>species</th>
      <th>taxa</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>31712</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>1</td>
      <td>DM</td>
      <td>M</td>
      <td>37.0</td>
      <td>43.0</td>
      <td>Dipodomys</td>
      <td>merriami</td>
      <td>Rodent</td>
    </tr>
    <tr>
      <th>1</th>
      <td>31718</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>2</td>
      <td>DM</td>
      <td>F</td>
      <td>34.0</td>
      <td>44.0</td>
      <td>Dipodomys</td>
      <td>merriami</td>
      <td>Rodent</td>
    </tr>
    <tr>
      <th>2</th>
      <td>31717</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>2</td>
      <td>NL</td>
      <td>M</td>
      <td>33.0</td>
      <td>121.0</td>
      <td>Neotoma</td>
      <td>albigula</td>
      <td>Rodent</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-4a3d1b22-5f3e-4c6e-928f-8a8f3d4cf8e2')"
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
          document.querySelector('#df-4a3d1b22-5f3e-4c6e-928f-8a8f3d4cf8e2 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-4a3d1b22-5f3e-4c6e-928f-8a8f3d4cf8e2');
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





```python
# What's the size of the output data if you use the entire survey_df 
merged_inner = pd.merge(left=surveys_df, 
                        right=species_sub, 
                        left_on='species_id', 
                        right_on='species_id')
print(merged_inner.shape)
print(merged_inner)
```

    (371, 12)
         record_id  month  day  year  site_id species_id sex  hindfoot_length  \
    0        31712      1   21  2001        1         DM   M             37.0   
    1        31718      1   21  2001        2         DM   F             34.0   
    2        31723      1   21  2001       12         DM   F             37.0   
    3        31725      1   21  2001       12         DM   M             36.0   
    4        31731      1   21  2001       17         DM   M             37.0   
    ..         ...    ...  ...   ...      ...        ...  ..              ...   
    366      33249     12   15  2001       19         PE   F             20.0   
    367      33291     12   15  2001       23         PE   M             20.0   
    368      33293     12   15  2001       20         PE   F             20.0   
    369      33302     12   15  2001       24         PE   M             20.0   
    370      33303     12   15  2001       24         PE   M             20.0   
    
         weight       genus   species    taxa  
    0      43.0   Dipodomys  merriami  Rodent  
    1      44.0   Dipodomys  merriami  Rodent  
    2      49.0   Dipodomys  merriami  Rodent  
    3      43.0   Dipodomys  merriami  Rodent  
    4      49.0   Dipodomys  merriami  Rodent  
    ..      ...         ...       ...     ...  
    366    14.0  Peromyscus  eremicus  Rodent  
    367    18.0  Peromyscus  eremicus  Rodent  
    368    22.0  Peromyscus  eremicus  Rodent  
    369    24.0  Peromyscus  eremicus  Rodent  
    370    23.0  Peromyscus  eremicus  Rodent  
    
    [371 rows x 12 columns]



> Note: that merged_inner has fewer rows than survey_sub. This indicates that there were rows in surveys_df with value(s) for species_id that do not exist as value(s) for species_id in species_df.

# Left Joins

What if we want to add information from species_sub to survey_sub without losing any of the information from survey_sub? In this case, we use a different type of join called a “left outer join”, or a “left join”.

The result DataFrame from a left join looks similar to the result DataFrame from an inner join in terms of the columns it contains. However, unlike merged_inner, merged_left contains the same number of rows as the original survey_sub DataFrame.

> Note: a left join will still discard rows from the right DataFrame that do not have values for the join key(s) in the left DataFrame.



```python
#left join is performed in pandas by calling
#the same `merge` function used for inner join, but using the how='left' argument:
merged_left = pd.merge(left=surveys_df,
                       right=species_sub, 
                       how='left', 
                       left_on='species_id', 
                       right_on='species_id')
merged_left
```





  <div id="df-94c43ec7-8fb3-4249-ad6b-0b5b324c234b">
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
      <th>record_id</th>
      <th>month</th>
      <th>day</th>
      <th>year</th>
      <th>site_id</th>
      <th>species_id</th>
      <th>sex</th>
      <th>hindfoot_length</th>
      <th>weight</th>
      <th>genus</th>
      <th>species</th>
      <th>taxa</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>31711</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>1</td>
      <td>PB</td>
      <td>F</td>
      <td>26.0</td>
      <td>25.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>31712</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>1</td>
      <td>DM</td>
      <td>M</td>
      <td>37.0</td>
      <td>43.0</td>
      <td>Dipodomys</td>
      <td>merriami</td>
      <td>Rodent</td>
    </tr>
    <tr>
      <th>2</th>
      <td>31713</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>1</td>
      <td>PB</td>
      <td>M</td>
      <td>29.0</td>
      <td>44.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>31714</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>1</td>
      <td>DO</td>
      <td>M</td>
      <td>34.0</td>
      <td>53.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>31715</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>2</td>
      <td>OT</td>
      <td>M</td>
      <td>20.0</td>
      <td>27.0</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1429</th>
      <td>33304</td>
      <td>12</td>
      <td>15</td>
      <td>2001</td>
      <td>24</td>
      <td>RM</td>
      <td>M</td>
      <td>16.0</td>
      <td>10.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1430</th>
      <td>33305</td>
      <td>12</td>
      <td>15</td>
      <td>2001</td>
      <td>7</td>
      <td>PB</td>
      <td>M</td>
      <td>29.0</td>
      <td>44.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1431</th>
      <td>33306</td>
      <td>12</td>
      <td>15</td>
      <td>2001</td>
      <td>7</td>
      <td>OT</td>
      <td>M</td>
      <td>19.0</td>
      <td>21.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1432</th>
      <td>33307</td>
      <td>12</td>
      <td>15</td>
      <td>2001</td>
      <td>7</td>
      <td>OT</td>
      <td>M</td>
      <td>20.0</td>
      <td>19.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1433</th>
      <td>33308</td>
      <td>12</td>
      <td>15</td>
      <td>2001</td>
      <td>7</td>
      <td>PP</td>
      <td>M</td>
      <td>24.0</td>
      <td>16.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>1434 rows × 12 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-94c43ec7-8fb3-4249-ad6b-0b5b324c234b')"
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
          document.querySelector('#df-94c43ec7-8fb3-4249-ad6b-0b5b324c234b button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-94c43ec7-8fb3-4249-ad6b-0b5b324c234b');
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





```python
#look at all the rows with null
merged_left[ pd.isnull(merged_left.genus) ]
```





  <div id="df-fef4ce8c-2361-4c62-a3ff-e721fa021127">
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
      <th>record_id</th>
      <th>month</th>
      <th>day</th>
      <th>year</th>
      <th>site_id</th>
      <th>species_id</th>
      <th>sex</th>
      <th>hindfoot_length</th>
      <th>weight</th>
      <th>genus</th>
      <th>species</th>
      <th>taxa</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>31711</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>1</td>
      <td>PB</td>
      <td>F</td>
      <td>26.0</td>
      <td>25.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>31713</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>1</td>
      <td>PB</td>
      <td>M</td>
      <td>29.0</td>
      <td>44.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>31714</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>1</td>
      <td>DO</td>
      <td>M</td>
      <td>34.0</td>
      <td>53.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>31715</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>2</td>
      <td>OT</td>
      <td>M</td>
      <td>20.0</td>
      <td>27.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>31716</td>
      <td>1</td>
      <td>21</td>
      <td>2001</td>
      <td>2</td>
      <td>RM</td>
      <td>M</td>
      <td>17.0</td>
      <td>11.0</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1429</th>
      <td>33304</td>
      <td>12</td>
      <td>15</td>
      <td>2001</td>
      <td>24</td>
      <td>RM</td>
      <td>M</td>
      <td>16.0</td>
      <td>10.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1430</th>
      <td>33305</td>
      <td>12</td>
      <td>15</td>
      <td>2001</td>
      <td>7</td>
      <td>PB</td>
      <td>M</td>
      <td>29.0</td>
      <td>44.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1431</th>
      <td>33306</td>
      <td>12</td>
      <td>15</td>
      <td>2001</td>
      <td>7</td>
      <td>OT</td>
      <td>M</td>
      <td>19.0</td>
      <td>21.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1432</th>
      <td>33307</td>
      <td>12</td>
      <td>15</td>
      <td>2001</td>
      <td>7</td>
      <td>OT</td>
      <td>M</td>
      <td>20.0</td>
      <td>19.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1433</th>
      <td>33308</td>
      <td>12</td>
      <td>15</td>
      <td>2001</td>
      <td>7</td>
      <td>PP</td>
      <td>M</td>
      <td>24.0</td>
      <td>16.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>1063 rows × 12 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-fef4ce8c-2361-4c62-a3ff-e721fa021127')"
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
          document.querySelector('#df-fef4ce8c-2361-4c62-a3ff-e721fa021127 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-fef4ce8c-2361-4c62-a3ff-e721fa021127');
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




These rows are the ones where the value of species_id from survey_sub (in this case, PF) does not occur in species_sub.

# Other join types

The `pandas` merge function supports two other join types:

- Right (outer) join: Invoked by passing how='right' as an argument. Like a left join, all rows from the right DataFrame are kept, while rows from the left DataFrame without matching join key(s) values are discarded.
- Full (outer) join: Invoked by passing how='outer' as an argument. This join type returns all pairwise combinations of rows from both DataFrames; i.e., the result DataFrame will have NaN if data is missing in one of the data frames. This join type is very rarely used.


# Extra Challenge

1. Create a new DataFrame by containing the individual organisms from `surveys2002.csv` that are the species found in `speciesSubset.csv`.

2. Calculate the mean hindfoot_length by sex. 



Adapted from Monash Data Science which was orginally adapted from the Data Carpentry - Python for Ecologists and Software Carpentry - Programming with Python (used under a CC-BY 4.0 license).

