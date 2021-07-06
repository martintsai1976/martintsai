---
layout: post
title:  "Data Cleaning in Python for Beginners"
date:   2021-07-05 18:58:57 +0200
category: Tech
---

### Step 1. Import libraries
The only library you need is Pandas! Import it as "pd" to make your lives easier. You will use this shortcut in the following codes.

<p style="background-color:LightGray; padding-left:10px"> import pandas as pd </p>

### Step 2. Data exploration
Always explore your data and set up clear objectives before further measures. The sample dataset used in this article is online product information collected from Amazon.com.

Type the following codes to read and display your dataset:
<p style="background-color:LightGray; padding-left:10px"> df = pd.read_csv('df.csv') <br> df.head(3) </p>

Here is what our dataset looks like: <br>
<img src="/blog-tech/assets/images/0706_data_exploration.png">


<a href="https://github.com/martintsai1976/Data-Cleaning-in-Python-for-Beginners.ipynb" target="_blank">Github Post</a>

