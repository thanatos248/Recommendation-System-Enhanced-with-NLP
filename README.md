# Recommendation System Enhanced with NLP
In this project, a system is proposed which would take tag movies with emotions based on emotional response of users by analyzing movie reviews. The emotions will be used in addition to genres to predict the rating by the user. MovieLens dataset also has tags which are keywords extracted from some reviews which will be used to predict rating a user might give the moviel. The two rating sytems will be combined using polynomial regression to get a final output. Based on a threshold of the rating the movie will be categorized into Like/Dislike. The like movies are the movies which the user might like and should be recommended dislike are the movies the user might not like.

## Datasets
- [Figure Eight Labelled Textual Dataset](https://www.kaggle.com/datasets/manuelbenedicto/figure-eight-labelled-textual-dataset)
- [Large Movie Review Dataset](https://aclanthology.org/P11-1015/)
- [MovieLens 25M Dataset](https://grouplens.org/datasets/movielens/25m/)

## Proposed System Diagram
![System Diagram](System_Diag.jpeg?raw=true)

## Proposed System Details

### Emotion Recognition Model
The model being used for Emotion Recognition will be decided after comparing 3 separate models namelu a LSTM model, a LSTM model with Glove word embedding and Robert model. The best performing model will then be chosen and the model will be used in the subsequent steps.
![Emotion Detection Model](Emotion_Recognition.png?raw=true)

### Emotion based Movie Tagging
Large Movie Review Dataset is a very popular dataset for binary sentiment classification.  The dataset contains imdb reviews for a lot of movies and even contains multiple reviews for a single movie. The dataset however, does not contain emotional tagging of the reviews.

For this reason we had to make use of Figure Eight Labelled Textual Dataset. The model trained and selected on that dataset during the Emotion Recognition Model module will be utilized in this module. Using the trained model we will identify the emotion being expressed in each review.

The model will return in terms of percentage how much of which emotion is being expressed in the review. We will perform averaging in case of multiple reviews of a single movie.
After averaging, the predominant emotion will be chosen as the emotional tag for the movie. After tagging the movies, the file will be stored for further use in subsequent modules.

### Movie Recommendation Model
This project employs a projected rating-based recommendation model. Two different rating predictors are utilised, one of which uses a mix of genres from the MovieLens dataset and the emotions tagged movies dataset to estimate what rating a user will give the film. Another rating predictor is utilised, which makes use of tags assigned to movies by users. After then, regression is used to combine the two to get a final rating estimate for each movie by a specific user. The movies are then divided into two categories: Like and Dislike, with Like being the movies that should be recommended to the user because he might enjoy them.
![Recommendation Model](Recommendation_Model.png?raw=true)
