---
layout: post
title:  "Market Segmentation with K-means Clustering"
date:   2021-07-06 10:58:57 +0200
category: Tech
image: /blog-tech/assets/images/0707/0707.jpg
---
Price levels are the main factors that affect purchase decisions and essential research resources. This article identified the price levels in the target market through analyzing the price data collected from online marketplaces.
<br><br>First, the k-means clustering algorithm divided product prices into different price clusters, and the Elbow Method served as a reference to determine the number of clusters. The result of the Elbow Method showed that three clusters might be a good choice for this study.
<div style="text-align: center"><img src="{{site.baseurl}}/blog-tech/assets/images/0707/0707_01.png"></div>

<br><br>However, the price range of each cluster was very wide after clustering product prices with 3 clusters. This situation harmed the validity of this study because customers with significantly different needs might be included in the same cluster. Therefore, the number of clusters was increased to identify a greater degree of granularity and provide finer suggestions for users. Finally, the number of clusters was set at five, and the clustering result was as follows.
<br>
<div style="text-align: center"><img src="{{site.baseurl}}/blog-tech/assets/images/0707/0707_02.png"></div>
<div style="text-align: center"><img src="{{site.baseurl}}/blog-tech/assets/images/0707/0707_03.png"></div>
<br><br>The clustering results helped companies better understand market demands and consumer needs, supporting product developers in making multiple decisions. Check here to see how to perform Elbow Method and k-means clustering utilized in this paper:
<br><a href="https://github.com/martintsai1976/Market-Segmentation-with-k-means-Clustering/blob/main/Market%20Segmentation%20with%20k-means%20Clustering.ipynb" target="_blank">K-means Clustering</a>

### Thank you for reading!