
# Problem:

We need a way to differentiate posts between subreddits in order to accurately classify them.  To that end, the task at hand is to create a model that is able to differentiate posts between subreddits.  This can be done by scraping the data from reddit itself.  

# Method:

The method I used was multistep.  

1.  I extracted the data from two subreddits, nfl and baseball, in order to see how I can create a model to better differentiate posts between the subs.

2.  I then performed some EDA and pushed both datasets into one large dataset of 1815 rows.  

3.  I first ran two models, a logistic regression and a MN naive bayes, with count and tfid vectorized version of the posts titles from the subreddits.

4.  Not content with my results, I looked to flair text of the authors, since both subreddits have a high rate of flaired users.  

5.  Once again, ran a logistic and MNNB for cvec and tfid vectorizers.

6.  Analyzed the results of the flair models and made recommendations

# Data Dictionaty

This includes the data I focused on, the model, and the vector used.  The description is for the first mention of the data only.  Any null values were dropped.

|Data|Model|Vectorizer|Description|
|---|---|---|---|
|Title|MN Bayes|Cvec|Vectorized post titles|
|Title|MN Bayes|Tfid||
|Title|LogReg|Cvec||
|Title|Logreg|Tfid||
|Flair Text|MN Bayes|Cvec|Vectorized Author flair text for each post|
|Flair Text|MN Bayes|Tfid||
|Flair Text|LogReg|Cvec||
|Flair Text|Logreg|Tfid||


# Conclusion and Recommendation

The best way, conclusively, to sort reddit posts by subreddit is to include flair text in your scrape.  Because flairs are unique on a per subreddit basis, there is a low chance of overlap once flairs are included in analysis.  However, not all subs have flairs and not all users flair themselves.  I believe that a combination of titles and flairs will be enough to differentiate any two subreddits with at least a 90% success rate, based on my analysis of both titles and flairs.  
