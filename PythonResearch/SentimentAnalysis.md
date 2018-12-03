# Algorithmic Trading of Cryptocurrency Based on Twitter Sentiment Analysis 
> Past research has shown that real time Twitter data can be used to predict market movement of securities and other financial instruments. The goal of this paper is to prove whether Twitter data relating to cryptocurrencies can be utilized to develop advantageous crypto coin trading strategies. By way of supervised machine learning techniques, our team will outline several machine learning pipelines with the objective of identifying cryptocurrency market movement.

* [Stuart Colianni, Stephanie Rosales, and Michael Signorotti](http://cs229.stanford.edu/proj2015/029_report.pdf) 

### Additional Resources 
* [Research Doc.1](http://cs229.stanford.edu/proj2015/029_report.pdf)
* [Sentiment Analysis with Python](https://towardsdatascience.com/sentiment-analysis-with-python-part-1-5ce197074184)
* [Python NLTK Text Classification Demo](https://text-processing.com/demo/sentiment/)
* [Simplifying Sentiment Analysis in Python](https://www.datacamp.com/community/tutorials/simplifying-sentiment-analysis-python)

#### Background Information 
**Creating a Training and Testing Data Set** 
----
> In order to create a training and testing data set for the learning algorithms, we utilize [Tweepy](http://www.tweepy.org/) - an open-source Python library for accessing the Twitter API. They keyword Bitcoin is searched in real time and tweets containing that token are placed in a text file. Additional data being collected for each post containing the keyword includes the user ID, a unique identifier which cannot be changed, and a time stamp. In addition, the prices of the cryptocurrency is collected every hour via the [cryptonator API](https://www.cryptonator.com/api) and placed into text files to create a price history. 

(_Research Doc.1_, S. Colianni, S. Rosales, M. Signorotti)

**Understanding Natural Language Processing and Python** 
----
_Sentiment Analysis_ or sentiment classification fall into the broad category of text classification tasks where you are supplied with a phrase, or a list of phrases and your classifier is supposed to tell if the sentiment behind that is positive, negative or neutral. Sometimes, the third attribute is not taken to keep it a binary classification. 

There are a number of preliminary processes that are essential for sentiment analysis: _data preprocessing and data cleaning_. The objective of these processes is to clean any _noise_ that is present in the raw data. This could be anything such as punctuation, special characters, numbers, and terms which don't carry significant weight in context to the data . 

![Diagram 1](https://cdn-images-1.medium.com/max/361/0*ga5rNPmVYBsCm-lz.)

**Classification Practices in Sentiment Analysis** 
---- 
* _Naive Bayes Classification_: 
* _Feature Vectors_: 
* _Logistic Regression_: 
