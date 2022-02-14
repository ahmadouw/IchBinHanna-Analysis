# IchBinHanna-Analysis

### Author: Ahmadou Wagne, TU Vienna, Master Data Science 
### Project Main Supervisor: Dr. Jana Lasser, TU Graz
### Project Co-Supervisor: Prof. Allan Hanbury, TU Vienna

### Overview
This project is conducted as part of the interdisciplinary project module of the Data Science curriculum at the TU Vienna. The topic of the project is to identify events that correspond to the twitter hashtag #IchBinHanna
using topic modelling and to perform sentiment analysis on a series of tweets containing the hashtag using dictionary based methods. The results are described in the report. However they to reproduce them,
the tweet collection (tweet IDs available at https://github.com/LaserSteff/IchbinHanna/blob/main/data/tweet_IDs/IchBinHanna_TweetIDs.txt). To make it possible to comprehend the analysis and methods used without obtaining the data, the repository consists of documented Jupyter Notebooks that are described below.

### Requirements
The whole project is written in Python 3.8.5 and all versions of packages used can be found in the requirements.txt.
### User profiles
Add_user_profiles.ipynb requires the data set containing all relevant tweets containing #IchBinHanna, as well as the data set containing the classified user profiles (have to be added in a directory /data/tweets as IchBinHanna.csv and TwitterUserClassification.csv). 
In this notebook both data sets are merged, which is not trivial, as some user IDs were broken due to an issue regarding their encoding. It also generates the data set that is further used (has to be also added to /data/tweets)

### Data Analysis
Data_analysis.ipynb requires the merged data set mentioned above. 
This notebook tackles the problem of data quality, analyses the distribution of tweet volumes and user profiles over time and observes a first draft of events using tweet and hashtag frequencies.

### Topic Modelling
Topic_modelling.ipynb requires the merged data set again only requires the merged data set.
Here Latent Dirichlet Allocation is used as an approach for topic modelling. It generates topics for the whole data set and different subsets of the data (monthly, per language) and visualizes the terms that define the topic. Those topics are used to identify further events.
Also topics per user group are analyzed, to observe whether the topics discussed vary across different groups.

### Sentiment Analysis
This topic includes the notebooks Sentiment_analysis_LIWC.ipynb, Sentiment_analysis_VADER.ipnyb and transformer_emotion.ipynb. They all require the merged data sets and the LIWC notebook additionaly requires the 2007 German LIWC dictionary,
as well as the 2015 English one (the word "like" has to be excluded manually) and a file generated by the VADER notebook called vader_sentiment.csv in the /data/tweets directory, which is used to compare the results of the dictionary based approaches.
The notebooks for VADER and LIWC contain a broad analysis of the sentiment of the relevant tweets concerning the development over time, the hashtags used in different classes, words used in different classes and the sentiment for different user groups and at specific events.
The transformer notebook is used to check on the intuition that several aspects of the tweets result in bad performance of the dictionary based methods on the #IchBinHanna twitter data. Here a pretrained transformer model is used on the english tweets that classifies emotion.
This part is not scientifically relevant and is only used to get a hint on the performance of the models.

