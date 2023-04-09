<a href="https://colab.research.google.com/github/theheking/intro-to-python/blob/gh-pages/2_DataFrames_Filled.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

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




    ('patient_data.csv', <http.client.HTTPMessage at 0x7f5a837053a0>)




```python
urllib.request.urlretrieve(url, 'patient_data.csv')
```




    ('patient_data.csv', <http.client.HTTPMessage at 0x7f5a83705d30>)



Next let's install the required packages for this workshop, by using ! we download and install directly into the notebook.


```python
! pip install pandas matplotlib seaborn

```

    Looking in indexes: https://pypi.org/simple, https://us-python.pkg.dev/colab-wheels/public/simple/
    Requirement already satisfied: pandas in /usr/local/lib/python3.9/dist-packages (1.4.4)
    Requirement already satisfied: matplotlib in /usr/local/lib/python3.9/dist-packages (3.7.1)
    Requirement already satisfied: seaborn in /usr/local/lib/python3.9/dist-packages (0.12.2)
    Requirement already satisfied: numpy>=1.18.5 in /usr/local/lib/python3.9/dist-packages (from pandas) (1.22.4)
    Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.9/dist-packages (from pandas) (2022.7.1)
    Requirement already satisfied: python-dateutil>=2.8.1 in /usr/local/lib/python3.9/dist-packages (from pandas) (2.8.2)
    Requirement already satisfied: packaging>=20.0 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (23.0)
    Requirement already satisfied: fonttools>=4.22.0 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (4.39.3)
    Requirement already satisfied: importlib-resources>=3.2.0 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (5.12.0)
    Requirement already satisfied: cycler>=0.10 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (0.11.0)
    Requirement already satisfied: contourpy>=1.0.1 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (1.0.7)
    Requirement already satisfied: pillow>=6.2.0 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (8.4.0)
    Requirement already satisfied: kiwisolver>=1.0.1 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (1.4.4)
    Requirement already satisfied: pyparsing>=2.3.1 in /usr/local/lib/python3.9/dist-packages (from matplotlib) (3.0.9)
    Requirement already satisfied: zipp>=3.1.0 in /usr/local/lib/python3.9/dist-packages (from importlib-resources>=3.2.0->matplotlib) (3.15.0)
    Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.9/dist-packages (from python-dateutil>=2.8.1->pandas) (1.16.0)


Pandas is a package. Packages are where functions are stored. You have to load a package in order to use the functions found within it. 


```python
#import pandas as a package
import pandas as pd 

#read in the patient data 
pd.read_csv('patient_data.csv', sep=',')
```





  <div id="df-6cb71573-8188-4e8f-a680-cf970b84f3e8">
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
      <td>1</td>
      <td>2</td>
      <td>M</td>
      <td>9:27 am</td>
      <td>2022</td>
      <td>1</td>
      <td>12</td>
      <td>cold</td>
      <td>27.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3</td>
      <td>M</td>
      <td>10:57 am</td>
      <td>2022</td>
      <td>1</td>
      <td>12</td>
      <td>stabbing</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2</td>
      <td>F</td>
      <td>4:33 pm</td>
      <td>2022</td>
      <td>1</td>
      <td>12</td>
      <td>faint</td>
      <td>19.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>7</td>
      <td>M</td>
      <td>4:52 pm</td>
      <td>2022</td>
      <td>1</td>
      <td>12</td>
      <td>jaundice</td>
      <td>19.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>3</td>
      <td>M</td>
      <td>7:26 pm</td>
      <td>2022</td>
      <td>1</td>
      <td>12</td>
      <td>NaN</td>
      <td>36.0</td>
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
      <th>1186</th>
      <td>1187</td>
      <td>16</td>
      <td>F</td>
      <td>4:00 pm</td>
      <td>2022</td>
      <td>11</td>
      <td>8</td>
      <td>myeloma</td>
      <td>36.0</td>
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
    <tr>
      <th>1188</th>
      <td>1189</td>
      <td>4</td>
      <td>F</td>
      <td>9:45 am</td>
      <td>2022</td>
      <td>11</td>
      <td>25</td>
      <td>septic</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>1189</th>
      <td>1190</td>
      <td>13</td>
      <td>M</td>
      <td>8:05 am</td>
      <td>2022</td>
      <td>11</td>
      <td>12</td>
      <td>aortic anurysm</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>1190</th>
      <td>1191</td>
      <td>5</td>
      <td>F</td>
      <td>1:17 pm</td>
      <td>2022</td>
      <td>11</td>
      <td>5</td>
      <td>overdose</td>
      <td>38.0</td>
    </tr>
  </tbody>
</table>
<p>1191 rows × 9 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-6cb71573-8188-4e8f-a680-cf970b84f3e8')"
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
          document.querySelector('#df-6cb71573-8188-4e8f-a680-cf970b84f3e8 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-6cb71573-8188-4e8f-a680-cf970b84f3e8');
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
#we have read it in we haven't saved it to an object
patient_df = pd.read_csv("patient_data.csv") # This is assigning it to a variable
patient_df.head() # this prints out the first rows


```





  <div id="df-75cb478b-8ce6-4c70-bd1f-605ed1d2c3cb">
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
      <td>1</td>
      <td>2</td>
      <td>M</td>
      <td>9:27 am</td>
      <td>2022</td>
      <td>1</td>
      <td>12</td>
      <td>cold</td>
      <td>27.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3</td>
      <td>M</td>
      <td>10:57 am</td>
      <td>2022</td>
      <td>1</td>
      <td>12</td>
      <td>stabbing</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2</td>
      <td>F</td>
      <td>4:33 pm</td>
      <td>2022</td>
      <td>1</td>
      <td>12</td>
      <td>faint</td>
      <td>19.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>7</td>
      <td>M</td>
      <td>4:52 pm</td>
      <td>2022</td>
      <td>1</td>
      <td>12</td>
      <td>jaundice</td>
      <td>19.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>3</td>
      <td>M</td>
      <td>7:26 pm</td>
      <td>2022</td>
      <td>1</td>
      <td>12</td>
      <td>NaN</td>
      <td>36.0</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-75cb478b-8ce6-4c70-bd1f-605ed1d2c3cb')"
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
          document.querySelector('#df-75cb478b-8ce6-4c70-bd1f-605ed1d2c3cb button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-75cb478b-8ce6-4c70-bd1f-605ed1d2c3cb');
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
# we can also check what type the DF is... 
print(type(patient_df)) # Can you guess?!
print(patient_df.dtypes) # What data types does it contain
```

    <class 'pandas.core.frame.DataFrame'>
    patient_id      int64
    site_id         int64
    sex            object
    time           object
    year           object
    month          object
    day            object
    illness        object
    weight        float64
    dtype: object


## Accessing the data from the data frame

Now we have the data, we need to use pandas as a way of processing it. Checking out the documentation is always super helpful (https://pandas.pydata.org/docs/)! 

Thankfully with programming you will not have a closed book test ever so really capitalise on the resources you have online. 




#### What we are doing next: 
1. Subset the first 20 rows of the dataframe 
2. Subset the last 10 rows of the dataframe
3. Finding the columns in the dataframe


```python
? pd.DataFrame.head
```


```python
patient_df.head(20)
```





  <div id="df-34b3f479-3ef0-44b7-b375-32f10abcccec">
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
      <td>1</td>
      <td>2</td>
      <td>M</td>
      <td>9:27 am</td>
      <td>2022</td>
      <td>1</td>
      <td>12</td>
      <td>cold</td>
      <td>27.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3</td>
      <td>M</td>
      <td>10:57 am</td>
      <td>2022</td>
      <td>1</td>
      <td>12</td>
      <td>stabbing</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2</td>
      <td>F</td>
      <td>4:33 pm</td>
      <td>2022</td>
      <td>1</td>
      <td>12</td>
      <td>faint</td>
      <td>19.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>7</td>
      <td>M</td>
      <td>4:52 pm</td>
      <td>2022</td>
      <td>1</td>
      <td>12</td>
      <td>jaundice</td>
      <td>19.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>3</td>
      <td>M</td>
      <td>7:26 pm</td>
      <td>2022</td>
      <td>1</td>
      <td>12</td>
      <td>NaN</td>
      <td>36.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>1</td>
      <td>M</td>
      <td>6:24 am</td>
      <td>2022</td>
      <td>2</td>
      <td>12</td>
      <td>neck dissection</td>
      <td>34.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>2</td>
      <td>F</td>
      <td>2:57 pm</td>
      <td>2022</td>
      <td>2</td>
      <td>12</td>
      <td>myeloma</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>1</td>
      <td>M</td>
      <td>3:45 pm</td>
      <td>2022</td>
      <td>2</td>
      <td>12</td>
      <td>nstemi</td>
      <td>38.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9</td>
      <td>1</td>
      <td>F</td>
      <td>7:06 pm</td>
      <td>2022</td>
      <td>2</td>
      <td>12</td>
      <td>septic</td>
      <td>29.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>6</td>
      <td>F</td>
      <td>3:23 am</td>
      <td>2022</td>
      <td>3</td>
      <td>12</td>
      <td>aortic anurysm</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>11</td>
      <td>5</td>
      <td>F</td>
      <td>2:14 pm</td>
      <td>2022</td>
      <td>3</td>
      <td>12</td>
      <td>overdose</td>
      <td>26.0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>12</td>
      <td>7</td>
      <td>M</td>
      <td>2:51 pm</td>
      <td>2022</td>
      <td>3</td>
      <td>12</td>
      <td>pe</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>13</td>
      <td>3</td>
      <td>M</td>
      <td>11:08 pm</td>
      <td>2022</td>
      <td>3</td>
      <td>12</td>
      <td>urinary tract infection</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>13</th>
      <td>14</td>
      <td>8</td>
      <td>NaN</td>
      <td>11:35 pm</td>
      <td>2022</td>
      <td>3</td>
      <td>12</td>
      <td>fall</td>
      <td>21.0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>15</td>
      <td>6</td>
      <td>F</td>
      <td>12:17 pm</td>
      <td>2022</td>
      <td>4</td>
      <td>12</td>
      <td>valve replacement</td>
      <td>28.0</td>
    </tr>
    <tr>
      <th>15</th>
      <td>16</td>
      <td>4</td>
      <td>F</td>
      <td>7:58 am</td>
      <td>2022</td>
      <td>5</td>
      <td>12</td>
      <td>stomach pump</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>16</th>
      <td>17</td>
      <td>3</td>
      <td>F</td>
      <td>8:39 am</td>
      <td>2022</td>
      <td>5</td>
      <td>12</td>
      <td>MVA</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>17</th>
      <td>18</td>
      <td>2</td>
      <td>M</td>
      <td>3:17 pm</td>
      <td>2022</td>
      <td>5</td>
      <td>12</td>
      <td>diabetic ketoacidosois</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>18</th>
      <td>19</td>
      <td>4</td>
      <td>NaN</td>
      <td>3:18 pm</td>
      <td>2022</td>
      <td>5</td>
      <td>12</td>
      <td>mva</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>19</th>
      <td>20</td>
      <td>11</td>
      <td>F</td>
      <td>5:34 pm</td>
      <td>2022</td>
      <td>5</td>
      <td>12</td>
      <td>NaN</td>
      <td>26.0</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-34b3f479-3ef0-44b7-b375-32f10abcccec')"
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
          document.querySelector('#df-34b3f479-3ef0-44b7-b375-32f10abcccec button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-34b3f479-3ef0-44b7-b375-32f10abcccec');
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
patient_df.tail(20) 
```





  <div id="df-f30a875b-0eba-4470-bf5c-c4b0b05737b8">
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
      <th>1171</th>
      <td>1172</td>
      <td>6</td>
      <td>F</td>
      <td>12:24 am</td>
      <td>2022</td>
      <td>11</td>
      <td>27</td>
      <td>pe</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>1172</th>
      <td>1173</td>
      <td>13</td>
      <td>F</td>
      <td>11:00 am</td>
      <td>2022</td>
      <td>11</td>
      <td>1</td>
      <td>urinary tract infection</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>1173</th>
      <td>1174</td>
      <td>13</td>
      <td>F</td>
      <td>8:20 am</td>
      <td>2022</td>
      <td>11</td>
      <td>28</td>
      <td>fall</td>
      <td>36.0</td>
    </tr>
    <tr>
      <th>1174</th>
      <td>1175</td>
      <td>16</td>
      <td>M</td>
      <td>11:10 am</td>
      <td>2022</td>
      <td>11</td>
      <td>3</td>
      <td>valve replacement</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>1175</th>
      <td>1176</td>
      <td>18</td>
      <td>F</td>
      <td>2:47 pm</td>
      <td>2022</td>
      <td>10</td>
      <td>29</td>
      <td>stomach pump</td>
      <td>21.0</td>
    </tr>
    <tr>
      <th>1176</th>
      <td>1177</td>
      <td>14</td>
      <td>M</td>
      <td>7:49 pm</td>
      <td>2022</td>
      <td>12</td>
      <td>2</td>
      <td>MVA</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1177</th>
      <td>1178</td>
      <td>16</td>
      <td>M</td>
      <td>10:30 am</td>
      <td>2022</td>
      <td>11</td>
      <td>16</td>
      <td>diabetic ketoacidosois</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1178</th>
      <td>1179</td>
      <td>18</td>
      <td>M</td>
      <td>11:40 am</td>
      <td>2022</td>
      <td>11</td>
      <td>1</td>
      <td>mva</td>
      <td>34.0</td>
    </tr>
    <tr>
      <th>1179</th>
      <td>1180</td>
      <td>4</td>
      <td>F</td>
      <td>2:30 pm</td>
      <td>2022</td>
      <td>10</td>
      <td>29</td>
      <td>NaN</td>
      <td>39.0</td>
    </tr>
    <tr>
      <th>1180</th>
      <td>1181</td>
      <td>15</td>
      <td>F</td>
      <td>1:05 pm</td>
      <td>2022</td>
      <td>11</td>
      <td>9</td>
      <td>cold</td>
      <td>36.0</td>
    </tr>
    <tr>
      <th>1181</th>
      <td>1182</td>
      <td>1</td>
      <td>F</td>
      <td>2:39 pm</td>
      <td>2022</td>
      <td>11</td>
      <td>4</td>
      <td>stabbing</td>
      <td>36.0</td>
    </tr>
    <tr>
      <th>1182</th>
      <td>1183</td>
      <td>2</td>
      <td>F</td>
      <td>5:15 pm</td>
      <td>2022</td>
      <td>11</td>
      <td>3</td>
      <td>faint</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>1183</th>
      <td>1184</td>
      <td>14</td>
      <td>F</td>
      <td>11:37 am</td>
      <td>2022</td>
      <td>12</td>
      <td>2</td>
      <td>jaundice</td>
      <td>27.0</td>
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
      <th>1185</th>
      <td>1186</td>
      <td>4</td>
      <td>F</td>
      <td>4:00 am</td>
      <td>2022</td>
      <td>11</td>
      <td>29</td>
      <td>neck dissection</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>1186</th>
      <td>1187</td>
      <td>16</td>
      <td>F</td>
      <td>4:00 pm</td>
      <td>2022</td>
      <td>11</td>
      <td>8</td>
      <td>myeloma</td>
      <td>36.0</td>
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
    <tr>
      <th>1188</th>
      <td>1189</td>
      <td>4</td>
      <td>F</td>
      <td>9:45 am</td>
      <td>2022</td>
      <td>11</td>
      <td>25</td>
      <td>septic</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>1189</th>
      <td>1190</td>
      <td>13</td>
      <td>M</td>
      <td>8:05 am</td>
      <td>2022</td>
      <td>11</td>
      <td>12</td>
      <td>aortic anurysm</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>1190</th>
      <td>1191</td>
      <td>5</td>
      <td>F</td>
      <td>1:17 pm</td>
      <td>2022</td>
      <td>11</td>
      <td>5</td>
      <td>overdose</td>
      <td>38.0</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-f30a875b-0eba-4470-bf5c-c4b0b05737b8')"
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
          document.querySelector('#df-f30a875b-0eba-4470-bf5c-c4b0b05737b8 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-f30a875b-0eba-4470-bf5c-c4b0b05737b8');
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
patient_df.columns
```




    Index(['patient_id', 'site_id', 'sex', 'time', 'year', 'month', 'day',
           'illness', 'weight'],
          dtype='object')



## Calculating Statistics From Data

So now the fun begins! You have to handle columns depending on what is in the column.

1. Find the unique data within categorical columns
2. Find data summaries of numerical columns


```python
pd.unique(patient_df['illness'])

```




    array(['cold', 'stabbing', 'faint', 'jaundice', nan, 'neck dissection',
           'myeloma', 'nstemi', 'septic', 'aortic anurysm', 'overdose', 'pe',
           'urinary tract infection', 'fall', 'valve replacement',
           'stomach pump', 'MVA', 'diabetic ketoacidosois', 'mva'],
          dtype=object)




```python
patient_df['illness'].value_counts()
```




    cold                       60
    nstemi                     60
    stabbing                   60
    aortic anurysm             60
    septic                     60
    overdose                   60
    myeloma                    60
    neck dissection            60
    jaundice                   60
    faint                      60
    pe                         59
    urinary tract infection    59
    fall                       59
    valve replacement          59
    stomach pump               59
    MVA                        59
    diabetic ketoacidosois     59
    mva                        59
    Name: illness, dtype: int64




```python
# Next we might want to "describe" a column

patient_df['site_id'].describe()

```




    count    1191.000000
    mean       11.186398
    std         6.555428
    min         1.000000
    25%         5.000000
    50%        11.000000
    75%        17.000000
    max        23.000000
    Name: site_id, dtype: float64




```python
# Or you might want to extract specific values
print(patient_df['weight'].min())
print(patient_df['weight'].max())
print(patient_df['weight'].mean())
print(patient_df['weight'].std())
print(patient_df['weight'].count())

```

    4.0
    200.0
    33.063655030800824
    22.596147280680526
    974


## Creating stats

Next we might want to create statistics on a subset of the data, for example, what is the weight if we subset first by sex?


```python
# Group data by sex
grouped_data = patient_df.groupby('sex')

# Summary statistics for all numeric columns by sex
print(grouped_data.describe())

```

        patient_id                                                            \
             count        mean         std  min    25%    50%    75%     max   
    sex                                                                        
    F        519.0  625.845857  356.728090  3.0  320.5  650.0  944.5  1191.0   
    M        507.0  587.398422  352.667776  1.0  258.0  601.0  898.5  1190.0   
    
        site_id             ...             weight                             \
          count       mean  ...   75%   max  count       mean        std  min   
    sex                     ...                                                 
    F     519.0  11.190751  ...  17.0  23.0  437.0  31.228833  18.254264  4.0   
    M     507.0  10.921105  ...  17.0  23.0  416.0  35.478365  26.115305  4.0   
    
                                  
          25%   50%   75%    max  
    sex                           
    F    20.0  29.0  42.0  187.0  
    M    20.0  32.0  44.0  200.0  
    
    [2 rows x 24 columns]



```python

# Provide the mean for each numeric column by sex
# As above, only the last command shows output below - you can try the others above in new cells
print(grouped_data.mean())
```

         patient_id    site_id     weight
    sex                                  
    F    625.845857  11.190751  31.228833
    M    587.398422  10.921105  35.478365


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





  <div id="df-21576f9c-f995-429a-850c-8796ea3692b5">
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
      <th></th>
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>max</th>
    </tr>
    <tr>
      <th>site_id</th>
      <th>sex</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">1</th>
      <th>F</th>
      <td>28.0</td>
      <td>35.000000</td>
      <td>26.577629</td>
      <td>11.0</td>
      <td>22.00</td>
      <td>29.0</td>
      <td>39.50</td>
      <td>158.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>27.0</td>
      <td>30.555556</td>
      <td>13.287743</td>
      <td>4.0</td>
      <td>19.50</td>
      <td>34.0</td>
      <td>41.00</td>
      <td>53.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">2</th>
      <th>F</th>
      <td>28.0</td>
      <td>34.107143</td>
      <td>32.415519</td>
      <td>7.0</td>
      <td>18.75</td>
      <td>27.0</td>
      <td>37.50</td>
      <td>187.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>54.0</td>
      <td>34.388889</td>
      <td>27.497799</td>
      <td>8.0</td>
      <td>19.00</td>
      <td>29.0</td>
      <td>43.50</td>
      <td>178.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">3</th>
      <th>F</th>
      <td>11.0</td>
      <td>31.363636</td>
      <td>12.306687</td>
      <td>14.0</td>
      <td>23.50</td>
      <td>30.0</td>
      <td>39.00</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>13.0</td>
      <td>51.769231</td>
      <td>51.016589</td>
      <td>14.0</td>
      <td>27.00</td>
      <td>36.0</td>
      <td>40.00</td>
      <td>196.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">4</th>
      <th>F</th>
      <td>31.0</td>
      <td>30.064516</td>
      <td>16.053941</td>
      <td>4.0</td>
      <td>17.00</td>
      <td>29.0</td>
      <td>41.50</td>
      <td>76.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>18.0</td>
      <td>30.444444</td>
      <td>13.600269</td>
      <td>11.0</td>
      <td>18.00</td>
      <td>29.0</td>
      <td>38.75</td>
      <td>59.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">5</th>
      <th>F</th>
      <td>29.0</td>
      <td>30.620690</td>
      <td>32.177425</td>
      <td>8.0</td>
      <td>13.00</td>
      <td>23.0</td>
      <td>38.00</td>
      <td>182.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>23.0</td>
      <td>30.391304</td>
      <td>15.455917</td>
      <td>9.0</td>
      <td>16.50</td>
      <td>26.0</td>
      <td>43.00</td>
      <td>57.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">6</th>
      <th>F</th>
      <td>17.0</td>
      <td>32.588235</td>
      <td>10.960491</td>
      <td>15.0</td>
      <td>25.00</td>
      <td>28.0</td>
      <td>43.00</td>
      <td>52.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>21.0</td>
      <td>33.761905</td>
      <td>9.364319</td>
      <td>19.0</td>
      <td>27.00</td>
      <td>35.0</td>
      <td>41.00</td>
      <td>46.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">7</th>
      <th>F</th>
      <td>3.0</td>
      <td>28.000000</td>
      <td>18.520259</td>
      <td>7.0</td>
      <td>21.00</td>
      <td>35.0</td>
      <td>38.50</td>
      <td>42.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>5.0</td>
      <td>31.400000</td>
      <td>12.116105</td>
      <td>19.0</td>
      <td>20.00</td>
      <td>34.0</td>
      <td>36.00</td>
      <td>48.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">8</th>
      <th>F</th>
      <td>26.0</td>
      <td>28.692308</td>
      <td>12.399256</td>
      <td>7.0</td>
      <td>18.75</td>
      <td>26.5</td>
      <td>35.00</td>
      <td>59.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>11.0</td>
      <td>45.636364</td>
      <td>49.459625</td>
      <td>7.0</td>
      <td>24.00</td>
      <td>33.0</td>
      <td>44.00</td>
      <td>190.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">9</th>
      <th>F</th>
      <td>33.0</td>
      <td>29.757576</td>
      <td>14.916497</td>
      <td>7.0</td>
      <td>17.00</td>
      <td>26.0</td>
      <td>44.00</td>
      <td>57.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>24.0</td>
      <td>46.833333</td>
      <td>45.333227</td>
      <td>9.0</td>
      <td>24.75</td>
      <td>38.0</td>
      <td>45.25</td>
      <td>199.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">10</th>
      <th>F</th>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>M</th>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">11</th>
      <th>F</th>
      <td>26.0</td>
      <td>30.307692</td>
      <td>12.714619</td>
      <td>8.0</td>
      <td>21.50</td>
      <td>29.0</td>
      <td>39.75</td>
      <td>55.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>30.0</td>
      <td>31.566667</td>
      <td>19.352775</td>
      <td>11.0</td>
      <td>17.50</td>
      <td>29.0</td>
      <td>44.50</td>
      <td>106.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">12</th>
      <th>F</th>
      <td>27.0</td>
      <td>29.074074</td>
      <td>13.170263</td>
      <td>7.0</td>
      <td>18.00</td>
      <td>29.0</td>
      <td>39.50</td>
      <td>52.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>25.0</td>
      <td>31.840000</td>
      <td>11.617802</td>
      <td>8.0</td>
      <td>21.00</td>
      <td>29.0</td>
      <td>41.00</td>
      <td>53.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">13</th>
      <th>F</th>
      <td>17.0</td>
      <td>32.176471</td>
      <td>12.836643</td>
      <td>16.0</td>
      <td>20.00</td>
      <td>31.0</td>
      <td>41.00</td>
      <td>57.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>24.0</td>
      <td>36.666667</td>
      <td>18.241536</td>
      <td>8.0</td>
      <td>25.00</td>
      <td>38.5</td>
      <td>47.00</td>
      <td>93.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">14</th>
      <th>F</th>
      <td>23.0</td>
      <td>25.304348</td>
      <td>13.854552</td>
      <td>7.0</td>
      <td>15.00</td>
      <td>20.0</td>
      <td>37.50</td>
      <td>49.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>15.0</td>
      <td>41.333333</td>
      <td>30.576991</td>
      <td>14.0</td>
      <td>20.00</td>
      <td>41.0</td>
      <td>47.50</td>
      <td>140.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">15</th>
      <th>F</th>
      <td>7.0</td>
      <td>33.000000</td>
      <td>14.047538</td>
      <td>8.0</td>
      <td>27.50</td>
      <td>36.0</td>
      <td>42.00</td>
      <td>48.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>8.0</td>
      <td>46.250000</td>
      <td>58.628979</td>
      <td>14.0</td>
      <td>19.50</td>
      <td>25.0</td>
      <td>35.25</td>
      <td>189.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">16</th>
      <th>F</th>
      <td>5.0</td>
      <td>34.800000</td>
      <td>9.038805</td>
      <td>20.0</td>
      <td>34.00</td>
      <td>36.0</td>
      <td>41.00</td>
      <td>43.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>10.0</td>
      <td>33.400000</td>
      <td>9.912954</td>
      <td>21.0</td>
      <td>25.50</td>
      <td>33.0</td>
      <td>38.50</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">17</th>
      <th>F</th>
      <td>43.0</td>
      <td>29.186047</td>
      <td>11.598965</td>
      <td>8.0</td>
      <td>20.00</td>
      <td>26.0</td>
      <td>38.00</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>36.0</td>
      <td>36.611111</td>
      <td>32.900958</td>
      <td>10.0</td>
      <td>20.75</td>
      <td>28.0</td>
      <td>45.25</td>
      <td>200.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">18</th>
      <th>F</th>
      <td>33.0</td>
      <td>32.606061</td>
      <td>14.153046</td>
      <td>11.0</td>
      <td>20.00</td>
      <td>32.0</td>
      <td>45.00</td>
      <td>57.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>26.0</td>
      <td>36.692308</td>
      <td>18.677835</td>
      <td>16.0</td>
      <td>28.00</td>
      <td>31.0</td>
      <td>43.25</td>
      <td>110.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">19</th>
      <th>F</th>
      <td>4.0</td>
      <td>39.250000</td>
      <td>4.924429</td>
      <td>35.0</td>
      <td>35.00</td>
      <td>39.0</td>
      <td>43.25</td>
      <td>44.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>7.0</td>
      <td>35.714286</td>
      <td>11.426786</td>
      <td>13.0</td>
      <td>33.50</td>
      <td>39.0</td>
      <td>41.00</td>
      <td>49.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">20</th>
      <th>F</th>
      <td>19.0</td>
      <td>32.684211</td>
      <td>14.118753</td>
      <td>7.0</td>
      <td>25.50</td>
      <td>31.0</td>
      <td>43.50</td>
      <td>59.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>19.0</td>
      <td>28.894737</td>
      <td>8.418859</td>
      <td>15.0</td>
      <td>21.50</td>
      <td>28.0</td>
      <td>36.00</td>
      <td>44.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">21</th>
      <th>F</th>
      <td>5.0</td>
      <td>26.000000</td>
      <td>14.713939</td>
      <td>11.0</td>
      <td>14.00</td>
      <td>28.0</td>
      <td>29.00</td>
      <td>48.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>8.0</td>
      <td>30.875000</td>
      <td>12.264205</td>
      <td>14.0</td>
      <td>19.25</td>
      <td>34.0</td>
      <td>40.50</td>
      <td>46.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">22</th>
      <th>F</th>
      <td>20.0</td>
      <td>37.700000</td>
      <td>21.516456</td>
      <td>8.0</td>
      <td>24.75</td>
      <td>36.0</td>
      <td>42.50</td>
      <td>113.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>10.0</td>
      <td>31.200000</td>
      <td>14.289079</td>
      <td>13.0</td>
      <td>19.50</td>
      <td>31.5</td>
      <td>44.50</td>
      <td>48.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">23</th>
      <th>F</th>
      <td>2.0</td>
      <td>40.500000</td>
      <td>0.707107</td>
      <td>40.0</td>
      <td>40.25</td>
      <td>40.5</td>
      <td>40.75</td>
      <td>41.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>2.0</td>
      <td>44.000000</td>
      <td>2.828427</td>
      <td>42.0</td>
      <td>43.00</td>
      <td>44.0</td>
      <td>45.00</td>
      <td>46.0</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-21576f9c-f995-429a-850c-8796ea3692b5')"
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
          document.querySelector('#df-21576f9c-f995-429a-850c-8796ea3692b5 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-21576f9c-f995-429a-850c-8796ea3692b5');
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




## Summary Counts in Pandas
First we number of samples for each . We can do this in a few ways, but we'll use groupby combined with a `count()` method.



```python
# Count the number of samples by species
patient_counts = patient_df.groupby('illness')['patient_id'].count()
print(patient_counts)
```

## Basic Math Functions

The nice thing about dataframes is that you can do math on them really easily which is awesome! 

So we can calculate the difference between columns, multiply them etc.


```python
# Multiply all weight values by 2 but does not change the original weight data
patient_df['weight']*2

```




    0       54.0
    1       74.0
    2       38.0
    3       38.0
    4       72.0
            ... 
    1186    72.0
    1187    70.0
    1188    74.0
    1189    70.0
    1190    76.0
    Name: weight, Length: 1191, dtype: float64




```python

patient_df.columns
```




    Index(['patient_id', 'site_id', 'sex', 'time', 'year', 'month', 'day',
           'illness', 'weight'],
          dtype='object')




```python
patient_df['weight_x_site'] = patient_df['weight']*patient_df['site_id']
patient_df['weight_x_site'] # Now you have it in a new column which is cool!
```




    0        54.0
    1       111.0
    2        38.0
    3       133.0
    4       108.0
            ...  
    1186    576.0
    1187     35.0
    1188    148.0
    1189    455.0
    1190    190.0
    Name: weight_x_site, Length: 1191, dtype: float64


Adapted from Monash Data Science which was orginally adapted from the Data Carpentry - Python for Ecologists and Software Carpentry - Programming with Python (used under a CC-BY 4.0 license).
