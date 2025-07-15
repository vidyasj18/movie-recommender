# movie-recommender

## Project overview

This project focusses on recommending similar movies built by integrating frontend and data models from the dataset TMDB 5000 movies and TMDB 5000 credits. This uses Classical NLP preprocessing (stemming + Bag of Words) and Vector-based similarity (cosine distance) techniques. The goal is to accurately recommend 5 movies to the movie selected by the user.


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

- NumPy and Pandas : For numerical operations and data manipulation.

- Scikit-learn : For importing algorithms and tools.

- NLTK : Natural Language Toolkit is used to process and analyze human language data (text).

- Pickle: Save (serialize) Python objects to a file and load (deserialize) them later.

- Streamlit : For creating frontend for the model.
  

## Data Preprocessing

### Install sickit-learn

```

!pip install scikit-learn

```

### Dataset merging 

This project uses 2 datasets, both are merged based on the "title".

```

movies = movies.merge(credits,on='title')

```

### Dropping irreleavant movies

Dropped movies containing null values.

```

movies.isnull().sum()
movies.dropna(inplace=true)

```

Checked for duplicate movies.

```

movies.duplicated().sum()

```

### Refining Genre, Keywords, Cast.

Genre,Keywords and cast has some names and each name has some unique id. Created a convert function which extracts only names from these columns.

```

import ast
def convert(obj):
    L = []
    for i in ast.literal_eval(obj):
        L.append(i['name'])
    return L

```

This convert function is applied on Genre, Keywords and cast.

```

movies['genres'] = movies['genres'].apply(convert)

```

```

movies['keywords'] = movies['keywords'].apply(convert)

```

```

movies['cast'] = movies['cast'].apply(convert3)

```

Crew contains a lot of names, for simplicity we extracted only the directors name.

```

import ast
def fetch_director(obj):
    L = []
    for i in ast.literal_eval(obj):
        if i['job']=='Director':
            L.append(i['name'])
            break
    return L
movies['crew'] = movies['crew'].apply(fetch_director)

```

### Merging all the info related to a movie in single column.

For simplicity, created new Tags column and merged all other columns except movie_id and title in it.

```

movies['tags'] = movies['overview'] + movies['genres'] + movies['keywords'] + movies['cast'] + movies['crew']

```

```

new_df = movies[['movie_id','title','tags']]

```


## Model Architecture

### Install nltk

```

!pip install nltk

```



