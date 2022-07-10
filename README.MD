# Movie Recommendation Application 
<img src="https://i.ibb.co/y0BYhDF/movierec.png" alt="movierec" border="0"> 

* This application takes in a movie title and returns 8 movie recommendations based on genre, movie overview, director and actors (Content based recommendation engine) also returns movie suggestions from user search input.  
* It has 2 types of endpoints, one for recommendations and the other for movie suggestions.
* Used the 5000 tmdb_movies dataset which includes movies up to 2017.
* Scraped 2018 to September 2021 movies from www.imdb.com.
* Engineered and cleaned the data so as to extract genre, director, movie overview and actors.
* Used Natural Language Processing (NLP) to tokenize and vectorize the data.
* Built a client facing Api using flask and hosted it on Heroku

### **Resources Used**
***
**Python Version**: 3.8

**Packages**: Pandas, Numpy, Sklearn, Json, Flask, Pickle, Fetch API and Beautiful Soup, Jupyter notebook   
![Python](https://img.shields.io/badge/python-3670A0?style=flat&logo=python&logoColor=ffdd54) ![Flask](https://img.shields.io/badge/flask-%23000.svg?style=flat&logo=flask&logoColor=white) ![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=flat&logo=pandas&logoColor=white) ![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=flat&logo=numpy&logoColor=white) ![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=flat&logo=jupyter&logoColor=white)

**For Web Framework Requirements**: pip install -r requirements.txt

**APIs**: TMDB API

### **Web Scraping**
***
Used Beautiful Soup to scrape 1000 movies from www.imdb.com from year 2018 to September 2021. Scraped the following features:
* Movie Title
* Genre
* Movie Overview
* Director
* Actors

### **Data Cleaning**
After scraping the data I needed to clean the data so as to feed it to the model so I made the following changes:
* Used the TMDB API to get the movie ids of the scraped movies
* Extracted only 3 actors from both the tmdb_dataset and scraped new movies to be used in the model
* Converted string data to integer data type
* Combined the director, genre, movie_overview and 3 actors columns 
* Combined the tmdb dataset and the scraped new movies dataset to create one dataset of 6000 movies with 3 columns Title, Movie_id and Combined

### **Model Building**
***
* Tuned and used TfidfVectorizer from SKLearn package to tokenize and vectorize the combined text column.
* Transformed the Combined column to a matrix
* Used the Sigmoid_Kernel model from Sklearn metrics.pairwise to create a similarity matrix.
* Created a recommender function which links the similarity matrix to the Movie_id and Title columns
* Created the function to recommend 8 movies from a movie title input

### **Productionization**
***
In this step, I built a flask API endpoint thats hosted on Heroku. I did the following:
* Used react to build the frontend.
* Created a suggestion engine at the backend(Flask server) to suggest a movie to the user as they type each letter of a movie title, used axios to move data between client and backend
* Used the axios package to move movie title entered by the client to the backend to be processed in the recommendation engine then back to the frontend
* Utilized the TMDB API to fetch movie posters, budget, popularity, overview of the typed and recommended movies 
* Created a javascript click event which also sends the clicked movie to the recommendation engine at the backend and return recommended movies with extra information from the TMDB API  

**Live Application:** [MoviePlus](https://react-movieplus.netlify.app)
