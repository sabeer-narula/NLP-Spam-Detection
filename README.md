# SMS and Email Spam Detection using Naive Bayes and Logistic Regression

## Authors
- Sabeer Narula
- Seth Serrano

## Abstract
Spam has been an issue that has plagued people since the advent of the internet. While many people are confident in their abilities to detect spam, it only takes one lapse in judgement for someone to lose their credit card details, download a virus, or wire a scammer thousands of dollars. While internet security training can mitigate these issue, 40-80% of sent emails are estimated to be spam - more than 100 billlion per day. Americans alone recieved 225 billion spam texts last year. I recieved one 3 hours ago, despite being on the federal no spam list. The damage is in the billions yearly, and instead of relying on humans on detecting spam, it is far more effective to remove them prior. We tried to approach solving this problem using two different methods - Naive Bayes and Logistic Regression. I worked on SMS spam while Seth worked on emails, and I found using Logistic Regresssion for training on the sms spam dataset from the SMS Spam Corpus worked slightly better than NB, but both were very effective. We initially preprocessed the text using a lemmatizer and a Bag of Words extraction. We then split the dataset 80:20, and trained on 80% of the data. NB waas 98.2% effective on the validation part of the dataset, while LR wass 99.2%. However, one major issue with spam detection is not having false positives (marking a legitimate message as Spam) which can be very detrimental. We wanted to test this so we ran both models on a complely new SMS dataset (with only legitimate messages encompassed), and NB detected it as 98.33% non-spam and LR detected it as 99.9% non-spam which was very impressive. As such, in our final model on the website we created, we used LR for sms spam detection. For the emails side, NB was actually just as effective as LR when we ran the model on the Enron Email dataset, and so we used NB for the email spam detection side on the website.

## Getting Started
This project involves reading and preprocessing data from CSV files containing SMS and email messages, followed by the application of machine learning models for spam detection. 

### Data Acquisition and Preprocessing
Data is obtained from:
- [Singaporean student text messages corpus](https://scholarbank.nus.edu.sg/handle/10635/137343)
- [Mobile text dataset](https://digitalcommons.mtu.edu/mobiletext/1/)
- [Spam sms dataset](https://www.kaggle.com/datasets/uciml/sms-spam-collection-dataset)
- [Text message corpus](https://web.archive.org/web/20130921043042/http://cybersecurity.cit.purduecal.edu/content/tmcorpus.html)
- [Enron email dataset](https://www.kaggle.com/datasets/wcukierski/enron-email-dataset)
- [Spam email dataset](https://www.kaggle.com/code/balaka18/email-spam-classification)
- [British Columbia Conversation Corpus](https://nlp.cs.ubc.ca/bc3.html)
and preprocessed to remove irrelevant characters and stopwords. The preprocessing involves tokenization, lemmatization, and the creation of a Bag of Words model.

## Model Training Procedure

The core of our spam detection system lies in the training of two machine learning models: Naive Bayes and Logistic Regression. Below is the step-by-step procedure and pseudocode that outlines the training process for both models.

### Steps for Training Models:
1. **Initialize the Models**: Start with two separate models, Naive Bayes and Logistic Regression.
2. **Training Process**:
   - For each model, perform the following steps:
     a. Utilize the training dataset, which consists of:
        - `X_train`: Features derived from the messages, transformed via vectorization.
        - `y_train`: Labels indicating whether a message is spam (`1`) or not spam (`0`).
     b. Train the model using the `fit` method with `X_train` and `y_train`.
     c. Through this process, the model learns to associate specific features with the labels of spam or not spam.

### Pseudocode for Training Models:
```plaintext
FOR EACH model IN [Naive Bayes, Logistic Regression]
    model.fit(X_train, y_train)
    PRINT "Model is trained and ready to classify messages"
END FOR
