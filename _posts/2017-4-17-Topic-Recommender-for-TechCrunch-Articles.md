After learning about supervised machine learning such as regression and classification at Metis, we jumped into the unknown realm of unsupervised machine learning, where there is no clear defined target for us to predict. Two big topics in unsupervised learning are Clustering and Natural Language Processing (NLP). For my fourth at Metis, I attempted to tackle both of them through exploring text data from TechCrunch posts.

My dataset contain 40,000 post and their related information such as author, category, and date from 2010 to 2016. 

First, I decided that the goal of my project is to create a topic recommendation system so that when users type in a topic they are interested in on TechCrunch, they will see recommended topics that are similar. The list of topics come from the ‘tag’ variable from my dataset, which includes topics like facebook, twitter, htc, and airbnb.

Before the fun part of creating a recommendation system, I had to process the text data into a format that’s easy to work with. I removed the punctuations since they don’t really provide much value for NLP purpose. Then, I removed the stop words, which are words that are used so frequently (such as ‘the’) that we can ignore them. Additionally, I applied a technique called ‘stemming’, which reduce words to their root form so they are treated as the same. For example, ‘users’ would be reduced to ‘user’. Lastly, I compiled the process article texts for each topic into one long string, so I ended up with 50 strings as my data.

In order to build the recommendation system, I created a TF-IDF matrix for each topic, which shows the TF-IDF values for every word appearing in each topic. TF-IDF stands for term frequency - inverse document frequency and it is a statistics that demonstrates how important a word is in a given document. 

However, in the TF-IDF matrix each topic contains around 8,000 unique words, meaning that the matrix is be extremely sparse with around 8,000 variables stored as columns. A big challenge with sparse matrix is curse of dimensionality - as dimensionality increases, space grows exponentially and data points become so far away that being close to one another become almost meaningless. To combat this problem, I applied a dimensionality reduction technique called Principal Component Analysis (PCA) to create 3 components that capture a large portion of the variance in the data. Having only 3 components also mean that I can graph my data points in 3D space.

At Metis, we learnt a great deal about clustering methods such as K-Means Clustering, DBSCAN, and Hierarchical Agglomerative Clustering. So I couldn’t wait to try out them out on my TechCrunch dataset. However, the results turned out to be less than idea. The best silhouette score (a measurement for how close points are to their own clusters) I could achieve was 40%. Why was this happening?

Luckily, since my data was transformed into 3 components, I can visualize my data points in 3-D graph (shown below). 

As shown in the graph, there really isn’t some clear patterns of clustering going on. The data points are all pretty close, possibly because they are all about technology. 

So instead of applying a clustering techniques, I decided to use a simple rule to recommend topics - when user inputs a topic they like, I will recommend the 3 closest topics based on euclidean distance.

Despite the simpleness, the method worked pretty well on the 50 topics. A couple of examples:

1. User types ‘HTC’: BlackBerry, Nokia, and Iphone are recommended
2. User types ‘Facebook’: Facebook-Messenger, Facebook-Ipo and Facebook-Whatsapp are recommended
3. User types ‘Twitter’: Jack-Dorsey, Vine, and Twitter-Vine are recommended
4. User types ‘Tesla’: Windows-10, FlipBoard, and Raspberry-Pi are recommended

Obviously, there are some constraints on this recommendation system. For instance, since there aren’t a lot of topics similar to Tesla in my dataset, Windows-10 is the closest topic recommended which is probably not what the user wanted to see. However, as demonstrated by other examples, the method worked well for most cases.

Finally, I also created a simple interactive interface where user can type in the topic keyword and get 3 recommended topics using Flask. 

You can find my codes and presentation for this project here.


