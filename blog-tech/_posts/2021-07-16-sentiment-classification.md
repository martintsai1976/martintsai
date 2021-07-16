---
layout: post
title:  "Sentiment Classification with Deep Learning (BERT + PyTorch)"
date:   2021-07-14 11:08:57 +0200
category: Tech
image: /blog-tech/assets/images/0716/0716.jpg
---
This paper introduces the process of establishing a sentiment classification model with BERT and PyTorch in Python.
<br><br>First, a pre-trained text transformer BERT BASE was inserted into the PyTorch neural network environment. BERT BASE was pre-trained through Masked Language Modeling (MLM) and Next Sentence Prediction (NSP) techniques. Based on what it learned, BERT BASE uses 12 encoder layers to convert the input sentence into a tensor that can best represent that sentence. Each token from the input layer will be converted into 768 hidden units.
<br><br>In our case, the size of each output tensor was 150, the maximum token length, times 768. For a classification model, the first 768 output units (pooled output) are good enough to represent the input sentence (Devlin et al., 2019). Therefore, the pooled output with the target variable (positive or negative) was sent to a Linear Transformer and converted into two output units that each represented the probabilities of the sentiment class. The output unit with a higher value would represent the predicted sentiment of the input sentence.
<br>
<div style="text-align: center"><img src="{{site.baseurl}}/blog-tech/assets/images/0716/0716_1.png"></div>
<br><br>The Linear Transformer applied a linear transformation to the pooled output based on the following formula: y = Ax + b. The x was a tensor that contained 768 output values, and y represented the target variable (0 is negative, and 1 is positive). The Linear Transformer tried to find out the best weight (A) and bias (b) that could most accurately transform the pooled output into the correct target variable.
<br><br>After completing the setup of the neural network environment, the training set was applied to train the sentiment analysis model for 10 epochs. At the same time, the validation set was used to validate the performance of the model under each epoch and identify the best model with the highest accuracy among the ten epochs. The training history was as follows. The training accuracy reached almost 100% at the fourth epoch, and the validation accuracy stayed around 96.5% for the whole process, indicating that 10 epochs were enough to train this model because the validation accuracy could not be further improved by running more epochs.  
<br>
<div style="text-align: center"><img src="{{site.baseurl}}/blog-tech/assets/images/0716/0716_2.png"></div>
<br><br>After the training process, the test set was used to test the performance of the sentiment analysis model with the highest validation accuracy. The model performance and confusion matrix were as follows. 
<br>
<div style="text-align: center"><img src="{{site.baseurl}}/blog-tech/assets/images/0716/0716_3.png"></div>
<br>
<div style="text-align: center"><img src="{{site.baseurl}}/blog-tech/assets/images/0716/0716_4.png"></div>
<br><br>The accuracy (F1-score) of negative and positive classes were 87% and 98%, and the overall accuracy reached 96%. The F1-score showed the weighted average of the precision and recall that indicates the accuracy of the classification model. Overall, the trained model had a great performance on the sentiment classification of online reviews according to the testing results. 

<br>Check here to see how to build a sentiment classification model demonstrated in this paper with BERT and PyTorch :
<br><a href="https://github.com/martintsai1976/Sentiment-Classification-with-Deep-Learning-BERT-PyTorch-/blob/main/Sentiment%20Classification.ipynb" target="_blank">Sentiment Classification</a>

### Thank you for reading!