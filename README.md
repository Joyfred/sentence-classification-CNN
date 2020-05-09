# Sentence Classification using CNN

## 1. Introduction

Sentiment analysis of short texts such as single sentences and tweets are challenging because of the limited contextual information that they normally contain. Effectively solving this task requires strategies that combine the small text content with prior knowledge and use more than just bag-of-words.

Typically, CNN’s are considered appropriate for image classifications. Based on past  research works, certain niche architectures of CNN are considered successful for classification problems of NLP.

## 2. Dataset Used

Data is a CSV consisting of 16,00,000 tweets with emoticons removed. Data file format has 6 fields as mentioned below:

0 - the polarity of the tweet (0 = negative, 4 = positive) <br/>
1 - the id of the tweet (2087) <br/>
2 - the date of the tweet (Sat May 16 23:58:44 UTC 2009) <br/>
3 - the query (lyx). If there is no query, then this value is NO_QUERY. <br/>
4 - the user that tweeted (robotickilldozr) <br/>
5 - the text of the tweet (Lyx is cool) <br/>

## 3. Network Architecture

* 1 embedding layer <br/>
* 3 region sizes = (2, 3, 4) <br/>
* 32 filters for each region size, Totally, 98 filters <br/>
* 1 max pooling layer after each unique region sized layer <br/>
* A Dense Layer of ReLu activation <br/>
* A Drop-out Layer <br/>
* A Dense Layer of Softmax activation <br/>

Every filter performs convolution on the sentence matrix and generates (variable-length) feature maps. Then 1-max pooling is performed over each map, i.e., the largest number from each feature map is recorded

Simplified Representation(2 filter/region size & 1 dense layer) of the network architecture:
![Image of Network Architecture](https://github.com/Joyfred/sentence-classification-CNN/blob/master/img/Network%20Architecture.png)

## 4. Conclusion

Out of 1600000 tweets, 16000 are used for testing and the remaining for training. Distribution of positive and negative tweets are equal (8,00,000 each). Model was trained for 5 epochs with binary cross-entropy loss. 

Binary cross-entropy:

![cross-entropy formula](https://github.com/Joyfred/sentence-classification-CNN/blob/master/img/binary-cross-entropy.png)

Finally, loss of 0.138 and accuracy of 94.8% was achieved.
