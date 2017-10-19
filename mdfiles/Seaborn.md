
# Data Visualization With Seaborn

Seaborn is one of the most popular and commonly used libraries for data visualisation.

So, let's kick-off with a quick question.

Do you think it is possible to visualize the relationship between all the variables in the entire data set with just one line of code?

Actually, YES! With the single line of code used below, we can visualize the relationships between all the different variables in the dataset.


```python
sns.pairplot(tips,hue='day',palette="YlGnBu")
```

<img src="../images/seaborn/output_2_1.png" width="600" height="500" />



So, how did it do that?

Well, Seaborn is a high-level Python data visualization library used for making attractive and informative statistical plots. It acts as a wrapper over matplotlib, and it's used in conjunction with NumPy and pandas data structures.

Matplotlib is another data visualization library used when greater control over the graphs are required. However, Seaborn should not be thought as a replacement for matplotlib, rather as a compliment. Even though matplotlib is more powerful, it has a steeper learning curve compared to Seaborn. When using seaborn, it is likely that you will often invoke matplotlib functions directly to draw simpler plots. Another way of putting it is "matplotlib tries to make easy things easier and hard things possible, seaborn attempts to make a well-defined set of hard things easy".

## Steps

<ol>

<li><a href="#importing" style="text-decoration: none;">Importing Libraries</a></li>
<li><a href="#overview" style="text-decoration: none;">Overview of the Data Set</a></li>
<li><a href="#plots" style="text-decoration: none;">Plots</a></li>
    <ol type='A'>
        <li><a href="#distribution" style="text-decoration: none;">Distribution Plot</a></li>
        <ol type='a'>
        <li><a href="#dist" style="text-decoration: none;">Dist Plot</a></li>
       
        </ol>
        <li><a href="#categorical" style="text-decoration: none;">Categorical Plot</a></li>
        <ol type="a">
            <li><a href="#count" style="text-decoration: none;">Count Plot</a></li>
            <li><a href="#box" style="text-decoration: none;">Box Plot</a></li>
            <li><a href="#violin" style="text-decoration: none;">Violin Plot</a></li>
        </ol>
        <li><a href="#matrix" style="text-decoration: none;">Matrix Plot</a><li>
        <ol type='a'>
            <li><a href="#heat" style="text-decoration: none;">Heat Map</a></li>
            <li><a href="#cluster" style="text-decoration: none;">Cluster Map</a></li>
        </ol>
        <li><a href="#regression" style="text-decoration: none;">Regression Plot</a></li>
        <ol type='a'>
            <li><a href="#reg" style="text-decoration: none;">Reg Plot</a></li>
        </ol>
        <li><a href="#axis" style="text-decoration: none;">Axis Grid</a></li>
        <ol type='a'>
            <li><a href="#joint" style="text-decoration: none;">Joint Plot</a></li>
            <li><a href="#pair" style="text-decoration: none;">Pair Plot</a></li>
        </ol>
    </ol>

<li><a href="#next" style="text-decoration: none;">Next Step</a></li>
</ol>

## <a name="importing"></a>Importing Libraries

The data analysis libraries, i.e. `NumPy` and `Pandas` are an integral part of Data Visualisation and are often required for data preprocessing. However, I will not be going into the preprocessing of data in this blog. 


```python
import numpy as np
import pandas as pd
```


```python
import seaborn as sns
```

Now, we use the command below to view all Seaborn plots within `Jupyter Notebook`.


```python
%matplotlib inline
```

## <a name="overview"></a>Overview of the Dataset

Now that we have imported the required libraries, I will be using the famous `Iris dataset` for this blog. If you are interested, all the other in-built Seaborn datasets are listed <a href = "https://github.com/mwaskom/seaborn-data" style="text-decoration: none;">**here**</a>.


```python
iris = sns.load_dataset('iris')
```

So, here is a quick view of the Iris dataset!


```python
iris.head(3)
```




<div id="table">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sepal_length</th>
      <th>sepal_width</th>
      <th>petal_length</th>
      <th>petal_width</th>
      <th>species</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
  </tbody>
</table>
</div>


<img src="../images/seaborn/iris-machinelearning.png" width="650" height="250" />

**Image:-** Different species of Iris Plant

Given below is a brief description of all the variables:

1. <p>`sepal_length`-> Sepal length in cm </p>
2. <p>`sepal_width` -> Sepal width in cm <p>
3. <p>`petal_length` -> Petal length in cm <p>
4. <p>`petal_width` -> Petal width in cm <p>
5. <p>`species` ->  Class of the Iris Plant<p>
    <p>* *Iris Setosa*</p>
    <p>* *Iris Versicolour*</p>
    <p>* *Iris Virginica*</p>
    
To know more about the Iris Dataset, you can refer <a href = "http://archive.ics.uci.edu/ml/datasets/Iris" style="text-decoration: none;">UC Irvine Machine Learning Repository. </a>

# <a name="plots"></a>Plots

## <a name="distribution"></a>Distribution Plot

### <a name="dist"></a>Dist Plot

Dist Plot, also known as Histogram is used to plot a univariate distribution of observation. It also displays a KDE(Kernal Density Estimation) plot over the histogram.

In the plot below, we are plotting a histogram of the `petal_width`.


```python
sns.distplot(a=iris['petal_width'], bins=40, color='m')
```


![png](../images/seaborn/output_24_1.png)
<img src="../images/seaborn/iris-machinelearning.png" width="650" height="250" />

## <a name="categorical" ></a>Categorical Plots

### <a name="count"></a>Count Plot

Count Plot displays the number of observations for a categorical variable using bars.

In the plot below, we are counting the number of observations of each `species` of Iris Plant, and we can see that each species has 50 samples in the dataset.


```python
sns.countplot(x='species',data=iris, palette="OrRd")
```

![png](../images/seaborn/output_28_1.png)
<img src="../images/seaborn/iris-machinelearning.png" width="650" height="250" />

### <a name="box"></a>Box Plot

A box plot shows the distribution of quantitative data across a categorical variable.

In the plot below, the quantitative data that we have used is the `sepal_width`, and we are comparing it to the categorical variable `species`.

```python
sns.boxplot(x='species',y='sepal_width',data=iris ,palette='YlGnBu')
```


![png](../images/seaborn/output_31_1.png)
<img src="../images/seaborn/iris-machinelearning.png" width="650" height="250" />

### <a name="violin"></a>Violin Plot

A violin plot is a variation of box plot. It shows the distribution of quantitative data across several levels of categorical variables. The violin plot also features a kde of the underlying distribution.

In the plot below, the `petal_length` is compared against `species`.


```python
sns.violinplot(x='species', y='petal_length', data=iris, palette='YlGnBu')
```

![png](../images/seaborn/output_34_1.png)
<img src="../images/seaborn/iris-machinelearning.png" width="650" height="250" />

## <a name="matrix"></a>Matrix Plots

### <a name="heat"></a>Heat Maps

A Heat Map is a graphical representation of the correlation between all the numerical variables in a dataset. The input provided is a correlation matrix generated using pandas.


```python
sns.heatmap(iris.corr(),cmap="YlGnBu", linecolor='white', linewidths=1)
```


<img src="../images/seaborn/output_38_1.png" width="500" height="400" />

### <a name="cluster"></a>Cluster Map

Cluster Map is a plot of matrix dataset as a hierarchically clustered heatmap.

**Note** Cluster map can only take in quantitative variables.


```python
g = sns.clustermap(iris, cmap="magma")
```


<img src="../images/seaborn/output_41_0.png" width="650" height="600" />

## <a name="regression"></a>Regression Plots

### <a name="reg"></a>Reg Plot

Regression Plot is used to map all the given data and plot a linear regression model fit for it.

In the example below, we have plotted the `petal_width` against the `petal_length`.


```python
sns.regplot(x='petal_width', y='petal_length', data=iris)
```

<img src="../images/seaborn/output_45_1.png" width="650" height="450" />

## <a name="axis"></a>Axis Grids

Axis Grids are graphs that combine various plots using FacetGrid to realize complex visualizations.

### <a name="lm"></a>LM Plots

LM plots are intended as a convenient interface to fit regression models (regression line) across conditional subsets of a dataset. It is a variation of regplot which uses FacetGrid to plot multiple subsets of data and plot the regression line for each of them.

In the example below, we have plotted sepal_width vs. sepal_length. The data set is divided into three subsets based on their species, and regression lines are mapped for each of them.


```python
sns.lmplot(x = 'sepal_width', y = 'sepal_length', data = iris, col = 'species', hue = 'species', palette = 'YlGnBu')
```


<img src="../images/seaborn/output_65_1.png" width="630" height="200" />


### <a name="joint"></a>Joint Plot

A joint plot is used to draw a plot of two variables with bivariate and univariate graphs.

In the example below, the kdeplots (univariate graphs) at the top and right are kde's of `sepal_width` and `petal_length` respectively, and the central graph (bivariate graph) plots the relationship between the two variables.


```python
sns.jointplot(x="sepal_width", y="petal_length", data=iris, kind="kde", color="m")
```

<img src="../images/seaborn/output_53_2.png" width="550" height="550" />

### <a name="pair"></a>Pair Plot

Pair Plot is used to view the pairwise relationship between all the variables in a dataset and the diagonal axes show the univariate distribution of the variable.

The example takes the entire dataset as input and distinguishes data on `species` with varying colors.


```python
sns.pairplot(iris, hue='species', palette="OrRd")
```

<img src="../images/seaborn/output_56_1.png" width="600" height="550" />

## <a name="next"></a>What Next?

Now that you are comfortable with the basics of Seaborn you can learn more about data visualization at <a href = "https://seaborn.pydata.org/api.html" style="text-decoration: none;">**seaborn.pydata.org**</a>.

## </a>References
<ol>
<li> <p>https://seaborn.pydata.org/index.html</p></li>

<li> <p>https://www.slideshare.net/Centerline_Digital/the-importance-of-data-visualization</p></li> 
<li> <p>https://tryolabs.com/blog/2017/03/16/pandas-seaborn-a-guide-to-handle-visualize-data-elegantly/</p></li> 
<li> <p>https://www.datacamp.com/community/tutorials/machine-learning-in-r#one </p></li> 
</ol>