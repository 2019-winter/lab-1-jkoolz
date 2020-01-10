---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name: Jack Kooley


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


What is the shortcut for making a new cell? How can I quickly send you my notebook? What is the marsland notebook?


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.

```python
import pandas as pd
import numpy as np
```

## Exercise 1

```python
# YOUR SOLUTION HERE
a = np.full((6,4), 2)
a
```

## Exercise 2

```python
# YOUR SOLUTION HERE
b = np.full((6,4), 1)
np.fill_diagonal(b, 3)
b
```

## Exercise 3

```python
# YOUR SOLUTION HERE
a * b
```

```python
np.dot(a, b)
```

This doesn't work because np.dot() is attempting to take the dot product of the arrays while the a * b expression is simply multiplying like cells through element by element multiplication


## Exercise 4

```python
# YOUR SOLUTION HERE
np.dot(a.transpose(), b)
```

```python
np.dot(a, b.transpose())
```

The reason these dot products are different is because they have different shapes when they are transposed and the dot product is dependent upon which shape is used in the expression.


## Exercise 5

```python
# YOUR SOLUTION HERE
def print_stuff(stuff):
    print(stuff)
    
print_stuff("Hello, World")
```

## Exercise 6

```python
# YOUR SOLUTION HERE
def rand_arrays():
    a = np.random.rand(6,4)
    print(a.sum())
    print(a.mean())
    print(a.sum(axis = 1))
    print(a.sum(axis = 0))
    
rand_arrays()
```

## Exercise 7

```python
# YOUR SOLUTION HERE
def num_ones(arr):
    c = 0
    for i in range(len(arr)):
        for j in range(len(arr[0])):
            if (arr[i][j] == 1):
                c += 1
    
    return c, len(np.where(arr == 1)[0])

a = np.full((6,4), 1)
num_ones(a)
```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
# YOUR SOLUTION HERE
a = pd.DataFrame(np.full((6,4), 2))
a
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
# YOUR SOLUTION HERE
b = np.full((6,4), 1)
np.fill_diagonal(b, 3)
b = pd.DataFrame(b)
b
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
# YOUR SOLUTION HERE
a * b
```

```python
np.dot(a, b)
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
# YOUR SOLUTION HERE
def df_num_ones(df):
    return len(np.where(df == 1)[0])

a = pd.DataFrame(np.full((6,4), 1))
df_num_ones(a)
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
## YOUR SOLUTION HERE
titanic_df['name']
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
## YOUR SOLUTION HERE
titanic_df.set_index('sex',inplace=True)
```

```python
titanic_df.loc["female"]
```

## Exercise 14
How do you reset the index?

```python
## YOUR SOLUTION HERE
```

```python
titanic_df.reset_index(inplace = True)
titanic_df
```

```python

```
