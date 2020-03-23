# Project 3: Web APIs & NLP

Author: Julie Vovchenko


## Content:
- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)
- [Next Steps](#Next-Steps)
- [References](#References)

## Dataset:
- [Scraped Raw Data from Both Subreddits](../data/both_scraped_subreddits.csv)


### Problem Statement
As part of psychological research done by Memorial Sloan Kettering, we were asked to create a predictive model that identifies whether certain posts on reddit.com are created in “Parenting: For those of us with kids of any age” or 'stepparents: For people raising other people's people' subreddits. In addition, we would need to determine specific words suggesting the group posting them. 

By using dataset scraped from reddit.com, we plan to use two models: LogisticRegression (LR) and Multinomial Naive Bayes (MNB) to classify whether a post is from subreddit 'Parenting' or 'stepparenting' (binary classification). These models can assist psychologists in identifying proper subreddit for a post published by a parent/stepparent. We will use accuracy scores to choose our best model.
 

### Executive Summary
The First notebook 1_code_scraping.ipynb begins by assigning the name of the subreddits, scraping the data from reddit.com and saving raw dataset into the data file both_scraped_subreddits.csv. We were able to collect around 5,000 posts that we believe is sufficient for the project. Once cleaned, we concatenated title and body of each post together in a new separate column. This was done in an effort to utilize maximum data from each post. 

Since our dependent variable, subreddits, are catgorical (r/parenting or r/stepparents), we can fit data into several classifiers, including LogisticRegression (with Count and Tfidf Vectorizers) and Multinomial Naive Bayes (with CountVectorizer transformer). We complemented these classifiers with some necessary hyperparameters in order to select the best classifier, based on accuracy. 

In comparisson with our baseline accuracy (50%) all of our complex models performed much better.  
Based on our models accuracy scores, we decided to choose TfidVectorizer and Logistic Regression model as our best model for predictions with strong Train(94%) and Test(92%) Accuracy scores.  


### Conclusion and Recommendations
Using Push shift's API we have successfully collected data from two of the subreddits r/Parenting and r/stepparents. During the EDA we noticed that both groups were mostly active on reddit.com on Mondays and Tuesdays, which could be beneficial to the psychological research. Also, most pressing issues that parents discussed in 'parenting' subreddit were: 'what are the things that no one told you before having kids' and 'does anyone regret having # of kids they have' in 'parenting' subreddit.  
On the other hand, members of 'stepparenting' group mostly discuss 'so demanding to love kids the same as your own' and 'if you had to do it over again, would you'. 

All the models we have trained outperformed the Base Line model. The following are the accuracy scores of our three models:

| Vectorizer     | Classifier | Train Score | Test Score |
|------------|------------|-------------|------------|
|            | Base Line  | 0.50        |       0.50     |
| CountVectorizer | LogisticRegression| 0.94        | 0.89       |
| **TfidfVectorizer**   | **LogisticRegression**| **0.94**        | **0.92**       |
| CountVectorizer      | MultinomialNB| 0.90       | 0.90      |
| TfidfVectorizer      | GaussianNB| 0.88      | 0.88      |


Even though our Logistic Regression model trained on TfidfVectorizer performed slightly better than other models, it appears there is still room for improvement in the accuracy. The present model is also slightly overfit. We noticed that our model has limitations. It seems that most users in each subreddit are using the reddit.com as a tool to express their concerns or worries; therefore, most posts have negative connotations. As a result, the model is most effective with the posts where issues, concerns and challenges are discussed. 

Since we have only collected a sample, about 5,000 posts for both subreddits the coefficients interpretations are used for generalization of the population (all posts ever published in reddit.com) Words that mostly help to identify a subreddits were 'my year', 'old', 'toddler', 'my daughter', 'my kid' for 'parenting' subreddit, and 'bm', 'sd', 'step', 'hcbm', 'my so' for 'stepparents' subreddit. 


### Next Steps
As a next step, additional words should be included into our stop-word-list to enable computing **3 or 4-gram words to visualize in depth language patterns**. By doing this, we can optimize our classification matrix: minimizing False Positive and False Negative, and maximize accuracy score.  
We may also consider collecting more data from reddit.com for all the posts written **1-2 years prior to our current collection sample**. 6 months could limit to our model from some other aspects of parents life that could occur during other half of the year.  
We plan to use other sources for additional data: facebook, twitter that might have more subjects discussed between parents and step-parents.  
Also, **different cultures have different angles of parents lives**, therefore collecting more data from different languages is appropriate. 
Implementing additional models like **Decision Trees and Random Forests** for potential optimization of classification matrix.

### References

www.reddit.com