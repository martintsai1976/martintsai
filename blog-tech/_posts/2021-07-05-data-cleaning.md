---
layout: post
title:  "Data Cleaning in Python"
date:   2021-07-01 18:58:57 +0200
category: Tech
image: /blog-tech/assets/images/0706/0706.jpg
---
This paper explains all the basic techniques for data cleaning in Python. Data cleaning is one of the most important processes for data analysis, and a good way to start your Data Science journey!

### Step 1. Import libraries
The only library you need is Pandas! Import it as "pd" to make your lives easier. You will use this shortcut in the following codes.
```php
import pandas as pd
```

### Step 2. Data exploration
Always explore your data and set up clear objectives before further measures. The sample dataset used in this article is online product information collected from Amazon.com.

Type the following codes to read and display your dataset:
```php
df = pd.read_csv('the_name_of_your_dataset.csv')
df.head(3)
```

<br>Here is what our dataset looks like. There are 7 columns in total with a bunch of information about online products.
<br>![]({{site.baseurl}}/blog-tech/assets/images/0706/0706_01.png)

<br>I want to turn this dataset into the following format without missing or duplicate values: 
<br>![]({{site.baseurl}}/blog-tech/assets/images/0706/0706_02.png)

<br>To successfully convert our dataset into the desired format, you will learn the following techniques:
<ul>
  <li>Drop useless columns</li>
  <li>Drop missing values</li>
  <li>Drop duplicate values</li>
  <li>Split one column into multiple columns</li>
  <li>Rename columns</li>
</ul>

So, without further ado, let’s get started!
<br><br>

### Step 3. Drop useless columns
I always like to remove columns I don't need before further procedures to make my dataset look cleaner. There are two ways to remove useless columns. First way is telling Pandas which columns you want to remove with the following codes:
<br>
```php
df = df.drop(columns=['A', 'B', 'D', 'E', 'F'])
```
Or you can just select columns you want to keep with the following codes:
<br>
```php
df = df[['C', 'G']]
```
![]({{site.baseurl}}/blog-tech/assets/images/0706/0706_05.png)
<br><br>

### Step 4. Drop missing/duplicate values
It is an important process to drop missing or duplicate values from your dataset because they can distort your analysis process adn bring you incorrect results. You can use the following codes to remove missing values. This line of codes means that Pandas will remove every row that contain at least one missing values.
<br>
```php
df = df.dropna()
```
Also, I want to remove all duplicate values based on column C (the product name) to ensure each product is unique. Therefore, I use the following codes to drop all duplicates:
<br>
```php
df = df.drop_duplicates(subset=['C'])
```
<br>

### Step 5. Split one column into multiple columns
Column G contain information of both the number of ratings and the number of reviews. For example: 121 global ratings | 48 global reviews. I want to split this column into two separate columns and only keep the numerical values.
<br><br>Therefore, I conduct the following procedures:
```php
# Split column G into two sperate columns
df['number_of_ratings'] = df['G'].str.rsplit(' | ').str[0]
df['number_of_reviews'] = df['G'].str.rsplit(' | ').str[-1]

# Remove the words 'global ratings' and 'global reviews'
df['number_of_ratings'] = df['number_of_ratings'].str.replace(' global ratings', '')
df['number_of_reviews'] = df['number_of_reviews'].str.replace(' global reviews', '')

# Remove comma between numbers
df['number_of_ratings'] = df['number_of_ratings'].str.replace(',', '')
df['number_of_reviews'] = df['number_of_reviews'].str.replace(',', '')

# Drop original columns
df = df.drop(columns='G')
```

Now, let's take a look at what our dataset looks like. It seems that there is still one more thing needed to be done, renaming the column.
<br>![]({{site.baseurl}}/blog-tech/assets/images/0706/0706_03.png)
<br><br>

### Step 6. Rename columns
I want to change the name of column C into "product_name". Therefore, I conducted the following codes, and now the dataset is exactly what we want.
<br>
```php
df = df.rename(columns={'C': 'product_name'})
```
<br>![]({{site.baseurl}}/blog-tech/assets/images/0706/0706_04.png)
<br>

### Summary
This paper tells you all the basic techniques to perform data cleaning in Python and start your Data Science journey. To know more about each function utilized in this paper, click the following buttons:

<a href="https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.drop.html" target="_blank">Drop columns</a>
<br><a href="https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.dropna.html" target="_blank">Drop missing values</a>
<br><a href="https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.drop_duplicates.html" target="_blank">Drop duplicate values</a>
<br><a href="https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.replace.html" target="_blank">Remove/replace strings</a>
<br><a href="https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.rename.html" target="_blank">Rename columns</a>

Check here to see the complete notebook used in this paper:
<br><a href="https://github.com/martintsai1976/Data-Cleaning-in-Python/blob/main/Data%20Cleaning%20in%20Python.ipynb" target="_blank">Github</a>
<br>

### Thank you for reading!