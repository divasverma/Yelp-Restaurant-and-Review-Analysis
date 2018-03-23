# Yelp-Restaurant-and-Review-Analysis

The aim of the project is to analyze yelp restaurant analysis and gain some insight into the
feedback provided by customers. This analysis is then used to suggest restaurants to users
based on the city and the food item that the customer wishes to eat. A sentiment analysis is
also done on the reviews to see if the star rating given by a customer can be gaged
accurately by just analyzing the review. The Yelp API only provides three reviews for each
restaurant queried. This would have been too less for the given analysis. Hence data for
various businesses and their reviews was obtained from the Yelp academic database.
The first task is to clean the data as it contains the given data for businesses contains all
businesses like salons, garages, restaurant, etc. Each business has a given set of attributes,
which provide some indication as to what business it is. For example, restaurants will have
attributes like ‘RestaurantPrice Range’, ‘RestaurantsTableService’, etc. The attributes for
each business were scanned and only those businesses with attributes pertaining to
restaurant were added to the final dataset. All the data reading and data manipulation was
done using Pandas.

Once the data was cleaned some basic analysis and visualization was conducted. Most of the
restaurants had some category, like ‘Italian’ or ‘Mexican’ attached with it. Ten broad
categories of cuisine were chosen, the variety of cuisines, in the given data, in each state was
mapped using a heat map. A heat map of the number of restaurants in each state was also
plotted. This helped gain an idea of the regions given covered in the given data and the states
to concentrate on for better results. Further the dependence of average footfall in a restaurant
in any given state and the average star rating received my any restaurant across the state on
the day of the week was investigated. For all the states, the number average footfall
increased drastically over the weekend, especially on Saturday’s. The average rating, on the
other hand was more or less uniform. Thus, it cannot be said, generally, that an increase in
number of customers leads to poor service in a restaurant.

Next the reviews for each restaurant were analyzed. Each review was broken down into
sentences and POS tagging was used to tag each word in the sentence. The noun in each
sentence was added, if it already did not exist, to a dictionary of ‘qualities’ maintained for each
restaurant. The number positive and negative adjectives in each sentence was used to
increase or decrease the counter for the corresponding noun in the dictionary. The adjectives
were categorized as negative and positive using the list of positive and negative words from
ptrckprry.com. This way each restaurant had a dictionary of ‘qualities’ that kept a count of all
the nouns and how they were described in the reviews. The common and unrelated nouns
were deleted before tagging the sentences. Also, the nouns one after the other were
considered a single entity, as they may be dish names. This analysis was conducted for all
the restaurants in the database. A bigger dictionary, with keys as restaurant names and the
values being the dictionary of ‘qualities’ of each restaurant was generated. This was then
used for further analysis.
A function was defined that takes as input a food item and a city. For example, ‘pizza’ and
‘Las Vegas’. This function returns the five restaurants in the given city, Las Vegas, which
have the highest value for the given food item, pizza, in their dictionaries. This way the top
five pizza places in Las Vegas, based on Yelp reviews are chosen. A word cloud for each
restaurant is generated for the user so that the user can then decide which restaurant to visit
based on the other offerings of the place, which can be easily picked out from the word cloud.
Another function is defined that goes through the dictionaries of all the restaurants for a given
state, and return the highest valued ‘qualities’ after joining all these dictionaries. This way the
most valued ‘qualities’, by each state can be analyzed. It can be seen that service and staff
are recurring qualities across states, implying that these are the most valued qualities by
customers. Some food items like coffee also made an appearance on the list.

Since all customers have different ways of giving rating and reviews, and often the ratings do
not give a true depiction of the overall sentiment of a review, we analyzed the positive
sentiment in each of the reviews. This analysis is critical for restaurants to help them filter out
the highly positive and negative reviews to understand customer feedback and improve their
operations. Restaurants often display such text to increase their popularity and grab customer
attention. Hence, selecting highly positive reviews is critical for their marketing. Using text
mining libraries, the proportion of positive content in reviews was found and classifier based
on a threshold value was used to predict whether the review is positive or negative. Reviews
with more than three rating were considered positive and rest negative. The classifier
accuracy was evaluated for a range of threshold values and the threshold giving least error
was selected. The test sample accuracy was found out to be 86.8%. The analysis was done
only a subset of the reviews, since the entire dataset was too large to work with.
Next, SVM (Support Vector Machine) was used to predict the actual rating (1-5). The model
was again trained on a subset of the data due to large size of the reviews data. Here the
methodology of TF-IDF which normalizes the count of each word in each text by the number
of times that that word occurs in all of the texts was used to train the model. The SVM
accuracy when predicting the rating was 41.48%. Then the same approach in SVM was used
to predict whether the review is positive or negative (reviews with more than three rating were
considered positive and rest negative). In this case the prediction accuracy increased to 85%.
