# movie-recommender

## Project overview

This project focusses on recommending similar movies from the dataset TMDB 5000 movies and TMDB 5000 credits. This uses Classical NLP preprocessing (stemming + Bag of Words) and Vector-based similarity (cosine distance) techniques. The goal is to accurately recommend 5 movies to the movie selected by the user.

## Dataset

https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata This dataset contains 4809 movies along with their  over 15 characteristics.

### Movie characteristics

- genre
- id
- link
- keywords
- language
- title
- popularity
- production companies
- production countries
- release date
- revenue
- runtime
- status
- tagline
- title
- vote average
- vote count

## Libraries used

- NumPy and Pandas : For numerical operations and data manipulation

- Scikit-learn : For importing algorithms and tools

- NLTK : Natural Language Toolkit is used to process and analyze human language data (text).

- Pickle: Save (serialize) Python objects to a file and load (deserialize) them later.

- Streamlit : For creating frontend for the model.

## Data Preprocessing


