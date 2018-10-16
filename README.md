###### Run above in https://nbviewer.jupyter.org/github/danturti/Reddit_Classification_Modelling_and_Web_Scraping/tree/master/ - for rendering jupyter notebook(.ipynb) if it fails to render

# Reddit_Classification_Modelling_and_Web_Scraping - Naive Bayes model Added to Update

In this project, I analyzed and evaluated Reddit's API for predicting a particular subreddit based of text titles/text posts in a given thread. 

The problem is a binary classification of two subreddits - 

1.fakehistoryporn 2.NatureIsFuckingLit 

To solve the problem, my workflow included three parts:

Webscraping: 

Use requests and json packages to scarpe the above 2 subreddits.

NLP and Modelling: 

Build classification models that are possible to interpret the importance of text(key word) features (e.g. KNN can’t be used) and choose one with a highest test score of accuracy. Inferences: Analyze the result of features (coefficient / key word importance) and find the most important key words that can be used to correctly classify a sub-reddit post and successfully predict a future subreddit post.

Here are some findings I got from the classification modeling and the natural language processing:

Comparing the TFIDF Vectorizer and Count vectorizer, the TFIDF Vectorizer performs better for the feature dataset which comprises of the title and selftext. Count Vectorizer simply counts the number of times a token shows up in the document and uses this value as its weight. TFIDF Vectorizer ensures that the weight assigned to each token not only depends on its frequency in a document but also how recurrent that term is in the entire corpus. This is key in removing function words like pronouns which are very common in an opinionated(comment-based) website like Reddit and which should not be a token of high weightage and hence should be weighted down in TFIDF. HashingVectorizer and CountVectorizer return identical results. The difference between HV and CV is that HV does not store the names of features (and thus is more memory efficient) whereas CV keeps the names of features.Hence, HashingVectorizer was not used.

Key fakehistoryporn tokens include: colorized, circa, 1944, ad, hitler, bc, 1943, american, battle, german, nazi, 1939, 1968, soldier, roman, president, army 

Key NatureIsFuckingLit tokens include: shark, park, kingfisher, iceland, lightning, coast, crab, turtle, wasp, fish, owl, caterpillar, dragonfly, octopus, bird,
rainbow, nature, sunset, baby, spider, tree, beautiful

The above makes perfect sense for classifying our data accurately.

3 classification models were used for evaluation of the corpus. The Logistic , Random Forest, SVM

The Logistic approach we get coefficients that estimate how our independent variables(text features) affect our dependent variable(correct subreddit). It therefore is a very good model to use because the dataset is not very big and the model is not being overwhelmed by many features. The Random Forests model which is a bagging method involving an ensemble of trees is also used for this problem. It performs with very reasonable accuracy by estimating an accurate model by shuffling through the text feature. Using SVM, every text in our dataset is represented as a vector with thousands of dimensions, every one representing the frequency one of the words of the text. It works very well as our dataset is not very robust.The high dimensional features space means it is great model for avoiding overfitting.

The Logistic and SVM with TFIDF Vectorizer are our best performers with the highest accuracy of post and subreddit classification - nearly 96% accuracy.

Further explorations should incorporate using: A boosting algorithm for classification like Gradient or Ada Boost. Using n-grams to find a phrase instead of a word token for more accurate classification. Collecting more data and grow the corpus and reevaluate the performance of the models especially the performance of the ensemble of trees(bagging and boosting).


