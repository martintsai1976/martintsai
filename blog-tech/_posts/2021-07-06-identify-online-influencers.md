---
layout: post
title:  "Identify Online Influencers"
date:   2021-07-05 18:58:57 +0200
category: Tech
image: /blog-tech/assets/images/0706-1.jpg
---
![]({{ page.image | relative_url}})
The advent of online information technology has given online users more chances to become an online influencer through the use of social media and online platforms. Online influencers are typically classified by the number of friends or followers. The more friends they have, the more they could make an impact on others.
<br><br>This study aims to explore the relationship between the number of friends on Yelp.com and other independent variables and identify extra variables that can help indicate online influencers.
<br><br>Also, this research seeks to make a prediction model to help owners on Yelp.com to improve the business. The methodology integrates linear regression, Pearson Correlation Matrix, and machine learning models, such as Decision Tree, Random Forests, and Gradient Boosting Regressions. 
<br><br>The analysis results identified that the number of reviews has a positive correlation with the number of friends, which means that users with higher number of friends also generate higher number of reviews.  Moreover, this study created a prediction model utilizing the Gradient Boosting Regressions. The model has a 71% prediction power in predicting the number of reviews. Company owners can use this model to identify the potential online influencers with a number of reviews, then further extract valuable information.
<br><br>

### Description of Data & Analysis Methods 
<u>Data description</u>
<br>The raw research dataset in this paper included thousands of online reviews from Yelp.com. Each review contained the following variables: date, rating, number of friends, number of reviews, and review content. Specifically, the review contents were analyzed by the text mining system in minemytext.com, and were converted into three new variables for the strength of positive sentiment, the strength of negative sentiment, and the average strength of each review. 
<br><br>Besides, the review dates were transformed into numerical values for further analyses. The dates ranged from July 19, 2009 to June 7, 2021 and were transformed into numbers from 1 to 4,342. The description of the research dataset is presented as follows.
<br><br>
![Data Exploration]({{site.baseurl}}/blog-tech/assets/images/0706-1_01.png)
<br><br>
Among the variables, the number of friends is the dependent variable in this paper, and the distribution of it is shown in the following figures. Most reviewers (98.45%) have less than 1,000 friends on Yelp.com, and around 1% of reviewers have more than 1,500 friends. These people with more than 1,500 friends are regarded as online influencers in the following analysis.
<br><br>
![Data Exploration]({{site.baseurl}}/blog-tech/assets/images/0706-1_02.png)
<br>

<u>Methodology</u>
<br>The research dataset was first analyzed by the linear regression method, which estimated the relationship between independent variables and the dependent variable by minimizing the variances between the observed and predicted values of the dependent variable. The linear regression can indicate whether independent attributes and the target attribute are strongly related. Besides, it examines the statistical significance of each independent variable. Based on the regression results, independent variables that were not statistically significant would be removed from the following analyses. 
<br><br>Secondly, the Pearson correlation coefficient of each statistically significant variable was calculated by data analysis libraries in Python. The calculation results show the linear correlation of two variables and range from -1 to 1. If two variables have a Pearson correlation coefficient that is equal to -1 or 1, it represents a perfect correlation. Variables that have a high correlation coefficient with the target variable (number of friends) can be used as indicators for potential online influencers.
<br><br>Finally, in Chapter 3 (Further Analyses), several regression models including the linear regression were used to build machine learning models that can predict the number of friends. The machine learning models include Decision Tree Regression, Random Forest Regression, and Gradient Boosting Regression.
<br><br>

### Regression Results
<u>Linear Regression</u>
<br>The R-squared value from the linear regression model was 0.246. It means that around 25% of the data fit the regression model. The F-value and Prob(F) test the overall significance of the regression model. The Prob(F) has a value of 0.00, which rejected the null hypothesis that all of the regression coefficients are zero. This implied that at least some of the regression parameters are nonzero and that the regression equation has some validity in fitting the data. 
<br><br>Besides, the p-values of independent variables indicated that all variables except the average sentiment were statistically significant (p-value lower than 0.01). To be more specific, the variable date has a t-value of -4.855, and the p-value is 0.000; the variable rating has a t-value of 4.556, and the p-value is 0.000; the variable negative sentiment has a t-value of -4.339, and the p-value is 0.000; the variable positive sentiment has a t-value of 3.758, and the p-value is 0.000; the variable average sentiment has a t-value of 0.005, and the p-value is 0.996; the variable number of reviews has a t-value of 52.579, and the p-value is 0.000. Thus, the average sentiment, which had 0.996 p-value, was excluded from the following step. Figure 3 shows the result of the linear regression.
<br><br>
![Data Exploration]({{site.baseurl}}/blog-tech/assets/images/0706-1_03.png)

<u>Correlation Matrix</u>
<br>The Correlation Matrix includes correlation coefficients that indicate whether there is a linear relationship between two variables. As a result, the Correlation Matrix of this analysis indicates that there is a low positive but nearly moderate (0.49) linear correlation between number of reviews and number of friends. Next, there is a low positive (0.44) linear correlation between rating and negative sentiment. Finally, there is another low positive (0.34) linear correlation between rating and positive sentiment. The other correlations can be negligible, meaning there are no relationships. The following figure presents the Correlation Matrix of this analysis:
<br><br>
![Data Exploration]({{site.baseurl}}/blog-tech/assets/images/0706-1_04.png)
<br><br>

### Further Analyses
This chapter compares the performance of Linear Regression, Decision Tree, Random Forest and Gradient Boosting algorithms and further examines which model has the best performance.
<br><br>
![Data Exploration]({{site.baseurl}}/blog-tech/assets/images/0706-1_05.png)

<br>Typically, training score indicates how well the model generalized or fitted in the training data. If the model fits so well in a data with lots of variance, then this causes over-fitting. This causes poor results on test scores because the model is curved a lot to fit the training data and generalized very poorly. Further, the test score is when our model is ready. This dataset of test data has not been used before this step. The higher the score, the better the model generalized. Therefore, I aim for a high score in both training and testing.
<br><br>For this analysis, there are 80 percent training data and 20 percent test data. In terms of Figure 5, the Decision Tree regressor had the worst performance, which showed a training and testing score of 0.095 and 0.035 respectively. Next, the Linear Regression has a better performance than Decision Tree Regressor. The training score and testing score of Linear Regression are 0.23 and 0.28 respectively. Finally, Random Forest and Gradient Boosting have the same training score of 0.4929; however, Gradient Boosting got a superior performance of testing score, 0.62, which is higher than the one of Random Forest, 0.49. Thus, the best performance model went to the Gradient boosting model.
<br><br>As regards to Figure 6, it showed the Feature Importance within the Gradient boosting model. The most important feature is the number of reviews, which has a value of approximately 0.8. The next important feature is rating; however, the value fell to only 0.1. The feature date and average sentiment has values less than 0.1, followed by positive sentiment and negative sentiment, which had nearly no value. This result showed that the number of reviews is the strongest predictor compared to the other features.
<br><br>The current test score of the Gradient Boosting model is around 0.62. Although it is already the best score among the models, I still wanted to improve the performance. Therefore, I would like to check that dropping certain features could make the accuracy of the Gradient Boosting model higher. The features were dropped from the least important feature, one by one, until the most important one was left. The scores are presented in the following figure and table.
<br>
![Data Exploration]({{site.baseurl}}/blog-tech/assets/images/0706-1_06.png)

Figure above showed the line graph after dropping each feature, and table 2 presented the names of the dropped features and their corresponding training and testing scores. From Figure 7, it is obvious that every time a feature was dropped, the testing score increased.  From feature 2 to 4, the testing scores increased gradually, and there was a huge rise after dropping feature 5 and 6, which are date and rating. In the meanwhile, the training scores were approximately the same after dropping feature 2 to 5; however, there was a comparably huge improvement after dropping feature 6 rating. In the end, the testing score of the gradient boosting model is with a 71% high prediction power.
<br><br>

### Discussion
Based on the linear regression results and the Correlation matrix (Chapter 4), the variable number of reviews is statistically significant and has the strongest correlation with number of friends compared to the other independent variables. Therefore, I plotted a scatter plot to further examine the relationship between number of friends and number of reviews.  Figure 8 shows that when the number of friends increases, the number of reviews also increases. This indicates that online influencers on Yelp.com also left more reviews compared to the others.
<br><br>
![Data Exploration]({{site.baseurl}}/blog-tech/assets/images/0706-1_07.png)
<br><br>Further, Table 3 compared the value of each variable between general users and online influencers. It shows that online influencers had 3,380 number of friends on average, and they generated 1,725 reviews on average. On the other hand, general users only got 151 number of friends, and they left merely 174 reviews on average. Moreover, the average rating and average sentiment that online influencers created were often higher than the general users. These results are aligned with the literature of Stansberry (2015) who mentioned that a relatively small number of influencers tended to be the main sources of online opinions.
<br><br>
![Data Exploration]({{site.baseurl}}/blog-tech/assets/images/0706-1_08.png)
<br><br>In terms of the further analysis of the prediction model (Chapter 5), the gradient boosting model has approximately 71% prediction power with only 1 variable number of reviews. The other variables would decrease the performance of the model. The result means that we can use the number of reviews to predict the number of friends of a user. The following chart further shows the distribution of true values(blue) and predicted values(red) of the gradient boosting model. If taken ID 1000 (true_value = 64) as a reference point: before ID 1000, the model tends to overestimate the number of friends, after that, the model is prone to underestimate the number of friends. Therefore, the model performs better for people with a smaller number of friends. 
<br><br>
![Data Exploration]({{site.baseurl}}/blog-tech/assets/images/0706-1_09.png)
<br><br>These results can help fill in the gap that I identified in the literature. Besides the number of friends, the number of reviews can also be an indicator of online influencers. It is not only correlated with number of friends, but also a strong predictor of number of friends. Thus, the result allows marketers to examine the number of online reviews to identify whose reviews might play an important part to general users. 
<br><br>

### Conclusion
In conclusion, it is suitable to use the number of friends to classify who is the online influencer and who is not. Users with a comparably higher number of friends can be seen as online influencers, whose behaviors differ from those of general users. Online influencers tend to have a higher number of reviews, higher ratings and higher average sentiment, and their behaviors could possibly influence the general users. Further, a series of analyses showed that number of reviews is the most important indicator of online influencers. By taking the number of friends as a dependent variable, the result showed that the number of reviews has the strongest correlation among the various variables. This indicates that there is a positive relationship with the number of reviews and online influencers. Moreover, the further analyses showed that the number of reviews has a strong prediction power of the number of friends, who are seen as online influencers. 
<br><br>The study provides valuable insights. First, the study identifies that other than the number of friends, the number of reviews is a useful indicator that could generate useful information. Secondly, the Gradient Boosting model in this analysis could be useful in practice. Companies and brands can use the model to identify the online influencers by number of reviews. By scrutinizing the online reviews from the online influencers, companies can save time and read the most valuable content to identify their problems and make subsequent improvements for their business.
<br><br>Check here to see how to perform regression and machine learning analysis used in this paper:
<br><a href="https://github.com/martintsai1976/Identify-Online-Influencers/blob/main/Identify%20Online%20Influencers_Regressions.ipynb" target="_blank">Regressions</a>
<br><a href="https://github.com/martintsai1976/Identify-Online-Influencers/blob/main/Identify%20Online%20Influencers_ML.ipynb" target="_blank">Machine Learning</a>

### Thank you for reading!