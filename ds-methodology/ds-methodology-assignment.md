## Topic chosen
Emails

## The problem
The client's help desk receives questions and requests for support from clients via email. The help desk personnel read the emails and defines to which of pre-defined categories the specific question/request belongs. The response email is sent to the client that includes more specific instructions for further clarification in accordance with the problem category.

## Question to be answered using data
Can we automatically determine the problem category based on the text of the request email message?

## Analytic Approach
One of the widely used natural language processing task in different business problems is “Text Classification”. The goal of text classification is to automatically classify the text documents into one or more defined categories.

There are many different choices of machine learning models which can be used to train a text classifier model. Since there are multiple implementations/libraries available we will try and evaluate three options. We implement Naive Bayes Classifier and Boosting models using ML libraries. We also will check one of available cloud solutions: Watson Natural Language Classifier (https://www.ibm.com/watson/services/natural-language-classifier/).

- Naive Bayes is a classification technique based on Bayes’ Theorem with an assumption of independence among predictors. We can create naive bayes model using sklearn implementation with different features.
- Boosting models are type of ensemble models part of tree based models. Boosting is a machine learning ensemble meta-algorithm for primarily reducing bias, and also variance in supervised learning. We can use XGBoost library to implement the boosting model classifier.
- Watson Natural Language Classifier (NLC) allows users to classify text into custom categories, at scale. Developers without a background in machine learning (ML) or NLP can enhance their applications using this service. NLC combines various advanced ML techniques to provide the highest accuracy possible, without requiring a lot of training data. We add this option in scope since it allows the client to avoid all the effort required to host on-premise classifier and infrastructure it requires.

## Data Requirements
Text Classification is an example of supervised machine learning task. Thus, we need a labeled dataset containing text documents and their labels to train a classifier.

## Data Collection
In the initial data collection stage, we will export already processed request from the client's issue tracking system. For each request we need to extract its text and the category (label) that was assigned by help desk personnel.

## Data Understanding and Preparation
First of all we need to review list of categories to be assigned by the help desk. These categories will form set of labels we will use in our model.

On the second step we need to look at request texts we have. We will start with cleaning data that can help to reduce the noise present in text data in the form of stop words, punctuations marks, suffix variations etc. Then we will prepare features to be used in our models. The request texts are actually series of words (ordered). In order to run machine learning algorithms we need to convert the texts into numerical feature vectors. We will use two types of features:
- Count Vectors - a matrix notation of the dataset in which every row represents a document from the corpus, every column represents a term from the corpus, and every cell represents the frequency count of a particular term in a particular document.
- TF-IDF Vectors - a score that represents the relative importance of a term in the document and the entire corpus. TF-IDF score is composed by two terms: the first computes the normalized Term Frequency (TF), the second term is the Inverse Document Frequency (IDF), computed as the logarithm of the number of the documents in the corpus divided by the number of documents where the specific term appears.

## Modeling and Evaluation
During the modeling stage we will define and train:
- Naive Bayes classifiers using sklearn implementations with count vectors and TF-IDF vectors.
- Boosting models using XGBoost library with count vectors and TF-IDF vectors.
- Watson Natural Language Classifier model using our texts.

To evaluate models we will use Accuracy - the number of correct predictions made by the model over all kinds predictions made. To better understand the results we will also create a confusion matrix which presents a summary on how many recipes from each category are correctly classified. This may give us ideas on how to adjust the training process to better detect some specific categories we failed to detect well.

To validate the stability of our machine learning model we will use cross-validation technique. In K Fold cross validation, the data is divided into k subsets. Now the holdout method is repeated k times, such that each time, one of the k subsets is used as the test set/ validation set and the other k-1 subsets are put together to form a training set. We will average the error estimation over all k trials to get total effectiveness of our models.
