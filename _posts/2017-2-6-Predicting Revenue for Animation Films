For the second project at Metis, I decided to build a model to predict gross revenue for animation films. 

The first step was to collect the data I needed. Using python package Beautiful Soup, I scraped data from IMDB.com for the top 400 gross animations films. Collecting data from a html page and turning them into workable was a challenging task. Fortunately, we learnt some basic elements of html to better understand how to retrieve data from a web page.

After obtaining the raw data, I spent a big chunk of my time doing data wrangling. Since everything from web scraping came in a string format, 
I dropped data with country outside of USA or release date earlier than 1990 to keep my model simple.
I converted the data into the appropriate data type. 
The awards information came in a format like “' Won 2 Oscars', ' Another 72 wins & 57 nominations’”. So I categorized them into ‘won’, ‘nominated’ and ‘not’ based on the keyword extracted from the descriptions. 
Based on the ranking of the movie’s production company’s total gross revenue, I categorized each movie’s production company into ‘large’, ‘medium’ and ‘small’. 
From the release date information, I extracted year, month, day, day of the week and date ordinal. Date ordinal is a count that increment by one as each day goes by. This way, I can use it as a variance to capture the effect of time in my model.
Lastly, I filled the 16 data points with missing value with the median.

Then, I took a look at the distribution of my variables to make sure that there is no unusual trend that might violate the assumption for linear regression. I soon discovered that release date ordinal has a skewed distribution, since there are more animation movies release recently. In order to turn it into something closer to a normal distribution, I applied a Box-Cox transformation and the data demonstrated less skewness after transformation.

After conducting feature engineering and checking for assumptions, I ran simple linear regression models to find out what variables are significant. The best predictor with significance at 90% confidence level turned out to be opening weekend, rating score, release date ordinal, awards results and production company size.

 To avoid overfitting, I split my data into test and training set and compared the model performance of cross validated Lasso, Rigid and Elastic Net models. Elastic Net model produced the lowest mean squared error, with an alpha level of 0.17 and R squared of 0.878. The final equation of my model is below:

96 + 62 ∗ Opening Weekend + 14 ∗ Rating Score + 0.0 ∗ Release Date Ordinal + 4 ∗ Nominated + 42 ∗ Won + 21 ∗ Large − 23 ∗ Small

Since I normalized my numeric variables to apply the regularization earlier, they are not in the original unit anymore. The equation tells us: 


the baseline of gross revenue is 96 million
with 1 unit increase in opening weekend revenue, gross revenue increases by 62 million
with 1 unit increase in IMDB rating score, gross revenue increases by 14 million
with 1 unit increase in release date ordinal, gross revenue increases by a small positive amount
compared to movies that did not win or get nominated for awards, being nominated for an award increases gross revenue by 4 million and winning an award increases gross revenue by 42 million
Compared to medium size production company, large size production company increases the movie’s gross revenue by 21 million and small size production company decreases the movie’s gross revenue by 23 million

Finally, I will test out how my model holds against a real life example. For the Disney movie Inside Out, my model predicted the gross revenue to be 340 million, and the actual gross revenue is 356 million. Pretty close!
