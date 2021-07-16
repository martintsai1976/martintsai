---
layout: post
title:  "Natural Language Processing for Online Reviews"
date:   2021-07-10 11:08:57 +0200
category: Tech
image: /blog-tech/assets/images/0707/0707-1.jpg
---
Several Natural Language Processing procedures were conducted to transform the clean data into desired formats for further analyses.

<br>Step (1): All multi-sentence reviews were broken into single sentences. These sentences would become the raw data for building the machine learning model to identify product features.
```php
# Break reviews into sentences
from nltk.tokenize import sent_tokenize
st = []
for sentence in rv.content:
    st.append(sent_tokenize(sentence))
```
<br>Step (2): All letters were converted into lower case. This step ensured that the calculation of the appearance frequencies of each product feature would not be affected by upper or lower case.
```php
# Convert sentences into lowercase
rv2['sentence'] = [x.lower() for x in rv2.raw_sentence]
rv3 = rv2.drop(columns='raw_sentence')
rv3.head(2)
```

<br>Step (3): Every word was tagged with part-of-speech codes. Each code represented a distinctive meaning. For instance, “NN” meant a singular noun, and “NNS” represented a plural noun. 
```php
# POS tagging
pos = []
for sentence in rv3.sentence:
    w = word_tokenize(sentence)
    pos.append(nltk.pos_tag(w))
```

<br>Step (4): All words were normalized into their root forms. For example, the words “louder” and “loudest” were lemmatized as the word “loud” because they represented the same product feature (high volume). This step prevented the subsequent processes from being affected by word forms. 
```php
# Lemmatize the lists
ft1 = []
for k in range(len(ft)):
    words=ft[k]
    WNlemma = nltk.WordNetLemmatizer()
    refined_list = [WNlemma.lemmatize(t, pos='n') for t in words]
    ft1.append(refined_list)
    
st1 = []
for k in range(len(st)):
    words=st[k]
    WNlemma = nltk.WordNetLemmatizer()
    refined_list = [WNlemma.lemmatize(t, pos='a') for t in words]
    st1.append(refined_list)
```

<br>Step (5): Nouns and adjectives in the same sentence were paired to identify product features. An adjective was followed by a noun to show the product feature with a brief description.
```php
# Create feature-sentiment pairs
pairs = []
for k in range(len(st1)):
    list = [i+"/"+str(j) for i in st1[k] for j in ft1[k]]
    pairs.append(list)
```

<br>The following table summarizes each step taken in this chapter with a real product review from Amazon.com.
![]({{site.baseurl}}/blog-tech/assets/images/0707/0707-1_01.jpg)

<br>Check here to see how to perform natural language processing techniques utilized in this paper:
<br><a href="https://github.com/martintsai1976/Natural-Language-Processing-for-Online-Reviews/blob/main/Natural%20Language%20Processing.ipynb" target="_blank">Natural Language Processing</a>

### Thank you for reading!
