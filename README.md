# Movie Recommendation Engine

A Python-based movie recommendation system built from scratch using Collaborative Filtering and the K-Nearest Neighbors (KNN) algorithm. This project predicts and suggests movies for a user based on the viewing history and ratings of similar users.

## Dataset
This project uses the **MovieLens dataset**, which contains:
* 100,004 ratings across 9,125 movies.
* 671 users (all selected users have rated at least 20 movies).
* Relevant files: `movies.csv` (contains `movieId` and `title`) and `ratings.csv` (contains `userId`, `movieId`, and `rating`).

## Methodology
The recommendation engine is built entirely from scratch without relying on high-level machine learning library wrappers for the core algorithm. The workflow includes:
1. **Data Preprocessing:** Merging movie titles with user ratings and creating a user-item pivot matrix where unrated movies are represented as NaN.
2. **Similarity Calculation:** Using Pearson correlation (`scipy.spatial.distance.correlation`) to find the similarity between users based on commonly rated movies, adjusting for each user's mean rating behavior.
3. **K-Nearest Neighbors (KNN):** Identifying the top `K` most similar users (neighbors) to the target user.
4. **Rating Prediction:** Predicting the target user's rating for unseen movies by calculating a weighted average of the neighbors' ratings, normalized by the similarity score.
5. **Recommendation:** Filtering out already-watched movies and returning the top `N` highest-predicted titles.

## Prerequisites
To run the notebook, you will need the following Python libraries installed:
* `pandas`
* `numpy`
* `scipy`

## Project Structure
* `Movie_Recommendation_Engine.ipynb`: The main Jupyter Notebook containing the data exploration, algorithm implementation, and testing.
* `data/movie_dataset/movies.csv`: Movie ID and title mappings.
* `data/movie_dataset/ratings.csv`: User ratings for specific movies.

## Usage
1. Clone the repository and ensure the dataset files are placed in the `data/movie_dataset/` directory.
2. Open `Movie_Recommendation_Engine.ipynb` in Jupyter Notebook or JupyterLab.
3. Run the cells sequentially to load the data, build the user-item matrix, and instantiate the recommendation functions.
4. Use the `top_n_recommendations(current_user, N)` function to get movie suggestions. 

**Example Output:**
```python
current_user = 140
print("User's favorite movies are : ", fav_movies(current_user, 5))
print("User's top recommendations are: ", top_n_recommendations(current_user, 3))
