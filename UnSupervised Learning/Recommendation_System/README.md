# RECOMMENDATION SYSTEM
# INTRODUCTION TO RECOMMENDATION SYSTEM
* A **recommender system** or a **recommendation system** is a subclass of information filtering system that seeks to predict the "rating" or "preference" a user would give to an item.
* A recommendation engine filters the data using different algorithms and recommends the most relevant items to users. It first captures the past behavior of a customer and based on that, recommends products which the users might be likely to buy.
* They are primarily used in commercial applications.
* **Example**:
  - playlist generators for video and music services like Netflix, YouTube and Spotify
  - product recommenders for services such as Amazon
  - content recommenders for social media platforms such as Facebook and Twitter.
# HOW DOES RECOMMENDATION SYSTEM WORKS
* Data Collection
* Data Storage
* Filltering the Data
  - Content based Filtering
  - Collabarative Filtering
<p align="center">
  <img src="https://github.com/Naga-kalyan/Machine_Learning/blob/master/UnSupervised%20Learning/Recommendation_System/Img/filtering.png"/></p>

# COLLABORATIVE FILTERING
* Collaborative filtering systems make recommendations based on historic users preference for items (clicked, watched, urchased, liked, rated, etc.).
* The preference can be presented as a user-item matrix.
<p align="center">
  <img src="https://github.com/Naga-kalyan/Machine_Learning/blob/master/UnSupervised%20Learning/Recommendation_System/Img/colabrative.png" width="200px" height="150px"/></p>

* Here is an example of a matrix describing the preference of 4 users on 5 items, where P12, is the user 1’s preference on item 2.
* The entries can be numeric like rating from 1-5, or binary like clicked, watched etc.
* In reality, the user-item matrix can be more than millions * millions (EX. Amazon, Youtube), and the majority of entries are missing.
<p align="center">
  <img src="https://github.com/Naga-kalyan/Machine_Learning/blob/master/UnSupervised%20Learning/Recommendation_System/Img/collabarative_matrix-1.png" width="200px" height="150px"/></p>
  
* The goal of recommender systems is to fill those missing entries.
* Collaborative-filtering-related approaches are:
  - nearest-neighbor
  - creating a new latent space using
  - matrix factorization
  - deep learning.
# NEAREST-NEIGHBOR
* Nearest-neighbor-based methods are based on the similarity between pairs of items or users.
* Cosine similarity is often used for measuring the distance:
<p align="center">
  <img src="https://github.com/Naga-kalyan/Machine_Learning/blob/master/UnSupervised%20Learning/Recommendation_System/Img/1.png"/></p>
  
* The preference matrix can be represented as item vectors:
<p align="center">
  <img src="https://github.com/Naga-kalyan/Machine_Learning/blob/master/UnSupervised%20Learning/Recommendation_System/Img/2.png"/></p>
  
* The similarity between item I1 and item I2 is calculated as cos(I1,I2).
* The matrix can also be represented as user vectors:
<p align="center">
  <img src="https://github.com/Naga-kalyan/Machine_Learning/blob/master/UnSupervised%20Learning/Recommendation_System/Img/3.png"/></p>
  
* The similarity between U1 and U2 is calculated as cos(U1,U2).
* Note that, the missing values in the preference matrix are commonly filled with zeros.
* For user_i, we can recommend the items liked by user_i’s most similar users (user-to-user) or the most similar items of user_i’s liked items (item-to-item).
# ASSOCIATION RULES (APRIORI ALGORITHM) 
* Association Rules is one of the very important concepts of machine learning being used in market basket analysis.
* In a store, all vegetables are placed in the same aisle, all dairy items are placed together and cosmetics form another set of such groups.
* Investing time and resources on deliberate product placements like this not only reduces a customer’s shopping time, but also reminds the customer of what relevant items (s)he might be interested in buying, thus helping stores cross-sell in the process.
* Association rules help uncover all such relationships between items from huge databases.
* Various metrics used to understand the strength of association between these two itemsets are:

___

* **Support**: an idea of how frequent an itemset is in all the transactions.
<p align="center">
  <img src="https://github.com/Naga-kalyan/Machine_Learning/blob/master/UnSupervised%20Learning/Recommendation_System/Img/4.png"/></p>

* Value of support helps us identify the rules worth considering for further analysis.
* For example, one might want to consider only the itemsets which occur at least 50 times out of a total of 10,000 transactions i.e. support = 0.005.

___

* **Confidence**: defines the likeliness of occurrence of Y on the cart given that the cart already has the X.
<p align="center">
  <img src="https://github.com/Naga-kalyan/Machine_Learning/blob/master/UnSupervised%20Learning/Recommendation_System/Img/5.png"/></p>
  
* That is, confidence is the conditional probability of occurrence of consequent given the antecedent.
* Consider the numbers from figure given here.
<p align="center">
  <img src="https://github.com/Naga-kalyan/Machine_Learning/blob/master/UnSupervised%20Learning/Recommendation_System/Img/6.png"/></p>
  
Confidence for {Toothbrush} — {Milk} will be 10/(10+4) = 0.7143
* Looks like a high confidence value. But we know intuitively that these two products have a weak association and there is something misleading about this high confidence value. Lift is introduced to overcome this challenge.

___

* **Lift:** Lift controls for the support (frequency) of consequent while calculating the conditional probability of occurrence of {Y} given {X}.
<p align="center">
  <img src="https://github.com/Naga-kalyan/Machine_Learning/blob/master/UnSupervised%20Learning/Recommendation_System/Img/7.png"/></p>
  
* If lift is greater than 1, then it means that {X} actually leads to {Y} on the cart.
* Consider the previous example of the {Toothbrush} — {Milk} rule.
* Probability of having milk on the cart with the knowledge that toothbrush is present (i.e. confidence) : 10/(10+4) = 0.7143
* Probability of having milk on the cart without any knowledge about toothbrush: 80/100 = 0.8
* These numbers show that having toothbrush on the cart actually reduces the probability of having milk on the cart to 0.7143 from 0.8.
* This will be a lift of 0.7143/0.8 = 0.8929.

# APRIORI ALGORITHM
* Let k=1
* Generate frequent itemsets of length 1
* Repeat until no new frequent itemsets are identified
  * Generate length (k+1) candidate itemsets from length k frequent itemsets
  * Prune candidate itemsets containing subsets of length k that are infrequent
  * Count the support of each candidate by scanning the DB
  * Eliminate candidates that are infrequent, leaving only those that are frequent
* **Creating Association Rules**:
  * If Lis the frequent item-set (after applying min_sup rule), then each combination of subsets S of | are considered.
  * A Rule is written as — **S ⮕ I-S**
  * The rules which satisfy min_conf are considered as Association Rules.
