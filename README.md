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
```

```from __future__ import print_function # this line adds compatibility to python 2```

Let us download and import our primary Canadian Immigration dataset using *pandas* ```read_excel()``` method. But before we can do that, we need to download a module on which *pandas* requires to read in excel files. This module is **xlrd**.
