

# The Pandas Library

> Pandas is a python library built on top of Numpy.

> While Numpy is best suited for working with arrays based numerical data, Pandas is designed for working with tabular data. It allows us to perform powerful tabular data based operations similar to those used in spreadsheet programs like excel.

### 1. Pandas Objects

> There are two fundamental Datatypes in pandas, they are:

> 1. **Series**: A Series is a one dimensional array containing a sequence of homogeneous(same) values. The Series object is similar to a one dimensional array. A pandas series can be created from a homogeneous list or an array as shown below:

   - ```python
     import numpy as np
     import pandas as pd
     
     a = np.random.randint(1, 100, 5)
     s = pd.Series (a)
     s
     ```

   > - **Note**: As can be seen from the output of the code, the Series object explicitly shows an index on the left and the values on the right.

> 2. **Dataframe**: The DataFrame basically represents a rectangular table of data, which contains an ordered collection of homogeneous(same) columns. Though the elements within a single column have to be homogeneous, each column can independently have its own different data type. The DataFrame objects have two indexes, one to represent the rows within the rectangular table of data and one for the columns.

   > - Consider the example given below, it expresses the age, weight and height features of a set of individuals.

   - ```py
     d1 = dict(sam = [60, 52, 5.91, # Dictionary of Heights
     jill = [55, 46, 5.4],
     kate = [19, 60, 5.8],
     jack = [36, 89, 6.3])
     ```

   - ```
     df = pd.DataFrame(d1)
     df
     ```

     

## 2. Reading & Writing Tabular Data Using Pandas

> The pandas library contains a number of inbuilt functions for reading various formats of tabular data as a DataFrame object.

```py
pd.read_csv # Load csv (comma separated values) file as DataFrame
pd.read_table # Load tsv (tab separated values) file as DataFrame
pd.read_excel # Load Excel file as DataFrame
pd.read_html # Load table found in html file as DataFrame
```

> **Note**: For most of the purposes in this course we shall be using the csv files format. The csv file format is basically a text file containing tabular data as “comma separated values” as shown below. Csv files have the ’.csv’ file extension that distinguishes it from other files.

```py
name = "sample table.csv" # this is an example only

df = pd.read_csv (name, index_col = 0) 
df
```



## 3. Basic Pandas For Data Exploration

> For the sake of demonstrating DataFrame operations, we shall be using the “**automobiles dataset**”, which is available as a csv file. This dataset was created in the mid 1980s and it describes various features of the cars available at that time (ex: manufacturer, car type, fuel type, number of cylinders, etc) along with their prices.

**Dataset Link** : [Automobile_data](https://github.com/AbhiNavneet/notes_draft/blob/main/Data_Processing/Automobile_data.csv)

### 3.1 Importing Numpy & Pandas Library

```py
import numpy as np
import pandas as pd
```
> We first load the data into a DataFrame using the read csv function and assign it to the variable name df cars as shown below.

```py
df_cars = pd.read_csv('cars.csv') # Loading Dataset from file
```

```py
df_cars.shape # Displaying row x column from dataset
```

```py
df_ cars.columns # Displaying Column names
```



### 3.2 The Head, Tail Method

> We can “peek” at the DataFrame’s content using the head, tail methods as shown below. The head and tail methods return the first n and last n rows of the dataset respectively.

```py
df_ cars.head(10)
```

```py
df_cars.tail(10)
```



### 3.3 The Info Method:

> The info method demonstrated below, gives us information of the data types and the number of non null values present in each column.

```py
df cars.info()
```



### 3.4 The Describe Method:

> The describe methods gives us a statistical summary of all the columns of the DataFrame that contain numerical values. The statistics returned by this method include the **count, mean, standard deviation, minimum, maximum, 25th, 50th and 75th percentiles values numeric column**. This is demonstrated in the code shown below.

```python
df_cars.describe()
```



### 3.5 The Unique Method:

> The number of unique values within any column of a DataFrame can be obtained by using the ”unique” method on its columns. This is demonstrated in the code shown below.

```py
df_cars.n_cyl.unique()
```

```py
df_cars.make.unique()
```



### 3.6 The value counts Method:

> Returns the count of values contained in a DataFrame column, as shown below:

```py
df_cars.make.value_counts()
```

```py
df_cars.n_cyl.value_counts()
```



### 3.7 The plot Method:

> The Pandas plot method returns visualizations/plots of the values. This helps the user to get a more visual/intuitive understanding of the data contained within DataFrames. 

> **Note**: The plot method takes in a keyword argument **kind**, which determines the kind of plot that will be returned. Pandas uses the **Matplotlib** library to create these plots. 

```py
df_cars.make.value counts().plot(kind = 'bar') # bar plot
```

> As seen in the output bar plot, this gives us a clear visual representation of the number of cars belonging to the various automobile manufactures used in the data set. If one prefers a horizontal version of the same bar plot, the barh keyword argument should be used instead of bar.

> Shown below are some more examples of plot methods in Pandas:

#### 3.7.1 Histogram

```py
df_cars.price.plot(kind = 'hist')
```

> From the histogram shown above, we understand that most of the cars lie within the price range of 500 to 15000.

#### 3.7.2 Scatter Plot

```py
df_cars.plot(x = 'city_mpg', y = 'price', kind = 'scatter')
```

> Scatter plots are used when one wants to understand the relationship between values in two chosen columns of the DataFrame. In the plot above we see that most of the vehicles have a mileage less than 35 and have their prices below 20000.

### 3.8 The Drop Method:

> The Drop method removes rows or columns from a DataFrame by specifying label names and corresponding axis of the rows/columns to be dropped as shown below.

```py
df_cars.drop(['drive', 'peak_rpm'], axis = 1).head()
```

> In the code shown above, we drop columns labelled “**drive**” and “**peak rpm**” . Note that we specify the axis keyword argument as one, to drop columns. The default value for axis is set to zero and hence the drop method by default drops rows. 

### 3.9 The sort values Method:

> The sort values method allows one to sort a DataFrame based on the values of any one of its numerical columns. Shown in the code below, we sort the dataset based on the “**price**” column.

```py
df_cars.sort_values('price', ascending = False).head()
```

### 3.10 The groupby Method:

> The Groupby method is used for aggregating the numerical columns of a DataFrame with respect to some other column containing categorical values. 

> Consider the Data Frame df cars, the first six of its columns contain categorical values and the rest are numerical in nature. Suppose one wants to do a mean aggregate on the numerical values of the DataFrame with respect to the “drive” column, this can be done as shown below.

```py
df_drive = df_cars.groupby('drive').mean()
df drive
```

> Thus from the Output of DataFrame df_drive returned above, we know the mean values for each of the numerical columns with respect to the number of cylinders of a vehicle. Thus the average number of cylinders, hp, peak rpm, miles per gallon and price for rear wheel drive cars are 4.8, 133.69, 5071.71, 23.13 and 14070.17 respectively.

## 3.11 Handling Missing Data (None, nan & NaN):

> Real world data is rarely clean and organized, and it is quite common for them to have values missing. The ability to be able to work with missing values is therefore quite important. Pandas makes use of special data handling protocols that makes working with missing data as easy as possible.

> Missing values are referred to as NA values (not available). Pandas relies on Numpy’s Internal representation of NA values while handling missing data. Numpy represents NA values using an abstract float value called nan which is basically an acronym for “Not A Number”.

### 3.12 ISNA, DROPNA & FILLNA Methods:

> **Isna, notna, dropna and fillna** are Pandas methods pandas used for handling missing values. The isna and notna methods are used for detecting missing values as shown below. To find out which columns contain missing values we can apply the sum method across the axis = 0 as shown below (this works because True == 1 and False == 0).

```py
null_cols = df_cars.isna().sum()
null cols
```

> The **fillna method** is used to fill missing values in  DataFrames with values of our choice. This is demonstrated for Series objects in the code shown below.

```py
df.fillna(0)
```

