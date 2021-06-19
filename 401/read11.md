# What is Jupyter Lab

## Overview
JupyterLab is a next-generation web-based user interface for Project Jupyter.

JupyterLab enables you to work with documents and activities such as Jupyter notebooks, text editors, terminals, and custom components in a flexible, integrated, and extensible manner

You can arrange multiple documents and activities side by side in the work area using tabs and splitters.

for example:
Code Consoles provide transient scratchpads for running code interactively, with full support for rich output. A code console can be linked to a notebook kernel as a computation log from the notebook, for example.

Kernel-backed documents enable code in any text file (Markdown, Python, R, LaTeX, etc.) to be run interactively in any Jupyter kernel.
Notebook cell outputs can be mirrored into their own tab, side by side with the notebook, enabling simple dashboards with interactive controls backed by a kernel.

Multiple views of documents with different editors or viewers enable live editing of documents reflected in other viewers. For example, it is easy to have live preview of Markdown, Delimiter-separated Values, or Vega/Vega-Lite documents.
 
JupyterLab also offers a unified model for viewing and handling data formats. JupyterLab understands many file formats (images, CSV, JSON, Markdown, PDF, Vega, Vega-Lite, etc.)


# NumPy Tutorial: Data Analysis with Python
data analysis package , using NumPy, you can speed up your workflow, and interface with other packages in the Python ecosystem.

Here are the first few rows of the winequality-red.csv file, which we’ll be using throughout this tutorial:
```
"fixed acidity";"volatile acidity";"citric acid";"residual sugar";"chlorides";"free sulfur dioxide";"total sulfur dioxide";"density";"pH";"sulphates";"alcohol";"quality"
7.4;0.7;0;1.9;0.076;11;34;0.9978;3.51;0.56;9.4;5
7.8;0.88;0;2.6;0.098;25;67;0.9968;3.2;0.68;9.8;5

```
The data is in what I’m going to call ssv (semicolon separated values) format — each record is separated by a semicolon (;), and rows are separated by a new line. There are 1600 rows in the file, including a header row, and 12 columns.

### Lists Of Lists for CSV Data

We can read in the file using the csv.reader object, which will allow us to read in and split up all the content from the ssv file.

In the below code, we:

```
import csv
with open('winequality-red.csv', 'r') as f:
    wines = list(csv.reader(f, delimiter=';'))
```

Import the csv library.
Open the winequality-red.csv file.
With the file open, create a new csv.reader object.; Pass in the keyword argument delimiter=";" to make sure that the records are split up on the semicolon character instead of the default comma character.
Call the list type to get all the rows from the file.
Assign the result to wines.
 
```
print(wines[:3])
```
print out the first 3 rows:
output 
```
[['fixed acidity', 'volatile acidity', 'citric acid', 'residual sugar', 'chlorides', 'free sulfur dioxide', 'total sulfur dioxide', 'density', 'pH', 'sulphates', 'alcohol', 'quality'], ['7.4', '0.7', '0', '1.9', '0.076', '11', '34', '0.9978', '3.51', '0.56', '9.4', '5'], ['7.8', '0.88', '0', '2.6', '0.098', '25', '67', '0.9968', '3.2', '0.68', '9.8', '5']]

```

```
qualities =
[float(item[-1]) for item in wines[1:]]
sum(qualities) / len(qualities) # 5.6360225140712945

```
what the previous code do ?

Extract the last element from each row after the header row.

Convert each extracted element to a float.
Assign all the extracted elements to the list qualities.

Divide the sum of all the elements in qualities by the total number of elements in qualities to the get the mean.

### Numpy 2-Dimensional Arrays
we can get element by specific row and column

In a NumPy array, the number of dimensions is called the rank, and each dimension is called an axis. So the rows are the first axis, and the columns are the second axis.

### Creating A NumPy Array
using the numpy.array function
> we’ll leave off the header row, which contains strings
> limitations of NumPy is that all the elements in an array have to be of the same type

In the below code, we:

Import the numpy package.
Pass the list of lists wines into the array function, which converts it into a NumPy array.
1. Exclude the header row with list slicing.
2. Specify the keyword argument dtype to make sure each element is converted to a float. We’ll dive more into what the dtype is later on.

```
import csv
with open("winequality-red.csv", 'r') as f:
    wines = list(csv.reader(f, delimiter=";"))
import numpy as np
wines = np.array(wines[1:], dtype=np.float)
```

```
array([[ 7.4 , 0.7 , 0. , ..., 0.56 , 9.4 , 5. ],
[ 7.8 , 0.88 , 0. , ..., 0.68 , 9.8 , 5. ],
[ 7.8 , 0.76 , 0.04 , ..., 0.65 , 9.8 , 5. ],
...,
[ 6.3 , 0.51 , 0.13 , ..., 0.75 , 11. , 6. ],
[ 5.9 , 0.645, 0.12 , ..., 0.71 , 10.2 , 5. ],
[ 6. , 0.31 , 0.47 , ..., 0.66 , 11. , 6. ]])
```
We can check the number of rows and columns in our data using the shape property of NumPy arrays:  
wines.shape
(1599, 12)

### Alternative NumPy Array Creation Methods

 will create an array with 3 rows and 4 columns, where every element is 0, using numpy.zeros:

` import numpy as np `
```
empty_array = np.zeros((3,4))

empty_array ```

array with rancdom nubmer :
` np.random.rand(3,4) `

### Using NumPy To Read In Files
use  numpy.genfromtxt function. to  read csv or other files into arrays.
```
In the below code, we:

Use the genfromtxt function to read in the winequality-red.csv file.
Specify the keyword argument delimiter=";" so that the fields are parsed properly.
Specify the keyword argument skip_header=1 so that the header row is skipped.
```
wines = np.genfromtxt("winequality-red.csv", delimiter=";", skip_header=1)
```
### Indexing NumPy Arrays
use array indexing to select individual elements, groups of elements, or entire rows and columns.
![img 11 ](/images/read11.PNG)

` wines[2,3] `

### Slicing NumPy Arrays
using a colon (:) A colon indicates that we want to select all the elements from the starting index up to but not including the ending index. This is also known as a slice:
```
wines[0:3,3]
```
```
array([ 1.9, 2.6, 2.3])
```
extract an entire row:
wines[3,:]

select the entire array using two colons 
wines[:,:]

### Assigning Values To NumPy Arrays
assigning directly to the indexed value:
`wines[1,5] = 10` 

### 1-Dimensional NumPy Arrays
NumPy is a package for working with multidimensional arrays

``` array([ 0.88588862, 0.85693478, 0.19496774])
```
 we passed in a shape for a single dimensional array , The shape specifies the number of dimensions, and the size of the array in each dimension. A shape of (10,10) will be a 2-dimensional array with 10 rows and 10 columns. A shape of (10,) will be a 1-dimensional array with 10 elements.

### N-Dimensional NumPy Arrays
greater than 3 dimensions, 

Let’s say we want to store the monthly earnings of a store, but we want to be able to quickly lookup the results for a quarter, and for a year. The earnings for one year might look like this:
```
 [500, 505, 490, 810, 450, 678, 234, 897, 430, 560, 1023, 640]
year_one = [
    [500,505,490],
    [810,450,678],
    [234,897,430],
    [560,1023,640]
]
# We can retrieve the earnings from January by calling year_one[0][0]
# If we want the results for a whole quarter, we can call year_one[0] or year_one[1]
```

```
earnings = [
    [
        [500,505,490],
        [810,450,678],
        [234,897,430],
        [560,1023,640]
    ],
    [
        [600,605,490],
        [345,900,1000],
        [780,730,710],
        [670,540,324]
    ]
]
```
monthly learining  
` earnings[0,0,0] `

We can also find the shape of the array:
```
earnings.shape
(2, 4, 3)
```
get the earnings for January of all years
```
earnings[:,0,0]

```
 first quarter earnings from both years,
```
earnings[:,0,:]
array([[500, 505, 490],
[600, 605, 490]])
```

### NumPy Data Types
> note : each NumPy array can store elements of a single data type

```
wines.dtype
output // dtype('float64')
```

### Converting Data Types

The method will actually copy the array, and return a new array with the specified data type.

we can convert wines to the int data type:
```
wines.astype(int)
```
We can check the name property of the dtype of the resulting array to see what data type NumPy mapped the resulting array to:

```
int_wines = wines.astype(int)
int_wines.dtype.name
# output //'int64'

```
You can use these directly to convert between types:

```
wines.astype(np.int32)
```

### NumPy Array Operations
NumPy makes it simple to perform mathematical operations on arrays.

#### Single Array Math
If you do any of the basic mathematical operations (/, *, -, +, ^) with an array and a value, it will apply the operation to each of the elements in the array.

```
wines[:,11] + 10
# or 
wines[:,11] += 10
#output // array([ 15., 15., 15., ..., 16., 15., 16.])

```
### Multiple Array Math

All of the common operations (/, *, -, +, ^) will work between arrays.

### Broadcasting

 Essentially, broadcasting involves a few steps:
The last dimension of each array is compared.
If the dimension lengths are equal, or one of the dimensions is of length 1, then we keep going.

If the dimension lengths aren’t equal, and none of the dimensions have length 1, then there’s an error.

Continue checking dimensions until the shortest array is out of dimensions.
```
A: (50,3)
B (3,)
```

This is because the length of the trailing dimension of array A is 3, and the length of the trailing dimension of array B is 3. They’re equal, so that dimension is okay. Array B is then out of elements, so we’re okay, and the arrays are compatible for mathematical operations.
Sources : 
* [What is Jupyter Lab](https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html)
* [Numpy Tutorial](https://www.dataquest.io/blog/numpy-tutorial-python/)
* [Numpy Arrays](https://www.tutorialspoint.com/numpy/index.htm)