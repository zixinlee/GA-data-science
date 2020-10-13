# Project 3: Classifying subreddit posts

View notebooks on NBviewer:
- [Part 1: Data collection and data cleaning](https://nbviewer.jupyter.org/github/zixinlee/GA-data-science/blob/master/Reddit-classification/1-Reddit-data-collection.ipynb)
- [Part 2: EDA and modelling](https://nbviewer.jupyter.org/github/zixinlee/GA-data-science/blob/master/Reddit-classification/2-EDA-modelling.ipynb)
---

### Problem statement

In this project, I attempt to classify posts from two subreddits – `r/AskWomen` and `r/AskWomenOver30`.
Both subreddits provide women a space where they can comfortably and candidly share their responses in a non-judgmental space, but the latter is catered towards females above 30 years old.

These two subreddits were chosen as I am interested in the study of human nature and wanted to examine whether and how topics of discussion amongst women differ between age groups.
Due to the overlapping nature of these subreddits, I am also keen to find out whether a machine learning model will be able to distinguish between posts from the two subreddits and extract meaningful differences in the topics discussed in them.

### Summary of approach and findings
_(A more detailed explanation of the project process is covered from the next section onwards.)_

To begin, I used Reddit's API to scrape posts from each subreddit. Next, I cleaned and transformed the raw text data into a numerical representation that can be understood by our machine learning models. Briefly, this involves:

- Cleaning text data – remove HTML, punctuation, and non-alphabetical text using regular expressions, and removing stopwords
- Preprocessing text data – lemmatization, tokenization and vectorization.

In my modelling process, I tested 3 classification models – Logistic Regression, Multinomial Naive Bayes, and Support Vector Machine – and evaluated them primarily on their Accuracy score and AUC score. The Logistic Regression model performed the best with an accuracy score of 0.8 and AUC score of 0.86, which suggests that it is able to correctly classify a post into the correct subreddit 80% of the time.

---

## Detailed overview of project

### Data preparation

Using Reddit's API, I collected close to 1,000 posts from each subreddit, which is the cap that Reddit has imposed on the number of posts that can be scraped at any one time. The posts were first cleaned and preprocessed as outlined below.

* Remove posts by moderators
* Combine the post title and post content columns into a single column
* Create target variable column `is_askwomenover30`
* Make text all lowercase
* Remove punctuation
* Remove all non-alphabetical text
* Remove stopwords
* Lemmatize words (which means to retrieve the dictionary form of a word)

The last step in our data preparation is to encode our text as numbers via Tokenization + Vectorization, because machine learning models are only able to take in numerical features as input. Specifically, when working with text documents, we transform them so that each document is represented as a numerical vector.

Sklearn has two built-in vectorizers, the CountVectorizer and TfidfVectizer, which takes in a collection of text documents and performs tokenization and vectorization together.

The difference between the two is that Count Vectorizer will simply count the frequency of every word and give every word an equal weightage. On the other hand, the TFIDF Vectorizer gives different weights to words. The fewer documents in which a term occurs, the more significant it likely is to be to the documents it does occur in.

I tested both vectorizers for each classification model for a more comprehensive comparison.

### Modelling

These are the 3 classification models that were evaluated:

 1. Logistic Regression
 2. Multinomial Naive Bayes
 3. Support Vector Classifier

As there are a few hyperparameters that require tuning, all 3 classifiers were optimised using GridSearchCV to find the best hyperparameter combination.

The below table summarises the performance of each model:

<img src="images/scores_df_styled.png" width="550" />


Generally speaking, the Logistic Regression models performed the best, followed by Support Vector Classifiers, then Multinomial Naive Bayes.

- Logistic Regression obtained the highest average accuracy and AUC scores
- Multinomial Naive Bayes achieved the highest recall scores
- Support Vector Classifier achieved the highest precision scores

In my case, since the classes in my dataset are balanced, the metrics that I  prioritise are accuracy and AUC score. Accuracy quantifies my model's ability to make correct predictions, whereas AUC quantifies the classifier's ability to separate the two classes, regardless of the threshold value.

Given that logistic regression had the best accuracy and AUC scores, it was selected as our final model. For the vectorizers, using the TFIDF Vectorizer gives us a higher AUC score than the Count Vectorizer. Thus, the final model will be **TfidfVectorizer + Logistic Regression**.


### Results from the best model

#### Top predictors

These word clouds show the top predictive words for the respective subreddits.

<img src="images/askwomenover30_most_predictive.png" width="450"/> <img src="images/askwomen_most_predictive.png" width="450" />

#### Misclassified posts

20% of the posts in our validation set (119 out of 591) were misclassified.

Looking at the documents that were misclassified, it seems that many of them were very short in length (less than 10 words) and and had generic content, i.e. they do not contain keywords that would allow the model to easily identify which subreddit they came from.


### Conclusion

Using a TfidfVectorizer + Logistic Regression classifier trained on title and post content allowed us to classify unlabelled posts into the correct subreddit with an 80% accuracy rate. This shows that there is a distinguishable difference in most of the posts from the two subreddits, although it is hard to infer from our top predictor words that they are differentiated by age group.

It is difficult to make the generalisation that there is a clear separation in the topics discussed by women above 30, given that different people move through life at different paces and not everyone within the same age group will share the same life stage and life events. Hence, what is relevant to r/AskWomenOver30 could also be very relevant to r/AskWomen.


### Limitations and future developments

- Despite the high accuracy of the model, the most predictive words for each subreddit do not give me meaningful insight about the topics that are discussed. If I want to gain more clarity about the topics, I could try doing topic modelling instead.


- For this analysis, we only have close to 1,000 documents to train the model with. To further improve our model's accuracy, I would need more content to expand the vocabulary associated with each subreddit. Next time, I could try using the PushShift API to collect more posts to train the model with.


- The analysis was only done on the title and content of a post. What could add value to the model would be to analyse the comments as well since the two subreddits analysed are heavily discussion-based. The responses provided by the members of the respective subreddits would likely give us more insight about them as opposed to the title and post content.


- The misclassification of posts could have been partially contributed by the short length of certain posts. With fewer terms in a document, it might be harder for the model to accurately predict the correct class based on only those few words. One possible exploration to make is to filter out documents that have less than _n_ words, e.g. 10 words.


- This time round, I did lemmatization of the words, but I could also try stemming the words to see how the results would be affected.


- There is imbalance in the member count and hence activity within each subreddit. As of 8 September 2020, `AskWomenOver30` only has 79.6k members whereas `AskWomen` has 1.3m members. There could be many women over 30 who are unaware of the existence of the `AskWomenOver30` subreddit and make their posts only on the `AskWomen` subreddit, and as a result there could be many posts on the `AskWomen` subreddit that would be more appropriate for the `AskWomenOver30` subreddit instead.


- The bag-of-words approach used does not allow for named entity recognition. Some word sequences may constitute proper names, such as the names of corporations, but these named entities will be transformed into meaningless words during the vectorization process. Next time, I could try using spaCy to do named entity recognition before vectorization.


### Final remarks

In spite of the limitations, the model performed very decently in separating the posts from the two subreddits. With more training and further fine-tuning, I believe the model can be deployed to do automatic post-sorting between r/AskWomen and r/AskWomenOver30.

### Code and resources used

- Python version: 3.7
- Packages: pandas, numpy, matplotlib, seaborn, sklearn, NLTK
