MovieLens Web Application

This project is a web application based on the MovieLens dataset. It allows users to search for movies, add new movies, temporarily rate movies, and receive movie recommendations based on their ratings.

The application is implemented with a simple frontend and a Python backend. The frontend is built with HTML, CSS and JavaScript, while the backend uses FastAPI and SQLite for data storage.

Technologies Used
HTML
CSS
JavaScript
Python
FastAPI
SQLite
MovieLens Latest Small Dataset
Main Features
Search Movies by Title

Users can search for movies by typing a keyword in the search box. The frontend sends a GET request to the backend, and the backend searches the movies table using the movie title.

Add New Movie

Users can add a new movie by providing a title and genres. The frontend sends a POST request to the backend, and the backend inserts the new movie into the SQLite database.

Temporary User Ratings

Users can rate movies from 0.5 to 5.0. These ratings are stored temporarily in the browser memory using a JavaScript object. They are not saved permanently in the database and are lost if the page is refreshed.

Movie Recommendations

The application can generate movie recommendations based on the temporary ratings given by the current user. The backend uses user-based collaborative filtering and compares the current user with existing MovieLens users.

Tag-Based Movie Search

An extra feature was added to support movie search based on tags. The user can type a tag keyword, such as funny, and the frontend sends a POST request to the backend.

The backend searches the tags table and joins it with the movies table in order to return the matching movies. The response includes the movie ID, title, genres, and the matching tag.

The matching rule is:

If the keyword has fewer than 5 characters, the tag must match exactly.
If the keyword has 5 or more characters, the first 5 characters of the keyword are compared with the first 5 characters of each tag.
The search is case-insensitive.
API Endpoints

The backend provides the following main endpoints:

GET  /movielens/api/movies
POST /movielens/api/movies
GET  /movielens/api/ratings/{movie_id}
POST /movielens/api/recommendations
POST /movielens/api/tags/movies
GET  /movielens/api/health
How to Run the Application

First, create the SQLite database from the MovieLens CSV files.

Then, start the FastAPI backend:

python3 -m uvicorn main:app --reload --port 3000

The backend runs at:

http://127.0.0.1:3000

The API documentation is available at:

http://127.0.0.1:3000/docs

The frontend can be opened with a local development server, such as Live Server in VS Code.

Project Structure
backend/
    main.py
    database.py
    recommender.py
    create_db.py
    movielens.db

frontend/
    index.html
    index.css
    index.js
Notes

The original application functionality was preserved. The tag-based movie search was added as an extra feature without changing the existing movie search, add movie, rating, and recommendation features.
