# Database Schema Design

## Schema

### Tables

#### Movies

- **Columns:**
  - `movie_id INT PRIMARY KEY`
  - `title VARCHAR(255) NOT NULL`
  - `director_id INT`
  - `genre_id INT`
- **Foreign Keys:**
  - `director_id` references `Directors(director_id)`
  - `genre_id` references `Genres(genre_id)`

#### Directors

- **Columns:**
  - `director_id INT PRIMARY KEY`
  - `name VARCHAR(255) NOT NULL`

#### Actors

- **Columns:**
  - `actor_id INT PRIMARY KEY`
  - `name VARCHAR(255) NOT NULL`

#### Genres

- **Columns:**
  - `genre_id INT PRIMARY KEY`
  - `genre_name VARCHAR(100) NOT NULL`

#### Cast

- **Columns:**
  - `movie_id INT`
  - `actor_id INT`
  - `role VARCHAR(255)`
- **Primary Key:** (`movie_id`, `actor_id`)
- **Foreign Keys:**
  - `movie_id` references `Movies(movie_id)`
  - `actor_id` references `Actors(actor_id)`

#### Ratings

- **Columns:**
  - `movie_id INT`
  - `rating DECIMAL(3, 1) CHECK (rating >= 0 AND rating <= 10)`
- **Primary Key:** `movie_id`
- **Foreign Key:**
  - `movie_id` references `Movies(movie_id)`

## SQL Queries

### Create Table Queries

```sql
-- Movies table
CREATE TABLE Movies (
  movie_id INT PRIMARY KEY,
  title VARCHAR(255) NOT NULL,
  director_id INT,
  genre_id INT,
  FOREIGN KEY (director_id) REFERENCES Directors(director_id),
  FOREIGN KEY (genre_id) REFERENCES Genres(genre_id)
);

-- Directors table
CREATE TABLE Directors (
  director_id INT PRIMARY KEY,
  name VARCHAR(255) NOT NULL
);

-- Actors table
CREATE TABLE Actors (
  actor_id INT PRIMARY KEY,
  name VARCHAR(255) NOT NULL
);

-- Genres table
CREATE TABLE Genres (
  genre_id INT PRIMARY KEY,
  genre_name VARCHAR(100) NOT NULL
);

-- Cast table
CREATE TABLE Cast (
  movie_id INT,
  actor_id INT,
  role VARCHAR(255),
  PRIMARY KEY (movie_id, actor_id),
  FOREIGN KEY (movie_id) REFERENCES Movies(movie_id),
  FOREIGN KEY (actor_id) REFERENCES Actors(actor_id)
);

-- Ratings table
CREATE TABLE Ratings (
  movie_id INT,
  rating DECIMAL(3, 1) CHECK (rating >= 0 AND rating <= 10),
  PRIMARY KEY (movie_id),
  FOREIGN KEY (movie_id) REFERENCES Movies(movie_id)
);
```
