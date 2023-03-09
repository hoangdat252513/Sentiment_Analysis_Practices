# Introduction

Sentiment analysis (or opinion mining) is a natural language processing (NLP) technique used to determine whether data is positive, negative or neutral. Sentiment analysis is often performed on textual data to help businesses monitor brand and product sentiment in customer feedback, and understand customer needs.

Sentiment analysis helps data analysts within large enterprises gauge public opinion, conduct nuanced market research, monitor brand and product reputation, and understand customer experiences. In addition, companies often develop sentiment analysis systems for customer experience management, social media monitoring, or workforce analytics platform to about their own customers.

![image](https://user-images.githubusercontent.com/83870939/224066942-3df40452-fede-4639-a405-deabf35a6b25.png)

Detail: https://blog.mobcoder.com/sentimental-analysis-how-the-phenomenon-changing-the-dynamics-of-brand-monitoring/

# Sentiment_Analysis_Practices

Source dataset Amazon's reviewed products:  https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Jewelry_v1_00.tsv.gz

I use this dataset for fine-grained sentiment analysis (Positive - Neutral - Negative or following a number of star rating)

## Common Table content

### 1. Exploratory Data Analysis: Visualization, astype grade, shuffle and pick up sample

### 2. Preprocessing Data:

    Remove the HTML tags and URLs
    
    Remove punctuations 
    
    Remove extra spaces between words
    
    Remove the stopwords
    
    Perform contractions
    
    Convert all Text into lower case
    
    Lemmatization
    
But in Vietnamese, some techniques like Lematization, stopwords don't have or different than English

### 3. Build model

We can use some Machine Learning model like: Naive Bayses, Logistic Regression, Suport Vector Machine to predict the Grade of the text

Or use RNN model (I use Bidirectional LSTM) to learn feature of input (text). But before fit data for training you have to tokenization and zero padding (pad_sequence) to encoding input into vector and have the same dimension

Some of feature extraction can use for text: Bag of Word (BOW), Bag of N-gram, TF-IDF, Word2Vec. I recommmend use TF-IDF (note that rather use n-gram) or Word2Vec

## Result

Bidirectional LSTM model predict 5 label (follow star rating) with accuracy 51.5%

![image](https://user-images.githubusercontent.com/83870939/224073161-109f8fc0-4f5d-4af1-a367-8a59b1960f50.png)

Logistic Regression predict 3 label (Positive as 5,4 star - Neutral as 3 star - Negative as 1,2 star) with accuracy 72%

![image](https://user-images.githubusercontent.com/83870939/224073853-ee9d7c09-eb9c-41fe-85a4-f99b2070ab1d.png)

## Optional

The notebook Sentiment_Analysis_Pretrained.ipynb for practise use Pretrained-Model for sentiment analysis: Vader(Sentiment Intensive Analyze), Roberta, DistilBERT, XLNet, transformer_pipeline from Transformer
