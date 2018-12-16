# IBM-Watson-Recommendations
Recommendations algorithms for IBM Watson articles repository

### Table of Contents

1. [Installation](#installation)
2. [Project Motivation](#motivation)
3. [File Descriptions](#files)
4. [Results](#results)
5. [Licensing, Authors, and Acknowledgements](#licensing)

## Installation <a name="installation"></a>
The code in this project is written in Python 3.6.6 :: Anaconda custom (64-bit).
The following additional libraries have been used:
- sklearn to compute accuracy and other metrics metrics
- matplotlib for visualizations
- nltk to implement the content based recommendation algorithm

## Project Motivation<a name="motivation"></a>
This projects implements a recommendation system for the IBM Boston articles dataset.
- a Rank-based Recommendation system: it returns the articles ranked by number of interactiins, with the most popular at the top. This algorithm is very useful in case of 'Cold Start" problem, when recommending articles to new users
- a Collaborative filtering algorithms for recommendations to users based on users similarity. A dor-product metric is used to compute user similarity and when users have the same similarity score the ones that have the most total article interactions are chosen. Also when choosing articles to recommend the ones with the most total interactions are selected before those with fewer total interactions. 
- a Content-based recommendation algorithm based on similarities between articles. The similarity is computed using NLTK techniques like Bag of words and TF/IDF to parse the article title.
- a Matrix Factorization recommendation system that uses Singular Value Decomposition to predict interactions between users and articles.

## File Descriptions <a name="files"></a>
The Jupyter notebooks included in this project are:
- Recommendations_with_IBM.html, with the code for the recommendation systems described above.

## Results<a name="results"></a>
The Collaborative filtering algorithm has  showed it can make at least 10 predictions even for user with only one interaction , especially in the modified version that chooses the users that have the most total article interactions before choosing those with fewer article interactions and chooses articles with the articles with the most total interactions before choosing those with fewer total interactions. This can eventually be integrated with the algorithm that captures similarities between articles, although the risk here is that the user could be become bored if he gets recommended items that are too similar to each other. I would use this one only in case the collaborative filtering algorithm doesn't give enough results.
The Matrix Factorization algorithm has not given satisfactory results, with am F1 score much lower for the test set compoared to the training set, reaching the best values around 100 latent features and beyond that the model just overfits the training data. If we look at precision and recall separately, we reach the same conclusion. A 0.549 recall means that out of 218 interactions in the test dataset the algorithm can predict only 120 of them, while 0.56 precsion means that only over half of the interactions predictions are correct. That doesn't give us the confidence we can make good predictions, so I would not consider this method here to make predictions in this case.

