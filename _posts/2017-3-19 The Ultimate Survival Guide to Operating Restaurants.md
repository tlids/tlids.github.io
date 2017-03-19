I am a big foodie who is always down to try new cuisines, so I decided to focus on food for the third project at Metis. Using classification machine learning algorithm, I tried to answer the question “how can we predict the successfulness a restaurant?”

As always, the first challenge is to find a dataset that has the information I need to build a good model. My first thought was to utilize Yelp’s API, however, Yelp has an access limit of 1000 so I could not get more than 1000 data points from their API. Luckily, Yelp published a comprehensive dataset for a challenge they host (https://www.yelp.com/dataset_challenge). Specifically, I used the business dataset which originally came in a json file and limited my criteria to restaurants in Las Vegas.

To get the raw json file into a dataframe that I can easily work with, I spent a big chunk of my time doing data munging. For example, the variable ‘attribute’ from the Json file is an array of strings where each array element is an attribute. (See example below) I wrote functions in Python to extract the elements and turned them into columns of binary values. For instance, each restaurant is categorized into ‘Alcohol’ = 1, meaning the restaurant provides alcohol, and ‘Alcohol’ = 0, meaning otherwise. Additionally, I had to make some executive decisions about how to fill in the missing values.

The Yelp dataset has a binary variable ‘is_open’: 1 if the restaurant is open and 0 if the restaurant is closed. Out of the 5,431 data points, about 30% of them are closed. I decided to use this as a proxy of the successfulness of a restaurant. Even though a lot of restaurant close down for reasons other than restaurant not being successful, such as change of career, it is very likely that unsuccessful restaurants would close. 

I used the following numeric features to predict if the restaurant is open: 
* Review count
* Yelp star
* Price range

And the following categorical features:
* Type of Meal (Dessert, late night, lunch, dinner, breakfast)
* Is downtown
* Good for groups
* Take out
* Good for kids
* Attire is casual
* Takes reservation
* Has outdoor seating
* Offers delivery
* Has alcohol
* Has TV
* Noisy
* Wifi (No, Free, Paid)
* Ambience is casual
* Restaurant categories (Nightlife, bar, fast food, Mexican, Chinese, Sandwiches, Seafood, etc)

Alright, onto the fun part of modeling! To evaluate my models, I splitted my scaled data into a train set and a test set so I could try my model on the test set data and compare the accuracy score of different algorithms. 

At Metis, we learnt a whole lot about classification algorithms, so after I tuned parameter tuning using GridSearch from sklearn, I compared the accuracy score Logistic Regression,  K Nearest Neighbors, Gaussian and Bernoulli Naive Bayes, Support Vector Machine, Decision Tree, and Random Forest. Logistic Regression with L1 regulation produced the best result, followed by K Nearest Neighbors and Support Vector Machine.

To further improve the performance of my classifier, I applied an ensemble method called voting classifier, where the prediction of each data point is produced by winner of the majority vote from my three top algorithms. At the end, my classification model significantly outperformed the dummy classifier with 14% increase in accuracy and 21% increase in recall. (See below)
