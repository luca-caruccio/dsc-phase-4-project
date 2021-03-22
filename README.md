
### Collaborative Movie Recommendation System for Auri+, a new streaming service


## Overview

This project will attempt use collaborative filtering to build a recommendation model for a new streaming service, Auri+. There will be two main focuses, item based and user based. First we created a list of recommendation based on a user's feeling regarding a certain movie. Auri+ will use this for new users, to recommend titles related to any movies they said they liked during the ign up process.

Secondly, and more importntly, we used a recommendation system that recommends movies based on similar users, who feel the same way about movies our existing user has already seen. Based on this, we can use ratings they have given to other movies hat our existing user has not seen, and recommend them based on their relationship to the movie in question.

## Business Problem(s)

Streaming services are now synonymous with the internet, most anyone who uses the internet has access to a streaming platform, albeit sometimes somebody elses. With so many platforms, the market for streaming has become oversaturated, and websites use recommendation systems to keep users interested. The problem, however, is that sometimes these recommendations aren't very good. Auri+ will hopefully use a different recommendation system, which weeds out films with lower than average ratings. 

## Data and Methods, Results

The data used for this recommendation system comes from the movieLens dataset, we will be using the "small" data set for the sake of simplicity and convenience.

This includes just over 100,000 movies, most of which are above the mean rating we are trying to beat.

After importing the data, we combine it while also dropping any unecessary columns, such as 'genre'. While genre might seem important at first glance, we are primarily measuring similarity across multiple users. So, if a user likes a certain genre, movies under that description will be grouped together anyways. 

After finding the average rating for a movie, we have our baseline, and can remove movies from the list that fall under the mean rating of 3.5.

After combining and restructuring the data, we create pivot tables to cross reference whether or not a user has rated a title (Values 1 or 'Nan'), which we can use to find correlation ratings across different films. With this, we create the first part of our recommender system, which simply finds similarly rated movies and groups the top choices based on the input of a single movie. For example, if we selected "Pulp Fiction", the top choices would be Reservoir Dogs, American Beauty, and Saving Private Ryan. 

Next we create a rather large dictionary, which contain the movies rated by each user, as well as another dictionary that contains the opposite, movies that were not rated by a user. We take our aforementioned pivot table, and replace the Nan values that would make rating and accuracy scores far less accurate.

After this we use the sklearn "NearestNeighbors" library to fit our pivot table using cosine similarity. This will be used to create our top movie recommendations for a user, which we do in our next function. We can also edit the number of recommendation if need be. Our outpout shows a user what they've already watched, and users that information to find users with simlar viewing histories, who gave high ratings to shows from our 'notrated' dictionary.


## Conclusions

We evaluated our model using RMSE (Root Mean Square Error) and MAE (Mean Absolute Error), and both fall within the normal range, ensuring us that our model is sound.

Based on this, there are three key recommendation to ensure this model works for our new streaming platform.

1. Have new users give examples of movies they like, so the model can present complimentary movies which should address the cold start problem.
2. incorporate a collaborative filtering system that can provide similar users new movies based on high ratings from users within their range, and relevant playlists for users based on this
3. Use users as the primary metric for recommendations. User based Collaborative filtering seems to be more essential than item based, however both are important.

## Future work

As far as future work goes, there's a lot we can do with this. We have found that we can edit recommendations based on rating floors or ceilings, but finding an ideal ratio would be very helpful. Additionally, adding movies that may have a high number of lower than average ratings could indicate a movie is still very popular, thus watchable. Lastly, though our model still managed to group similar movies together, we could use the rating[genre] column in the future to possibly recommend genres that have similar viewer patterns. This could keep users engaged with an entirely new set of movies, while also providing valuable ratings to further improve our model.

## For more information

Email: lfcaruccio@gmail.com
Github: luca-caruccio
Linkedin: Luca Caruccio

## Repository Structure

-Introduction and Overview

-Business Problems

-Data Methods, Results

-Conclusions

-Future Work and Next Steps

