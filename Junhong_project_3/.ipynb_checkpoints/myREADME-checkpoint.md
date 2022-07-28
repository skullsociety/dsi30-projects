# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Web APIs & NLP

# Introduction:

We are a data science team working in Sing Song Cellar, specialising in investing and trade in rum and whiskey. Based on concerns and feedbacks from company shareholders, we are tasked to create a classification model to identify either rum or whiskey is worth purchasing.  
  
# Problem statement  
  
Sing Song Cellar requests the creation of a machine learning-based algorithm to identify the ways they can maximize the efficiency of their marketing spend based on their target audience.  
Management had asked us to survey whether rum or whiskey is worth investing and buying in.   
  
# Executive Summary:  
  
Sing Song cellar is a international alcohol dealer that is known world wide for it's quality of alcohol sold to their distributors. We have got customers in every end of the world and we are the first company that is able to ship/air drop our consumer's favourite alcoholic beverages in any part of the world at a affordable cost.  
  
As a coorperation, We should focus on maximizing profits and revenue with the limited resources we have. We should focus on increasing revenue, cost cutting and keeping consumers satisfied with our product and services at any time. As you know, our resources are not infinite and we have to best ultilize every dollar invested by our investors into achieving this goal.  
  
By building a classification model to classify new posts to whiskey and rum, we can identify whichever have higher popularity among the consumers, limited to the users of subreddit. By gaining such insights and knowledge, we would be able to tweek parameters or add a bot to further find out about the brands and models consumers would prefer and we will be assured that our following months of revenue would skyrocket and leave competitors far behind.  
  
Our team have got the most experienced data scientist with several of them with very outstanding achievements. We would scrape the data off subreddit and analyise them via different models and would construct and run the model for future subreddit posts. We have done many similar projects that have previously allowed our company to reach the position they are in the global market. We have became a pillar of economy in the global alcohol trade.  
  
We love to make our company dream a reality. Revenue and profits to the moon without compromising on quality service and high satisfection and approval rates from our consumers.  
  
The proposal outlines in more detail how we would do it and what you can expect along the way. Your biggest expectation should be one of success. Lets make it happen, lets get our products in every table of alcoholics around the world.  
  
## Results and insights  
  
There are 8/3083 whiskey posts (0.2%) that are misclassfied as rum and there are 53/2612 rum posts (2.0%) that are misclassified as whiskey post. It is also observed that the words rum and whiskey are the dominant words that helps the model to classify and predict that the post is classfied under either whiskey or rum respectively. Common words between both topic such as, get, really, good, looking, bottles is also rated highly in these posts.

It is observed that misclassified whiskey posts consist of a lot of the words 'rum' and 'whiskey' and all misclassified rum posts consist of a lot of the words 'rums' and 'bottle'  
  
| Model | Train Score | Test Score | AUC Score |
| --- | --- | --- | --- |
| Bernoulli Naive Bayes (TfidfVectorizer) | 0.54 | 0.54 | - |
| Bernoulli Naive Bayes (CountVectorizer)| 0.88 | 0.86 | - |
| Multinomial Bayes (CountVectorizer) | 0.88 | 0.86 | - |
| Multinomial Bayes (TF-IDFVectorizer) | 0.98 | 0.95 | 0.95 |
| Gaussian Naive Bayes (CountVectorizer) | 0.88 | 0.86 | - |
| Gaussian Naive Bayes (TfidfVectorizer)| 0.98 | 0.80 | - |
| Logistic Regression (TF-IDFVectorizer) | 0.99 | 0.96 | 0.99 |
| KNeighborsClassifier (TF-IDFVectorizer) | 0.94 | 0.89 | 0.94 |
| Hypertuned KNeighborsClassifier (TF-IDFVectorizer) | 0.89 | 0.88 | 0.95 |
  
Based on the train, test and AUC scores, the TF-IDF Vectorized Multinomial Bayes is the best performing model. This indicates that it will be a good and accurate model at classifying the new post. The reason why Multinomial Bayes seems like the best model despite the equivalent test and AUC scores is because the train score for LogReg is 0.99 indicating that there might be overfitting As a result, the findings cannot be well-generalised to unseen data/posts. However, if sample size were to tend to infinity (i.e. very large datasets), Logistic Regression might be a better choice assuming the problem is still a binary classification problem.  
  
Nonethless the 0.95 AUC score for both the Multinomial Bayes and 0.99 for Logistic Regression indicate that they are both well suited to predict which subreddit a post comes from. 

As for KNN, There is a slight improvement in the AUC score once both the Vectorizer and model are hypertuned. Train score dropped, less overfitting as compared to the un-hypertuned model. While it is still not the best predictor for whether a post belongs to a specific subreddit, it gives us insight into how hyperparameter tuning can could decrease overfitting of a model to our data. 
  
Our model performed at 95% as compared to the baseline, machine learning is effective in classification of subreddit text posts.  
  
  
## Future Improvements  
  
We could improve the accuracy of predictions by trying and explore a more diverse range of models including but not limited to Random Forests Classifier, Ensemble Techniques, SVM, GLM in order to get better scores. 
  
Lemmetization did not reduce words to the similar root word. For example, 'go' and 'going' were both present in the word cloud and we may want to consider employ stemming during the pre-processing phase.  
  
Due to a shortage of time, only one model was improved upon, but in future reiterations of this project, it might be best to hypertune both the models and Vectorizers for all models being used so as to optimize their fit and prevent over and/or underfitting of data.  
  
When comparing the top words for both subreddits, similar words such as 'really', 'get' appeared for both and it would be worthwhile excluding them as stopwords as they may be unlikely to help in classification.  
  
Our model is also limited to whiskey and rum subreddit. It may be worth considering and exploring other related subreddits that may be able to better make predictions. We can also train our model with more data to be able to be able to increase the accuracy for rum.  
  
We may also web scrap data from other popular platforms such as facebook and twiter to obtain a wider range of data, instead of limiting to subreddit users.  
  
## Conclusion  
  
The Multinomial NB model was able to accurately classify 95% of the posts according to the subreddit and hence the model can be deployed for use. The model can also be deployed on more unseen posts to further validate its accuracy.  
  
By using the model, we can further classify the subreddit to either rum or whiskey to identify the preference and popularity of either alcohol. Future data could be used for training the model to better predict if the post is from rum or whiskey subreddit.  








