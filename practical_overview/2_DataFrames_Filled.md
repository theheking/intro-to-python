<a href="https://colab.research.google.com/github/theheking/intro-to-python/blob/gh-pages/2_DataFrames_Filled.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

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




    ('patient_data.csv', <http.client.HTTPMessage at 0x7f46a44b4580>)



Next let's install the required packages for this workshop, by using ! we download and install directly into the notebook.


```python
! pip install pandas matplotlib seaborn

```

    Looking in indexes: https://pypi.org/simple, https://us-python.pkg.dev/colab-wheels/public/simple/
    Requirement already satisfied: pandas in /usr/local/lib/python3.10/dist-packages (1.5.3)
    Requirement already satisfied: matplotlib in /usr/local/lib/python3.10/dist-packages (3.7.1)
    Requirement already satisfied: seaborn in /usr/local/lib/python3.10/dist-packages (0.12.2)
    Requirement already satisfied: python-dateutil>=2.8.1 in /usr/local/lib/python3.10/dist-packages (from pandas) (2.8.2)
    Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.10/dist-packages (from pandas) (2022.7.1)
    Requirement already satisfied: numpy>=1.21.0 in /usr/local/lib/python3.10/dist-packages (from pandas) (1.22.4)
    Requirement already satisfied: contourpy>=1.0.1 in /usr/local/lib/python3.10/dist-packages (from matplotlib) (1.0.7)
    Requirement already satisfied: cycler>=0.10 in /usr/local/lib/python3.10/dist-packages (from matplotlib) (0.11.0)
    Requirement already satisfied: fonttools>=4.22.0 in /usr/local/lib/python3.10/dist-packages (from matplotlib) (4.39.3)
    Requirement already satisfied: kiwisolver>=1.0.1 in /usr/local/lib/python3.10/dist-packages (from matplotlib) (1.4.4)
    Requirement already satisfied: packaging>=20.0 in /usr/local/lib/python3.10/dist-packages (from matplotlib) (23.1)
    Requirement already satisfied: pillow>=6.2.0 in /usr/local/lib/python3.10/dist-packages (from matplotlib) (8.4.0)
    Requirement already satisfied: pyparsing>=2.3.1 in /usr/local/lib/python3.10/dist-packages (from matplotlib) (3.0.9)
    Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.10/dist-packages (from python-dateutil>=2.8.1->pandas) (1.16.0)


Pandas is a package. Packages are where functions are stored. You have to load a package in order to use the functions found within it. 


```python
#import pandas as a package
import pandas as pd 

#read in the patient data 
pd.read_csv('patient_data.csv', sep=',')
```





  <div id="df-7a7cad25-6c90-477d-a9a9-c1e0a8c2b471">
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
      <th>gender</th>
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
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>overdose</td>
      <td>38.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3</td>
      <td>M</td>
      <td>10:57 am</td>
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>valve replacement</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2</td>
      <td>F</td>
      <td>4:33 pm</td>
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>MVA</td>
      <td>74.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>7</td>
      <td>M</td>
      <td>4:52 pm</td>
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>aortic aneurysm</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>3</td>
      <td>M</td>
      <td>7:26 pm</td>
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>MVA</td>
      <td>80.0</td>
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
      <td>2022.0</td>
      <td>11.0</td>
      <td>8.0</td>
      <td>MVA</td>
      <td>NaN</td>
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
      <td>pe</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1188</th>
      <td>1189</td>
      <td>4</td>
      <td>F</td>
      <td>9:45 am</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>25.0</td>
      <td>pleural effusion</td>
      <td>82.0</td>
    </tr>
    <tr>
      <th>1189</th>
      <td>1190</td>
      <td>13</td>
      <td>M</td>
      <td>8:05 am</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>12.0</td>
      <td>nstemi</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1190</th>
      <td>1191</td>
      <td>5</td>
      <td>F</td>
      <td>1:17 pm</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>5.0</td>
      <td>diabetic ketoacidosois</td>
      <td>54.0</td>
    </tr>
  </tbody>
</table>
<p>1191 rows × 9 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-7a7cad25-6c90-477d-a9a9-c1e0a8c2b471')"
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
          document.querySelector('#df-7a7cad25-6c90-477d-a9a9-c1e0a8c2b471 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-7a7cad25-6c90-477d-a9a9-c1e0a8c2b471');
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





  <div id="df-2371a223-fe7a-4296-9c4d-7f9969ab6d48">
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
      <th>gender</th>
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
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>overdose</td>
      <td>38.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3</td>
      <td>M</td>
      <td>10:57 am</td>
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>valve replacement</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2</td>
      <td>F</td>
      <td>4:33 pm</td>
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>MVA</td>
      <td>74.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>7</td>
      <td>M</td>
      <td>4:52 pm</td>
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>aortic aneurysm</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>3</td>
      <td>M</td>
      <td>7:26 pm</td>
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>MVA</td>
      <td>80.0</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-2371a223-fe7a-4296-9c4d-7f9969ab6d48')"
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
          document.querySelector('#df-2371a223-fe7a-4296-9c4d-7f9969ab6d48 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-2371a223-fe7a-4296-9c4d-7f9969ab6d48');
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
    gender         object
    time           object
    year          float64
    month         float64
    day           float64
    illness        object
    weight        float64
    dtype: object


## Accessing the data from the data frame

Now we have the data, we need to use pandas to process it. Checking out the documentation is always super helpful (https://pandas.pydata.org/docs/)! 

Thankfully, with programming, you will never have a closed book test, so capitalise on the resources you have online. 



#### What we are doing next: 
1. Subset the first 20 rows of the data frame 
2. Subset the last 10 rows of the data frame
3. Finding the columns in the data frame


```python
#check the head function
? pd.DataFrame.head
```


```python
#print the top 20 rows
patient_df.head(20)
```





  <div id="df-05a51b86-c609-4c94-964a-ee26af368d91">
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
      <th>gender</th>
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
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>overdose</td>
      <td>38.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3</td>
      <td>M</td>
      <td>10:57 am</td>
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>valve replacement</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2</td>
      <td>F</td>
      <td>4:33 pm</td>
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>MVA</td>
      <td>74.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>7</td>
      <td>M</td>
      <td>4:52 pm</td>
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>aortic aneurysm</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>3</td>
      <td>M</td>
      <td>7:26 pm</td>
      <td>2022.0</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>MVA</td>
      <td>80.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>1</td>
      <td>M</td>
      <td>6:24 am</td>
      <td>2022.0</td>
      <td>2.0</td>
      <td>12.0</td>
      <td>myeloma</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>2</td>
      <td>F</td>
      <td>2:57 pm</td>
      <td>2022.0</td>
      <td>2.0</td>
      <td>12.0</td>
      <td>septic</td>
      <td>92.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>1</td>
      <td>M</td>
      <td>3:45 pm</td>
      <td>2022.0</td>
      <td>2.0</td>
      <td>12.0</td>
      <td>overdose</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9</td>
      <td>1</td>
      <td>F</td>
      <td>7:06 pm</td>
      <td>2022.0</td>
      <td>2.0</td>
      <td>12.0</td>
      <td>urinary tract infection</td>
      <td>42.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>6</td>
      <td>F</td>
      <td>3:23 am</td>
      <td>2022.0</td>
      <td>3.0</td>
      <td>12.0</td>
      <td>pe</td>
      <td>100.0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>11</td>
      <td>5</td>
      <td>F</td>
      <td>2:14 pm</td>
      <td>2022.0</td>
      <td>3.0</td>
      <td>12.0</td>
      <td>hyponatraemia</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>11</th>
      <td>12</td>
      <td>7</td>
      <td>M</td>
      <td>2:51 pm</td>
      <td>2022.0</td>
      <td>3.0</td>
      <td>12.0</td>
      <td>MVA</td>
      <td>68.0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>13</td>
      <td>3</td>
      <td>M</td>
      <td>11:08 pm</td>
      <td>2022.0</td>
      <td>3.0</td>
      <td>12.0</td>
      <td>neck dissection</td>
      <td>NaN</td>
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
      <td>NaN</td>
      <td>92.0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>15</td>
      <td>6</td>
      <td>F</td>
      <td>12:17 pm</td>
      <td>2022.0</td>
      <td>4.0</td>
      <td>12.0</td>
      <td>faint</td>
      <td>88.0</td>
    </tr>
    <tr>
      <th>15</th>
      <td>16</td>
      <td>4</td>
      <td>F</td>
      <td>7:58 am</td>
      <td>2022.0</td>
      <td>5.0</td>
      <td>12.0</td>
      <td>stomach pump</td>
      <td>76.0</td>
    </tr>
    <tr>
      <th>16</th>
      <td>17</td>
      <td>3</td>
      <td>F</td>
      <td>8:39 am</td>
      <td>2022.0</td>
      <td>5.0</td>
      <td>12.0</td>
      <td>pe</td>
      <td>46.0</td>
    </tr>
    <tr>
      <th>17</th>
      <td>18</td>
      <td>2</td>
      <td>M</td>
      <td>3:17 pm</td>
      <td>2022.0</td>
      <td>5.0</td>
      <td>12.0</td>
      <td>jaundice</td>
      <td>58.0</td>
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
      <td>jaundice</td>
      <td>52.0</td>
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
      <td>jaundice</td>
      <td>52.0</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-05a51b86-c609-4c94-964a-ee26af368d91')"
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
          document.querySelector('#df-05a51b86-c609-4c94-964a-ee26af368d91 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-05a51b86-c609-4c94-964a-ee26af368d91');
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
#print the final 20 rows
patient_df.tail(20) 
```





  <div id="df-90beea92-6909-413b-b443-52f7b566a467">
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
      <th>gender</th>
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
      <td>2022.0</td>
      <td>11.0</td>
      <td>27.0</td>
      <td>MVA</td>
      <td>48.0</td>
    </tr>
    <tr>
      <th>1172</th>
      <td>1173</td>
      <td>13</td>
      <td>F</td>
      <td>11:00 am</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>1.0</td>
      <td>stabbing</td>
      <td>84.0</td>
    </tr>
    <tr>
      <th>1173</th>
      <td>1174</td>
      <td>13</td>
      <td>F</td>
      <td>8:20 am</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>63.0</td>
      <td>fall</td>
      <td>52.0</td>
    </tr>
    <tr>
      <th>1174</th>
      <td>1175</td>
      <td>16</td>
      <td>M</td>
      <td>11:10 am</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>3.0</td>
      <td>neck dissection</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>1175</th>
      <td>1176</td>
      <td>18</td>
      <td>F</td>
      <td>2:47 pm</td>
      <td>2022.0</td>
      <td>10.0</td>
      <td>29.0</td>
      <td>diabetic ketoacidosois</td>
      <td>62.0</td>
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
      <td>90.0</td>
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
      <td>fall</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th>1178</th>
      <td>1179</td>
      <td>18</td>
      <td>M</td>
      <td>11:40 am</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>1.0</td>
      <td>NaN</td>
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
      <td>nstemi</td>
      <td>38.0</td>
    </tr>
    <tr>
      <th>1180</th>
      <td>1181</td>
      <td>15</td>
      <td>F</td>
      <td>1:05 pm</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>9.0</td>
      <td>urinary tract infection</td>
      <td>54.0</td>
    </tr>
    <tr>
      <th>1181</th>
      <td>1182</td>
      <td>1</td>
      <td>F</td>
      <td>2:39 pm</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>4.0</td>
      <td>fall</td>
      <td>51.0</td>
    </tr>
    <tr>
      <th>1182</th>
      <td>1183</td>
      <td>2</td>
      <td>F</td>
      <td>5:15 pm</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>3.0</td>
      <td>myeloma</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>1183</th>
      <td>1184</td>
      <td>14</td>
      <td>F</td>
      <td>11:37 am</td>
      <td>2022.0</td>
      <td>12.0</td>
      <td>2.0</td>
      <td>myeloma</td>
      <td>90.0</td>
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
      <td>MVA</td>
      <td>56.0</td>
    </tr>
    <tr>
      <th>1185</th>
      <td>1186</td>
      <td>4</td>
      <td>F</td>
      <td>4:00 am</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>29.0</td>
      <td>pe</td>
      <td>96.0</td>
    </tr>
    <tr>
      <th>1186</th>
      <td>1187</td>
      <td>16</td>
      <td>F</td>
      <td>4:00 pm</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>8.0</td>
      <td>MVA</td>
      <td>NaN</td>
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
      <td>pe</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1188</th>
      <td>1189</td>
      <td>4</td>
      <td>F</td>
      <td>9:45 am</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>25.0</td>
      <td>pleural effusion</td>
      <td>82.0</td>
    </tr>
    <tr>
      <th>1189</th>
      <td>1190</td>
      <td>13</td>
      <td>M</td>
      <td>8:05 am</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>12.0</td>
      <td>nstemi</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1190</th>
      <td>1191</td>
      <td>5</td>
      <td>F</td>
      <td>1:17 pm</td>
      <td>2022.0</td>
      <td>11.0</td>
      <td>5.0</td>
      <td>diabetic ketoacidosois</td>
      <td>54.0</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-90beea92-6909-413b-b443-52f7b566a467')"
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
          document.querySelector('#df-90beea92-6909-413b-b443-52f7b566a467 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-90beea92-6909-413b-b443-52f7b566a467');
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
#print the columns 
patient_df.columns
```




    Index(['patient_id', 'site_id', 'gender', 'time', 'year', 'month', 'day',
           'illness', 'weight'],
          dtype='object')



## Calculating Statistics From Data

So now the fun begins! First, you have to handle columns depending on what is in the column.

1. Find the unique data within categorical columns
2. Find data summaries of numerical columns


```python
#find the unique values in the illness 
pd.unique(patient_df['illness'])

```




    array(['overdose', 'valve replacement', 'MVA', 'aortic aneurysm',
           'myeloma', 'septic', 'urinary tract infection', 'pe',
           'hyponatraemia', 'neck dissection', nan, 'faint', 'stomach pump',
           'jaundice', 'seizure', 'sob', 'diabetic ketoacidosois', 'stabbing',
           'fall', 'brainstem lesion', 'heart failure', 'nstemi', 'cold',
           'pleural effusion', 'acute asthma', 'lung transplant',
           'subdural haemotoma'], dtype=object)




```python
#use value counts to find the number of times a unique value occurs
patient_df['illness'].value_counts()
```




    MVA                        116
    aortic aneurysm             60
    nstemi                      60
    pe                          59
    fall                        59
    diabetic ketoacidosois      59
    sob                         58
    valve replacement           56
    urinary tract infection     49
    hyponatraemia               48
    cold                        43
    faint                       41
    overdose                    40
    myeloma                     38
    stomach pump                37
    stabbing                    35
    acute asthma                33
    septic                      32
    neck dissection             28
    jaundice                    27
    lung transplant             23
    brainstem lesion            23
    heart failure               21
    pleural effusion            16
    seizure                     10
    subdural haemotoma           4
    Name: illness, dtype: int64




```python
# next we might want to "describe" the site id column
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
# extract specific values min max mean std count for weight
print(patient_df['weight'].min())
print(patient_df['weight'].max())
print(patient_df['weight'].mean())
print(patient_df['weight'].std())
print(patient_df['weight'].count())

```

    14.0
    398.0
    71.09349593495935
    37.358419043398506
    984


## Creating stats

Next we might want to create statistics on a subset of the data, for example, what is the weight if we subset first by gender?


```python
# Group data by gender
grouped_data = patient_df.groupby('gender')

# Summary statistics for all numeric columns by gender
print(grouped_data.describe())

```

           patient_id                                                            \
                count        mean         std  min    25%    50%    75%     max   
    gender                                                                        
    F           519.0  625.845857  356.728090  3.0  320.5  650.0  944.5  1191.0   
    M           507.0  587.398422  352.667776  1.0  258.0  601.0  898.5  1190.0   
    
           site_id             ...   day       weight                              \
             count       mean  ...   75%   max  count       mean        std   min   
    gender                     ...                                                  
    F        519.0  11.190751  ...  23.0  63.0  431.0  69.320186  24.628676  18.0   
    M        507.0  10.921105  ...  23.0  63.0  415.0  73.440964  48.165884  14.0   
    
                                     
             25%   50%   75%    max  
    gender                           
    F       51.0  66.0  84.0  226.0  
    M       50.0  65.0  84.0  398.0  
    
    [2 rows x 48 columns]



```python
# Provide the mean for each numeric column by gender
# As above, only the last command shows output below - you can try the others above in new cells
print(grouped_data.mean())
```

            patient_id    site_id         year      month        day     weight
    gender                                                                     
    F       625.845857  11.190751  2022.049310  10.240631  17.266272  69.320186
    M       587.398422  10.921105  2021.814664  10.061100  17.419552  73.440964


    <ipython-input-93-bba4e173eead>:3: FutureWarning: The default value of numeric_only in DataFrameGroupBy.mean is deprecated. In a future version, numeric_only will default to False. Either specify numeric_only or select only columns which should be valid for the function.
      print(grouped_data.mean())


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




```python
patient_df["gender"].value_counts()
```




    F    519
    M    507
    Name: gender, dtype: int64




```python
#perform challenge
grouped_data2 = patient_df.groupby(['site_id','gender'])
grouped_data2.mean()

```

    <ipython-input-99-e43a6bdeebc6>:3: FutureWarning: The default value of numeric_only in DataFrameGroupBy.mean is deprecated. In a future version, numeric_only will default to False. Either specify numeric_only or select only columns which should be valid for the function.
      grouped_data2.mean()






  <div id="df-8811921c-1ce0-46af-91ee-9e57abea853b">
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
      <th>patient_id</th>
      <th>year</th>
      <th>month</th>
      <th>day</th>
      <th>weight</th>
      <th>weight_x_site</th>
    </tr>
    <tr>
      <th>site_id</th>
      <th>gender</th>
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
      <td>705.827586</td>
      <td>2022.074074</td>
      <td>9.444444</td>
      <td>19.111111</td>
      <td>60.304348</td>
      <td>60.304348</td>
    </tr>
    <tr>
      <th>M</th>
      <td>643.870968</td>
      <td>2022.137931</td>
      <td>8.793103</td>
      <td>17.172414</td>
      <td>72.720000</td>
      <td>72.720000</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">2</th>
      <th>F</th>
      <td>629.068966</td>
      <td>2022.000000</td>
      <td>9.965517</td>
      <td>12.517241</td>
      <td>64.240000</td>
      <td>128.480000</td>
    </tr>
    <tr>
      <th>M</th>
      <td>571.637931</td>
      <td>2022.127273</td>
      <td>9.836364</td>
      <td>14.545455</td>
      <td>70.958333</td>
      <td>141.916667</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">3</th>
      <th>F</th>
      <td>496.083333</td>
      <td>2022.166667</td>
      <td>9.500000</td>
      <td>21.250000</td>
      <td>74.833333</td>
      <td>224.500000</td>
    </tr>
    <tr>
      <th>M</th>
      <td>414.230769</td>
      <td>2022.000000</td>
      <td>8.916667</td>
      <td>20.916667</td>
      <td>58.555556</td>
      <td>175.666667</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">4</th>
      <th>F</th>
      <td>645.833333</td>
      <td>2022.000000</td>
      <td>10.771429</td>
      <td>21.600000</td>
      <td>69.300000</td>
      <td>277.200000</td>
    </tr>
    <tr>
      <th>M</th>
      <td>753.200000</td>
      <td>2022.050000</td>
      <td>10.600000</td>
      <td>17.300000</td>
      <td>88.214286</td>
      <td>352.857143</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">5</th>
      <th>F</th>
      <td>576.193548</td>
      <td>2022.000000</td>
      <td>10.806452</td>
      <td>20.161290</td>
      <td>62.461538</td>
      <td>312.307692</td>
    </tr>
    <tr>
      <th>M</th>
      <td>619.033333</td>
      <td>2022.000000</td>
      <td>10.633333</td>
      <td>19.866667</td>
      <td>70.173913</td>
      <td>350.869565</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">6</th>
      <th>F</th>
      <td>669.210526</td>
      <td>2022.055556</td>
      <td>9.555556</td>
      <td>26.388889</td>
      <td>71.933333</td>
      <td>431.600000</td>
    </tr>
    <tr>
      <th>M</th>
      <td>581.380952</td>
      <td>2022.047619</td>
      <td>10.380952</td>
      <td>20.047619</td>
      <td>64.352941</td>
      <td>386.117647</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">7</th>
      <th>F</th>
      <td>115.333333</td>
      <td>2022.000000</td>
      <td>12.000000</td>
      <td>15.666667</td>
      <td>29.000000</td>
      <td>203.000000</td>
    </tr>
    <tr>
      <th>M</th>
      <td>67.400000</td>
      <td>2022.000000</td>
      <td>8.000000</td>
      <td>13.200000</td>
      <td>71.000000</td>
      <td>497.000000</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">8</th>
      <th>F</th>
      <td>669.241379</td>
      <td>2022.000000</td>
      <td>11.034483</td>
      <td>14.827586</td>
      <td>69.923077</td>
      <td>559.384615</td>
    </tr>
    <tr>
      <th>M</th>
      <td>703.461538</td>
      <td>2022.000000</td>
      <td>10.846154</td>
      <td>10.538462</td>
      <td>62.000000</td>
      <td>496.000000</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">9</th>
      <th>F</th>
      <td>663.581395</td>
      <td>2022.071429</td>
      <td>10.595238</td>
      <td>14.214286</td>
      <td>73.750000</td>
      <td>663.750000</td>
    </tr>
    <tr>
      <th>M</th>
      <td>626.464286</td>
      <td>2022.071429</td>
      <td>10.464286</td>
      <td>14.535714</td>
      <td>84.150000</td>
      <td>757.350000</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">10</th>
      <th>F</th>
      <td>31.000000</td>
      <td>2022.000000</td>
      <td>7.000000</td>
      <td>12.000000</td>
      <td>86.000000</td>
      <td>860.000000</td>
    </tr>
    <tr>
      <th>M</th>
      <td>201.000000</td>
      <td>2022.000000</td>
      <td>12.000000</td>
      <td>16.000000</td>
      <td>40.000000</td>
      <td>400.000000</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">11</th>
      <th>F</th>
      <td>593.000000</td>
      <td>2022.064516</td>
      <td>9.580645</td>
      <td>19.741935</td>
      <td>68.925926</td>
      <td>758.185185</td>
    </tr>
    <tr>
      <th>M</th>
      <td>616.277778</td>
      <td>2018.657143</td>
      <td>9.400000</td>
      <td>22.685714</td>
      <td>81.750000</td>
      <td>899.250000</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">12</th>
      <th>F</th>
      <td>695.000000</td>
      <td>2022.032258</td>
      <td>10.709677</td>
      <td>15.387097</td>
      <td>56.571429</td>
      <td>678.857143</td>
    </tr>
    <tr>
      <th>M</th>
      <td>669.259259</td>
      <td>2022.076923</td>
      <td>10.615385</td>
      <td>19.269231</td>
      <td>63.333333</td>
      <td>760.000000</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">13</th>
      <th>F</th>
      <td>646.650000</td>
      <td>2022.050000</td>
      <td>10.450000</td>
      <td>20.300000</td>
      <td>65.928571</td>
      <td>857.071429</td>
    </tr>
    <tr>
      <th>M</th>
      <td>546.600000</td>
      <td>2022.000000</td>
      <td>10.692308</td>
      <td>16.423077</td>
      <td>64.615385</td>
      <td>840.000000</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">14</th>
      <th>F</th>
      <td>630.071429</td>
      <td>2022.035714</td>
      <td>10.428571</td>
      <td>16.464286</td>
      <td>69.958333</td>
      <td>979.416667</td>
    </tr>
    <tr>
      <th>M</th>
      <td>550.681818</td>
      <td>2022.045455</td>
      <td>10.409091</td>
      <td>17.954545</td>
      <td>76.150000</td>
      <td>1066.100000</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">15</th>
      <th>F</th>
      <td>616.200000</td>
      <td>2022.000000</td>
      <td>9.700000</td>
      <td>12.900000</td>
      <td>64.285714</td>
      <td>964.285714</td>
    </tr>
    <tr>
      <th>M</th>
      <td>453.400000</td>
      <td>2022.000000</td>
      <td>9.333333</td>
      <td>18.000000</td>
      <td>66.181818</td>
      <td>992.727273</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">16</th>
      <th>F</th>
      <td>443.600000</td>
      <td>2022.000000</td>
      <td>10.444444</td>
      <td>15.888889</td>
      <td>59.428571</td>
      <td>950.857143</td>
    </tr>
    <tr>
      <th>M</th>
      <td>773.692308</td>
      <td>2022.076923</td>
      <td>10.307692</td>
      <td>14.769231</td>
      <td>79.700000</td>
      <td>1275.200000</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">17</th>
      <th>F</th>
      <td>650.163265</td>
      <td>2022.108696</td>
      <td>9.608696</td>
      <td>15.347826</td>
      <td>75.250000</td>
      <td>1279.250000</td>
    </tr>
    <tr>
      <th>M</th>
      <td>697.285714</td>
      <td>2022.025000</td>
      <td>10.475000</td>
      <td>18.400000</td>
      <td>69.891892</td>
      <td>1188.162162</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">18</th>
      <th>F</th>
      <td>673.783784</td>
      <td>2022.054054</td>
      <td>10.540541</td>
      <td>16.351351</td>
      <td>73.827586</td>
      <td>1328.896552</td>
    </tr>
    <tr>
      <th>M</th>
      <td>622.250000</td>
      <td>2022.074074</td>
      <td>10.333333</td>
      <td>17.962963</td>
      <td>66.227273</td>
      <td>1192.090909</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">19</th>
      <th>F</th>
      <td>373.800000</td>
      <td>2022.000000</td>
      <td>10.800000</td>
      <td>17.200000</td>
      <td>88.000000</td>
      <td>1672.000000</td>
    </tr>
    <tr>
      <th>M</th>
      <td>335.000000</td>
      <td>2022.166667</td>
      <td>9.750000</td>
      <td>14.666667</td>
      <td>91.000000</td>
      <td>1729.000000</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">20</th>
      <th>F</th>
      <td>604.461538</td>
      <td>2022.115385</td>
      <td>9.769231</td>
      <td>17.000000</td>
      <td>81.857143</td>
      <td>1637.142857</td>
    </tr>
    <tr>
      <th>M</th>
      <td>493.107143</td>
      <td>2022.071429</td>
      <td>9.607143</td>
      <td>17.392857</td>
      <td>87.520000</td>
      <td>1750.400000</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">21</th>
      <th>F</th>
      <td>562.571429</td>
      <td>2022.000000</td>
      <td>11.142857</td>
      <td>20.285714</td>
      <td>70.285714</td>
      <td>1476.000000</td>
    </tr>
    <tr>
      <th>M</th>
      <td>558.733333</td>
      <td>2022.000000</td>
      <td>10.142857</td>
      <td>14.857143</td>
      <td>74.214286</td>
      <td>1558.500000</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">22</th>
      <th>F</th>
      <td>649.800000</td>
      <td>2022.080000</td>
      <td>10.040000</td>
      <td>15.440000</td>
      <td>72.590909</td>
      <td>1597.000000</td>
    </tr>
    <tr>
      <th>M</th>
      <td>491.666667</td>
      <td>2022.000000</td>
      <td>9.466667</td>
      <td>18.266667</td>
      <td>59.769231</td>
      <td>1314.923077</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">23</th>
      <th>F</th>
      <td>108.500000</td>
      <td>2022.000000</td>
      <td>11.250000</td>
      <td>17.750000</td>
      <td>68.750000</td>
      <td>1581.250000</td>
    </tr>
    <tr>
      <th>M</th>
      <td>80.750000</td>
      <td>2022.000000</td>
      <td>12.000000</td>
      <td>17.500000</td>
      <td>222.000000</td>
      <td>5106.000000</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-8811921c-1ce0-46af-91ee-9e57abea853b')"
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
          document.querySelector('#df-8811921c-1ce0-46af-91ee-9e57abea853b button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-8811921c-1ce0-46af-91ee-9e57abea853b');
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
#looking at one column
grouped_data2['weight'].describe()
```





  <div id="df-a7f1551a-8111-40af-9ac9-7234e0ab60b9">
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
      <th>gender</th>
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
      <td>23.0</td>
      <td>60.304348</td>
      <td>16.888497</td>
      <td>40.0</td>
      <td>48.50</td>
      <td>56.0</td>
      <td>71.00</td>
      <td>96.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>25.0</td>
      <td>72.720000</td>
      <td>60.859483</td>
      <td>20.0</td>
      <td>46.00</td>
      <td>65.0</td>
      <td>78.00</td>
      <td>350.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">2</th>
      <th>F</th>
      <td>25.0</td>
      <td>64.240000</td>
      <td>21.405373</td>
      <td>38.0</td>
      <td>46.00</td>
      <td>63.0</td>
      <td>74.00</td>
      <td>104.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>48.0</td>
      <td>70.958333</td>
      <td>43.210498</td>
      <td>18.0</td>
      <td>48.00</td>
      <td>61.5</td>
      <td>83.75</td>
      <td>316.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">3</th>
      <th>F</th>
      <td>12.0</td>
      <td>74.833333</td>
      <td>26.114550</td>
      <td>42.0</td>
      <td>48.25</td>
      <td>80.0</td>
      <td>90.50</td>
      <td>124.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>9.0</td>
      <td>58.555556</td>
      <td>15.387585</td>
      <td>40.0</td>
      <td>52.00</td>
      <td>56.0</td>
      <td>66.00</td>
      <td>83.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">4</th>
      <th>F</th>
      <td>30.0</td>
      <td>69.300000</td>
      <td>19.839268</td>
      <td>38.0</td>
      <td>54.25</td>
      <td>71.0</td>
      <td>84.00</td>
      <td>104.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>14.0</td>
      <td>88.214286</td>
      <td>90.535313</td>
      <td>40.0</td>
      <td>52.50</td>
      <td>64.5</td>
      <td>72.00</td>
      <td>398.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">5</th>
      <th>F</th>
      <td>26.0</td>
      <td>62.461538</td>
      <td>17.641385</td>
      <td>30.0</td>
      <td>51.25</td>
      <td>58.0</td>
      <td>76.25</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>23.0</td>
      <td>70.173913</td>
      <td>49.967855</td>
      <td>40.0</td>
      <td>49.00</td>
      <td>58.0</td>
      <td>74.00</td>
      <td>286.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">6</th>
      <th>F</th>
      <td>15.0</td>
      <td>71.933333</td>
      <td>20.547738</td>
      <td>40.0</td>
      <td>55.50</td>
      <td>80.0</td>
      <td>89.00</td>
      <td>100.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>17.0</td>
      <td>64.352941</td>
      <td>20.040400</td>
      <td>38.0</td>
      <td>48.00</td>
      <td>60.0</td>
      <td>80.00</td>
      <td>100.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">7</th>
      <th>F</th>
      <td>2.0</td>
      <td>29.000000</td>
      <td>15.556349</td>
      <td>18.0</td>
      <td>23.50</td>
      <td>29.0</td>
      <td>34.50</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>3.0</td>
      <td>71.000000</td>
      <td>23.643181</td>
      <td>49.0</td>
      <td>58.50</td>
      <td>68.0</td>
      <td>82.00</td>
      <td>96.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">8</th>
      <th>F</th>
      <td>26.0</td>
      <td>69.923077</td>
      <td>17.879425</td>
      <td>40.0</td>
      <td>56.25</td>
      <td>65.5</td>
      <td>87.00</td>
      <td>100.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>11.0</td>
      <td>62.000000</td>
      <td>26.743223</td>
      <td>20.0</td>
      <td>46.00</td>
      <td>56.0</td>
      <td>83.00</td>
      <td>104.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">9</th>
      <th>F</th>
      <td>36.0</td>
      <td>73.750000</td>
      <td>30.269622</td>
      <td>18.0</td>
      <td>55.50</td>
      <td>70.0</td>
      <td>88.00</td>
      <td>206.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>20.0</td>
      <td>84.150000</td>
      <td>71.901449</td>
      <td>38.0</td>
      <td>51.50</td>
      <td>73.5</td>
      <td>83.75</td>
      <td>380.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">10</th>
      <th>F</th>
      <td>1.0</td>
      <td>86.000000</td>
      <td>NaN</td>
      <td>86.0</td>
      <td>86.00</td>
      <td>86.0</td>
      <td>86.00</td>
      <td>86.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>1.0</td>
      <td>40.000000</td>
      <td>NaN</td>
      <td>40.0</td>
      <td>40.00</td>
      <td>40.0</td>
      <td>40.00</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">11</th>
      <th>F</th>
      <td>27.0</td>
      <td>68.925926</td>
      <td>17.437638</td>
      <td>40.0</td>
      <td>51.50</td>
      <td>72.0</td>
      <td>84.00</td>
      <td>96.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>32.0</td>
      <td>81.750000</td>
      <td>62.713378</td>
      <td>38.0</td>
      <td>51.75</td>
      <td>72.5</td>
      <td>84.50</td>
      <td>374.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">12</th>
      <th>F</th>
      <td>28.0</td>
      <td>56.571429</td>
      <td>16.455166</td>
      <td>40.0</td>
      <td>48.75</td>
      <td>52.0</td>
      <td>58.00</td>
      <td>106.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>21.0</td>
      <td>63.333333</td>
      <td>19.168551</td>
      <td>20.0</td>
      <td>50.00</td>
      <td>62.0</td>
      <td>72.00</td>
      <td>98.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">13</th>
      <th>F</th>
      <td>14.0</td>
      <td>65.928571</td>
      <td>25.475371</td>
      <td>40.0</td>
      <td>47.00</td>
      <td>56.0</td>
      <td>83.00</td>
      <td>112.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>26.0</td>
      <td>64.615385</td>
      <td>22.627553</td>
      <td>14.0</td>
      <td>46.50</td>
      <td>66.5</td>
      <td>77.50</td>
      <td>104.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">14</th>
      <th>F</th>
      <td>24.0</td>
      <td>69.958333</td>
      <td>18.150288</td>
      <td>40.0</td>
      <td>59.50</td>
      <td>65.5</td>
      <td>88.00</td>
      <td>104.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>20.0</td>
      <td>76.150000</td>
      <td>24.734964</td>
      <td>40.0</td>
      <td>53.50</td>
      <td>82.0</td>
      <td>94.50</td>
      <td>124.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">15</th>
      <th>F</th>
      <td>7.0</td>
      <td>64.285714</td>
      <td>15.074419</td>
      <td>44.0</td>
      <td>52.00</td>
      <td>66.0</td>
      <td>77.00</td>
      <td>82.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>11.0</td>
      <td>66.181818</td>
      <td>23.789990</td>
      <td>40.0</td>
      <td>46.00</td>
      <td>62.0</td>
      <td>84.00</td>
      <td>106.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">16</th>
      <th>F</th>
      <td>7.0</td>
      <td>59.428571</td>
      <td>19.932027</td>
      <td>40.0</td>
      <td>44.50</td>
      <td>56.0</td>
      <td>67.50</td>
      <td>96.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>10.0</td>
      <td>79.700000</td>
      <td>27.491615</td>
      <td>40.0</td>
      <td>70.00</td>
      <td>71.0</td>
      <td>89.50</td>
      <td>143.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">17</th>
      <th>F</th>
      <td>40.0</td>
      <td>75.250000</td>
      <td>37.992408</td>
      <td>38.0</td>
      <td>53.50</td>
      <td>64.0</td>
      <td>76.50</td>
      <td>226.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>37.0</td>
      <td>69.891892</td>
      <td>22.789842</td>
      <td>18.0</td>
      <td>56.00</td>
      <td>68.0</td>
      <td>88.00</td>
      <td>118.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">18</th>
      <th>F</th>
      <td>29.0</td>
      <td>73.827586</td>
      <td>25.509199</td>
      <td>38.0</td>
      <td>52.00</td>
      <td>70.0</td>
      <td>90.00</td>
      <td>152.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>22.0</td>
      <td>66.227273</td>
      <td>22.315768</td>
      <td>20.0</td>
      <td>50.25</td>
      <td>63.0</td>
      <td>83.50</td>
      <td>108.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">19</th>
      <th>F</th>
      <td>5.0</td>
      <td>88.000000</td>
      <td>22.538855</td>
      <td>66.0</td>
      <td>70.00</td>
      <td>86.0</td>
      <td>96.00</td>
      <td>122.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>11.0</td>
      <td>91.000000</td>
      <td>63.297709</td>
      <td>42.0</td>
      <td>57.00</td>
      <td>78.0</td>
      <td>94.00</td>
      <td>272.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">20</th>
      <th>F</th>
      <td>21.0</td>
      <td>81.857143</td>
      <td>35.430616</td>
      <td>38.0</td>
      <td>52.00</td>
      <td>76.0</td>
      <td>110.00</td>
      <td>186.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>25.0</td>
      <td>87.520000</td>
      <td>73.602604</td>
      <td>40.0</td>
      <td>58.00</td>
      <td>66.0</td>
      <td>80.00</td>
      <td>364.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">21</th>
      <th>F</th>
      <td>7.0</td>
      <td>70.285714</td>
      <td>18.741347</td>
      <td>40.0</td>
      <td>63.00</td>
      <td>72.0</td>
      <td>78.00</td>
      <td>98.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>14.0</td>
      <td>74.214286</td>
      <td>20.027591</td>
      <td>42.0</td>
      <td>62.25</td>
      <td>77.0</td>
      <td>88.25</td>
      <td>112.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">22</th>
      <th>F</th>
      <td>22.0</td>
      <td>72.590909</td>
      <td>20.804439</td>
      <td>40.0</td>
      <td>54.25</td>
      <td>77.0</td>
      <td>86.00</td>
      <td>114.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>13.0</td>
      <td>59.769231</td>
      <td>16.300071</td>
      <td>42.0</td>
      <td>50.00</td>
      <td>54.0</td>
      <td>62.00</td>
      <td>96.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">23</th>
      <th>F</th>
      <td>4.0</td>
      <td>68.750000</td>
      <td>22.321514</td>
      <td>50.0</td>
      <td>50.75</td>
      <td>64.5</td>
      <td>82.50</td>
      <td>96.0</td>
    </tr>
    <tr>
      <th>M</th>
      <td>2.0</td>
      <td>222.000000</td>
      <td>240.416306</td>
      <td>52.0</td>
      <td>137.00</td>
      <td>222.0</td>
      <td>307.00</td>
      <td>392.0</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-a7f1551a-8111-40af-9ac9-7234e0ab60b9')"
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
          document.querySelector('#df-a7f1551a-8111-40af-9ac9-7234e0ab60b9 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-a7f1551a-8111-40af-9ac9-7234e0ab60b9');
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
First, we number of patients for each. We can do this in a few ways, but we'll use `groupby` combined with a `count()` method.




```python
# Count the number of patients by illness
patient_counts = patient_df.groupby('illness')['patient_id'].count()
print(patient_counts)
```

    illness
    MVA                        116
    acute asthma                33
    aortic aneurysm             60
    brainstem lesion            23
    cold                        43
    diabetic ketoacidosois      59
    faint                       41
    fall                        59
    heart failure               21
    hyponatraemia               48
    jaundice                    27
    lung transplant             23
    myeloma                     38
    neck dissection             28
    nstemi                      60
    overdose                    40
    pe                          59
    pleural effusion            16
    seizure                     10
    septic                      32
    sob                         58
    stabbing                    35
    stomach pump                37
    subdural haemotoma           4
    urinary tract infection     49
    valve replacement           56
    Name: patient_id, dtype: int64


## Basic Math Functions

The nice thing about data frames is that you can do the math on them quickly, which is fantastic! 

So we can calculate the difference between columns, multiply them etc.


```python
# Multiply all weight values by 2 but does not change the original weight data
patient_df['weight']*2

```




    0        76.0
    1        80.0
    2       148.0
    3         NaN
    4       160.0
            ...  
    1186      NaN
    1187      NaN
    1188    164.0
    1189      NaN
    1190    108.0
    Name: weight, Length: 1191, dtype: float64




```python
patient_df['weight_x_site'] = patient_df['weight']*patient_df['site_id']
patient_df['weight_x_site'] # Now you have it in a new column which is cool!
```




    0        76.0
    1       120.0
    2       148.0
    3         NaN
    4       240.0
            ...  
    1186      NaN
    1187      NaN
    1188    328.0
    1189      NaN
    1190    270.0
    Name: weight_x_site, Length: 1191, dtype: float64


