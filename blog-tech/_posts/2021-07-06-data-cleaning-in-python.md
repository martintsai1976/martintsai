---
layout: post
title:  "Data Cleaning in Python"
date:   2021-07-06 18:58:57 +0200
category: Tech
image: /blog-tech/assets/images/0706.jpg
---
![]({{ page.image | relative_url}})

### Step 1. Import libraries
The only library you need is Pandas! Import it as "pd" to make your lives easier. You will use this shortcut in the following codes.

<p style="background-color:LightGray; padding-left:30px"> import pandas as pd </p>
<br>

### Step 2. Data exploration
Always explore your data and set up clear objectives before further measures. The sample dataset used in this article is online product information collected from Amazon.com.

Type the following codes to read and display your dataset:
<p style="background-color:LightGray; padding-left:30px"> df = pd.read_csv('the_name_of_your_dataset.csv') <br> df.head(3) </p>

<br>Here is what our dataset looks like: <br>
![Data Exploration]({{site.baseurl}}/blog-tech/assets/images/0706_01.png)

<br>I want to turn this dataset into the following format without missing or duplicate values: <br>
![Data Exploration]({{site.baseurl}}/blog-tech/assets/images/0706_02.png)

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



<a href="https://github.com/martintsai1976/Data-Cleaning-in-Python-for-Beginners.ipynb" target="_blank">Github Post</a>

