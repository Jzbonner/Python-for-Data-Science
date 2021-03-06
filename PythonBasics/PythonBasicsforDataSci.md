# Python 3 
Python is a first-class tool mainly because of its libraries for storing, manipulating, and gaining insight from data. 


## Introductory Information on Python: List, Dictionaries & Booleans 
Personal notes were taking down in physical format regarding these basic concepts behind the Python language. I have included a few useful links in regards to what will aid those in understanding the basic principles of Python, specifically data types, functions and methods and dev environments: 
* Python Basic: https://community.modeanalytics.com/python/tutorial/python-basics/
* Python Methods and Functions: https://community.modeanalytics.com/python/tutorial/python-methods-functions-and-libraries/

## Interactive Python
IPython stands for Interactive Python and can be used to run scripts (either directly in the IPython Shell or via .py files). A great resource for those that are completely new to Python can be found at [python for beginners](http://www.pythonforbeginners.com/basics/), where you can learn about how to install Python package manager, web application frameworks, debuggers, etc. You also learn about the general basics behind Python Syntax, Variables, Comments, DocStrings, Booleans, Operators, Exception Handling, List, Strings, Dictionaries, Loops, Functions, Conditional Statements, Writing Files, and Language Rules. 

> The majority of my work in python will be done using the open source web application [Jupyter Notebook](http://jupyter.org/). I would recommend everyone to utilize this platform, either as an independent resource or through the Anaconda3 distribution. 

## Python: Pandas, Data Frames and Selecting Data 
The following information is summarized from the [Mode Analytics Community Reference Material](https://community.modeanalytics.com/python/tutorial/pandas-dataframe/). This information covered from this site will utilize the Pandas python library extensively (or at least enough to give a surface level efficiency with data frames and their uses). 

Pandas has two unique data structures: Data Frames and Series. A _data frame_ is a a table with multiple columns and a column of that data frame, or a list like object, is known as a _series_. A data frame is a table much like that in SQL or Excel and can be manipulated through specific operation; such as aggregation, filtering and pivoting. Data frames can operate very quickly while maintaining their mutability thanks to Python. 
* Data frames can load data through a number of different data structures and files. 
    * Including list and dictionaries, csv files, excel files and database records 

## Dataframes in Python with Examples 
The `datasets` object is a list where each item is a dataframe corresponding to one of the SQL queries in the Mode report (examples in subsequent sections will reference csv files as the sudo SQL database however [Mode](https://modeanalytics.com/tutorial/reports/326495548afb/python) utilizes an predefined SQL query to bring in data to their interactive python notebook). So `datasets[0]` is a dataframe object within the `datasets` list. Python allows you to give libraries aliases, so that you can reference them quickly in your code. The pandas library in python is typically aliased as `pd`. 

```python 
import pandas as pd 
```

SQL refers to missing values as `null`, by using the method `fillna()` you can replace missing values with empty strings in `datasets`. 

Example Utilization of Pandas and Datasets in Python: Analyzing web traffic data from a nonprofit website [Watsi](http://watsi.org/) by utilization of a predefined SQL query for historic data from the site. 

Row in Dataset | Description 
--- | ---
`referrer` | The url that referred the user to the site (if available). For example, if someone arrived at the page through a Facebook link, referrer would be https://www.facebook.com 
`timestamp` |  The time the event occurred
`title` | The title of the page the user visited on the Watsi website
`url` | The url the user visited. For example, https://watsi.org/team/the-meteor-chef
`user_agent` | The software the user used to accessed the site, including platform, browser, and extensions
`user_id` | A unique id for each user (normally they’d be numbers—we’ve turned them into anonymous names instead)
`referrer_domain` | The domain of the url that referred the user to the site. For example, “facebook.com”
`website_section` | The section of the website visited. For example, the section of https://watsi.org/team/the-meteor-chef is “team”
`platform` |  The device platform the user visited from. Possible values are "Desktop" and "Mobile"

Brackets are utilized to select a value in a list or dictionary, and similarly you can use brackets to select a column in the DataFrame. For Example: 

```python 
input ~ 
data['url]

output ~ 
0                        https://watsi.org/
1    https://watsi.org/team/the-meteor-chef
2              https://watsi.org/gift-cards
3                        https://watsi.org/
4                        https://watsi.org/
Name: url, dtype: object
```

You can select rows by using brackets and row indexes. By using :notation between brackets you can select specific values according to their indexes. For example `data[:3]` wil provide you with the values up to index 3, `data[4:7]` will provide you with the values from index 4 up to - but not including - index 7, and `data[4997:]` will provide you with everything from index 4997 onwards. In order to select rows you have to use the `data.ix[]` method on your datasets. 

Selecting series from your datasets can be done individually or simultaneously. Meaning that you can select rows and columns separately or together. For our above example you may utilize something like `data['title'][:3]` to select the first three rows of the `title` column or `data['referrer'][10:15]` to select the indexes from 10 to 15 of the `referrer` column. Selecting multiple series can be done with the following syntax `data[['referrer', 'title']]`

## Counting Values and Basic Plotting in Python 
* Refer to Files on Jupyter Notebook for visual representations of the subsequent concepts. 
* SideNote: VSCode does have an extension for previewing Jupyter Notebook files in your editor [VSCode Jupyter Notebook Previewer](https://marketplace.visualstudio.com/items?itemName=jithurjacob.nbpreviewer)

For this section and future sections, we will be working with a CSV file containing information on the FDIC Failed Bank List, entitled _Finance.csv_. 

> Federal Deposit Insurance Corporation — The FDIC is often appointed as receiver for failed banks. This list includes banks which have failed since October 1, 2000.

By utilizing some of the previous concepts discussed above, we will set up python environment that loads locally stored csv information and presents the first few rows of the csv in a `dataframe`. All sample csv data is being taken from [Data.gov](https://catalog.data.gov/dataset). Priming your csv file in Jupyter Notebook should begin as follows: 

```python 
import pandas as pd

data = pd.read_csv('Finance.csv')
data.fillna('')

data.head(n=8)
```
A result of the above operation can be seen in the Jupyter Notebook file entitled _Python, DataFrames, and Libraries Workbook.ipynb_. The line `data.head(n=8)` will provide you with a general visualization of how the raw data in the CSV file has been translated into a dataset. From here we will use this format to find the 20 most popular (read frequency of) failed bank names from the raw data and visually plot the results in a bar chart. 

To achieve the above goals we will have to import a very important library as well as a script to display our plotted data inline. 

> Matplotlib is a 2d Python plotting library which produces publication quality figures in a variety of hardcopy formats and interactive environments across platforms. 

A simple aggregate function that you can use to achieve our desired outcome above is the `.value_counts()` method. This will allow you to pull frequency data for a specified value from the dataset.  Keeping in mind the use of bracket notation for placing parameter constraints on your index, we can easily achieve a raw list of of the most popular (i.e. frequent) failed bank names from our dataset: 

```python 
"""
used to find the 20 most popular failed bank names out of the dataset
"""

import pandas as pd

data = pd.read_csv('Finance.csv')
data.fillna('')

data['Bank Name'].value_counts()[:21]
```

We are using the `Bank Name` column from our dataset and picking the pertinent information from that series to begin this process. From here we need to utilize the Matplotlib library to plot this data into a bar chart. Luckily, this is done by the use of one method, `.plot()`. You can then specify the particular plotting visual you would like to use based on the data; for this example it will be the bar chart, or `.plot(kind='barh')`. Be mindful of your import dependencies and also take note of the implementation format for customizing our plotted data: 

```python 
"""
used to find the 20 most popular failed bank names out of the dataset and 
plot them in a visual bar chart.
"""

import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline

data = pd.read_csv('Finance.csv')
data.fillna('')

data['Bank Name'].value_counts()[:21].plot(kind='barh')

# Customization to plot visual for readability 
plt.xticks(fontsize=14, fontweight='bold')
plt.yticks(fontsize=9)
plt.xlabel('Frequency')
plt.ylabel('Bank Names')
plt.title('Frequency of Failed Bank Names')
```
* For additional information on the Matplotlib library please refer to this [documentation](https://matplotlib.org/contents.html)

## Filtering Data in Python with Boolean Indexes 
Segmentation in coding is the division into separate parts or sections. Filtering data in python can be done via the help of Boolean indexes. A `boolean index` is a series composed of `TRUE` or `FALSE` values that correspond to rows in the dataset. This type of indexing could be useful in identifying trends and movement within a data set. Looking at our `Finance.csv` data we could be interested in determining the city with the highest number of failed banks specifically in Georgia. To do this we would need to create a `boolean index` that filters all the Bank Names that are linked to GA and place those results into an a new dataset that could then be mutated further to observe city frequency. 

```python 
import pandas as pd 
import matplotlib.pyplot as plt 
%matplotlib inline 

data = pd.read_csv('Finance.csv')
data.fillna('')

# Here we have to take our boolean index operation and transmute it into a dataset so that it can be further analyzed by methods in the pandas library

statefilter_Index = (data['ST'] == 'GA')
state_Index = data[statefilter_Index]
state_Index['City'].value_counts()[:20]
```

The above code shows you how to do just that and return a list of the top 20 most frequent cities with failed banks. Creating new datasets from our original parsed csv file, allows us to utilize a boolean index to filter our data and then prime that specific dataset to see a list of the top 20 most frequent cities with failed banks. From there we can use the matplotlib python library to create a visualization: 

```python 
import pandas as pd 
import matplotlib.pyplot as plt 
%matplotlib inline 

data = pd.read_csv('Finance.csv')
data.fillna('')

statefilter_Index = (data['ST'] == 'GA')
state_Index = data[statefilter_Index]
state_Index['City'].value_counts()[:10].plot(kind='bar')

# plot visual customization 
plt.xlabel('Cities')
plt.ylabel('Number of Banks')
plt.title('Frequency of Failed Banks by City in Georgia')
```

You don't have to specify an index search based off of `Series` titles. Developers can also use `boolean indexes` with strings by utilizing the `.str.contains()` method. For instance if you wanted to find a list of Bank Names that contain the string "First", then you would accomplish using the `.str.contains()` method as follows: 

```python 
import pandas as pd 

data = pd.read_csv('Finance.csv')
data.fillna('')

bn_filter_index = data['Bank Name'].str.contains('First')
bn_index = data[bn_filter_index]
bn_index
```
Utilizing the above setup we can then use the `.tolist()` method to generate a list of the CERT numbers for all failed banks that contain the string "First" in their Bank Name. 

```python 
import pandas as pd 

data = pd.read_csv('Finance.csv')
data.fillna('')

bn_filter_index = data['Bank Name'].str.contains('First')
bn_index = data[bn_filter_index]
bn_index['CERT'].tolist()
```

## Deriving New Columns and Defining Python Functions 
Creating a new column in a dataset is like creating a new key-value pair in a dictionary. By assigning values to the new column name you add a column to the DataFrame. For instance adding a new column to your data set may look something like this: 

```python 
import pandas as pd 

data = pd.read_csv('Finance.csv')
data.fillna('')

data['new'] = 'new data'
data[:3]
```

Lets say you wanted to run a function through the dataset to determine whether or not the failed bank was located in the north east or the south west for the first 200 data entries. To do this you would need to define a function that checks each row for values that match those present in the function. We would need to first define the specific function and its return values and then `.apply()` it to our dataframe as a whole. Your resulting code with functionality for plotting using the Matplotlib library should be as follows: 

```python 
import pandas as pd 
import matplotlib.pyplot as plt 
%matplotlib inline 

data = pd.read_csv('Finance.csv')
data.fillna('')

north_east = ['PA', 'MD', 'DE', 'NJ', 'RI', 'CT', 'MA', 'NH', 'ME', 'VT', 'NY']
south_west = ['AZ', 'NM', 'NV', 'UT']

def is_in_region(state): 
    if state in north_east: 
        return 'Northeast'
    elif state in south_west: 
        return 'Southwest'
    else: 
        return 'Other Regions'
        
data['ST'][:200].apply(is_in_region)    

# importing the derived data into a new column
data['region'] = data['ST'].apply(is_in_region)

# To ensure that you accurately selected multiple columns of your data frame. 
data[['ST', 'region']][0:10]

# plotting an analysis of the information in a bar graph 
data['region'][:200].value_counts().plot(kind='bar', figsize=(10,8))

plt.title('Frequency of Failed Banks in the NE and SW compared to Other Regions')
plt.ylabel('Frequency')
plt.xlabel('Regions')
```

Further analysis can be made to determine the correlation between frequency of failed banks in the north east, the south west and the other regions in the United States. We will cover some of those details in later sections but hopefully this gives you insight on how to manipulate column data in a data frame, how to define functions and how to apply them to data frames. 

## Pandas .groupby(), Lambada Functions and Pivot Tables wih NumPy 
~ Refer to Jupyter Notebooks for in depth examples. 



