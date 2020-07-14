![cognitiveclass](https://user-images.githubusercontent.com/53174566/87385938-fa2d0780-c5bc-11ea-8455-9fff96fa4e64.png "CognitiveClass") 

## Pie Charts, Box Plots, Scatter Plots, and Bubble Plots 

### Introduction

In this lab session, we continue exploring the Matplotlib library. More specificatlly, we will learn how to create pie charts, box plots, scatter plots, and bubble charts.

### Table of Contents

<div>
  
1. Exploring Datasets with *pandas* <br>
2. Downloading and Prepping Data <br>
3. Visualizing Data using Matplotlib <br>
4. Pie Charts <br>
5. Box Plots <br>
6. Scatter Plots <br>
7. Bubble Plots <br> 
</div>
<hr>

### Exploring Datasets with pandas and Matplotlib

Toolkits: The course heavily relies on [*pandas*](http://pandas.pydata.org/) and [**Numpy**](http://www.numpy.org/) for data wrangling, analysis, and visualization. The primary plotting library that we are exploring in the course is [Matplotlib](http://matplotlib.org/).

Dataset: Immigration to Canada from 1980 to 2013 - [International migration flows to and from selected countries - The 2015 revision](http://www.un.org/en/development/desa/population/migration/data/empirical2/migrationflows.shtml) from United Nation's website.

The dataset contains annual data on the flows of international migrants as recorded by the countries of destination. The data presents both inflows and outflows according to the place of birth, citizenship or place of previous / next residence both for foreigners and nationals. For this lesson, we will focus on the Canadian Immigration data.

### Downloading and Prepping Data

Import Primary Modules. The first thing we'll do is import two key data analysis modules: *pandas* and **Numpy**.

```python
import numpy as np  # useful for many scientific computing in Python
import pandas as pd # primary data structure library


from __future__ import print_function # this line adds compatibility to python 2
```

Let us download and import our primary Canadian Immigration dataset using *pandas* ```read_excel()``` method. But before we can do that, we need to download a module on which *pandas* requires to read in excel files. This module is **xlrd**.


```python
!conda install -c anaconda xlrd --yes
```

Download the dataset and read it into a *pandas* dataframe.

```python
df_can = pd.read_excel('https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/DV0101EN/labs/Data_Files/Canada.xlsx',
                       sheet_name='Canada by Citizenship',
                       skiprows=range(20),
                       skipfooter=2
                      )

print('Data downloaded and read into a dataframe!')
```

Let's take a look at the first five items in our dataset.


```python
df_can.head()
```

Let's find out how many entries there are in our dataset.


```python
# print the dimensions of the dataframe
print(df_can.shape)
```

Clean up data. We will make some modifications to the original dataset to make it easier to create our visualizations. Refer to `Introduction to Matplotlib and Line Plots` lab for the rational and detailed description of the changes.

```python
# Clean up the data set to remove unnecessary columns (eg. REG) 
df_can.drop(['AREA', 'REG', 'DEV', 'Type', 'Coverage'], axis=1, inplace=True)

# Let us rename the columns so that they make sense
df_can.rename(columns={'OdName':'Country', 'AreaName':'Continent','RegName':'Region'}, inplace=True)

# For sake of consistency, let us also make all column labels of type string
df_can.columns = list(map(str, df_can.columns))

# set the country name as index - useful for quickly looking up countries using .loc method
df_can.set_index('Country', inplace=True)

# Add total column
df_can['Total'] = df_can.sum(axis=1)

# years that we will be using in this lesson - useful for plotting later on
years = list(map(str, range(1980, 2014)))
print('data dimensions:', df_can.shape)
```

### Visualizing Data using Matplotlib

Import `Matplotlib`

```python
# use the inline backend to generate the plots within the browser
%matplotlib inline 

import matplotlib as mpl
import matplotlib.pyplot as plt

mpl.style.use('ggplot') # optional: for ggplot-like style

# check for latest version of Matplotlib
print ('Matplotlib version: ', mpl.__version__) # >= 2.0.0
```


