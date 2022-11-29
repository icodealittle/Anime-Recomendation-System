# Anime Recommendation System

## Part 1: Dataset

The data used in this experiment was collected from a Kaggle dataset of all the anime on MAL, which
was scraped from MAL public API. The original dataset includes MAL user information such as what
anime they have marked as watched, completed, currently watching, or dropped. It also includes
information on user ratings that score from 1 to 10. There is a separate dataset from the same Kaggle
repository that has general information about all the anime on MAL such as the title of the anime and
genre. This dataset was combined with the user dataset in numerous ways for each of the different data
mining techniques. This data was then preprocessed and cleaned for the various algorithms and matrices
transformations.

The MAL user dataset has been preprocessed and exported into separate, simpler datasets. Initially, the
user data contained 20 columns. However, the dataset was reduced to essential information for the
recommendation system with features such as user identification (user_id), watched anime identified by
mal_id, and its respective user-anime rating. The user-anime rating ranges from 1 to 10.

## Part 1.1: Data Pre-processing

The original dataset contained unnecessary metrics and mainly associated with one user, it was too parsed to achieve the table shown below. Since the original dataset is very large and too parsed, we created a subdataset that mainly consisted of user_id, mal_id, and rating.

   ![Screenshot 2022-11-29 at 1 49 02 PM](https://user-images.githubusercontent.com/55925207/204619486-2f7e0815-bb37-404b-a26a-ad3b9c47bac1.png)

Similar to the table above, we created another subdataset that consists of user favorites. Each user row
contained a column of “favorites”, which was contained in a dictionary of the user's favorite anime,
character, and people as keys and list of mal_id and anime title as values. The user_id, mal_id, and binary
indication of favorites were extracted from the original dataset. Whether the user indicates if a mal_id was
favorited was determined in a binary matter, 1 and 0, meaning favorited or not favorited respectively.

   ![Screenshot 2022-11-29 at 2 04 58 PM](https://user-images.githubusercontent.com/55925207/204622569-26be713f-8fb1-431d-ac5b-71def7ff3d7c.png)

Another data frame was created by concatenating the two subdataset and filling the empty favorited columns with 0. Since the favorites are
indicated using binary values, an assumption that all values not marked as 1 indicate 0, or not favorited. The table below combined data frame gives more data points since it has information about both
user ratings and favorites.

  ![Screenshot 2022-11-29 at 2 11 03 PM](https://user-images.githubusercontent.com/55925207/204623669-eefa0f6b-a712-4d72-890c-852707832f12.png)

## Part 2: Data Manipulation through Machine Learning Algorithms (Result)

## Part 2.1: Linear Regression

The predicted values were filled in place of the missing values to complete the original user rating dataset shown below based on user_id = 3

   ![Screenshot 2022-11-29 at 2 18 55 PM](https://user-images.githubusercontent.com/55925207/204625440-9d0ed9dc-67be-40b0-9c88-7a3b224ced3c.png)

## Part 2.2: K-Nearest Neighbors

The accuracy scores of K-nearest neighbor classifier test and training data were about 21% and 37%
respectively. Since the user data was not a symmetric data, this may not be the most accurate representation of the model’s performance. The weighted average recall of the test and training data was 0.22 and 0.37 for test and training data respectively. Finally, the weighted average F1 scores were 0.20
and 0.36 for test and training data respectively.

## Part 2.3: K-Mean Clustering

The recommendation system for K-Mean clustering was built using the same approach as the K-Nearest Neighbor method. Three datasets were merged together
to create a new dataset based on the corresponding mal_id with anime_data.csv, complete_user_rating.csv, and user_score_data.csv that specifically worked for the K-Mean recommendation system. Unlike other methods that were created, the output of the K-Mean recommendation system produced the user's most popular genres based on the information in the dataset.

## Part 2.4: Singular Value Decomposition

The SVD model with three latent variables has a RSME of 6.02. It was slightly smaller than the SVD
model with two latent variables. The range between the minimum and maximum of RSME values for the
dataset was 12.62. There was a large difference and variance between the RSME values. There was no
decreasing or increasing trend in relation to the increase of latent variables.

   ![Screenshot 2022-11-29 at 2 29 23 PM](https://user-images.githubusercontent.com/55925207/204629738-5b5c5f5d-9137-465b-98a7-4ceaa5053859.png)

## Part 2.5: Alternating Least Squares

The RSME for the best ALS model on our data was 1.74. It was calculated using PySpark’s ALS and CrossValidator classes.
   
   ![Screenshot 2022-11-29 at 2 30 10 PM](https://user-images.githubusercontent.com/55925207/204629873-0fc2505f-a564-4f15-b2d4-57a6e7c264de.png)

## Part 3: Conclusion

Four out of the six algorithms used in our project successfully recommended anime titles to users. One potential reason two of the algorithms were unsuccessful may be due to the sparsity of our data. 

In the future, a more unified approach to comparing algorithm performance would help with improving anime recommendation outputs and then can be incorporated into a combined recommendation system that uses multiple algorithms to develop one set of recommendations.
To address issues with the diversity of users’ genre tastes, different combinations of the algorithms from
this report could be used to find an improved recommendations output. For example, we could use
K-means to find a subset of anime that are from the most popular genres for a specific user and then use
18 that subset of anime to predict new animes a user would want to watch using either K-nearest neighbor or ALS

Overall majority of our data mining techniques were successful at recommending anime, and we hope to
improve on these analyses by gathering more data, implementing different collaborative filtering
algorithms and combining different data mining techniques.
