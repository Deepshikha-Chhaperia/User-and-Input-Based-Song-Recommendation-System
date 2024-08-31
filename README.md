# Spotify Recommender System

## Overview

This project provides a Spotify-like recommendation system for songs and artists using a combination of text and numeric data. It leverages cosine similarity to compare songs and artists based on their genres and audio features. The recommender system can suggest similar songs and artists based on a given input song, allowing users to discover new music that matches their tastes.

## Features

- **Song Recommendation**: Recommends songs similar to a given song based on genres and audio features.
- **Artist Recommendation**: Recommends artists similar to a given artist based on genres and popularity.
- **Complete Spotify Recommender**: Combines both song and artist recommendations into a single function, offering a comprehensive music discovery experience.

## Setup

### Prerequisites

- Python 3.x
- Jupyter Notebook or any Python IDE
- Required Libraries: 
  - `pandas`
  - `numpy`
  - `sklearn` (Scikit-Learn)

### Installing Required Libraries

If you do not have the required libraries installed, you can install them using pip:

```bash
pip install pandas numpy scikit-learn
```

## Data Setup

The recommendation system relies on two main DataFrames:

1. **`song_library`**: A DataFrame containing details of songs including their genres, audio features, and other metadata.
2. **`artist_library`**: A DataFrame containing details of artists including their genres, popularity, followers, and other metadata.

Make sure these DataFrames are loaded in your environment with the following structure:

### `song_library` DataFrame

| Column Name       | Description                        |
|-------------------|------------------------------------|
| `name`            | Name of the song                   |
| `artists`         | Artists contributing to the song   |
| `genres`          | Genres associated with the song    |
| `release_year`    | Year the song was released         |
| `duration_s`      | Duration of the song in seconds    |
| `popularity`      | Popularity score of the song       |
| `danceability`    | Danceability feature of the song   |
| `energy`          | Energy feature of the song         |
| `key`             | Musical key of the song            |
| `loudness`        | Loudness feature of the song       |
| `mode`            | Mode feature of the song           |
| `speechiness`     | Speechiness feature of the song    |
| `acousticness`    | Acousticness feature of the song   |
| `instrumentalness`| Instrumentalness feature of the song|
| `liveness`        | Liveness feature of the song       |
| `valence`         | Valence feature of the song        |
| `tempo`           | Tempo feature of the song          |

### `artist_library` DataFrame

| Column Name       | Description                        |
|-------------------|------------------------------------|
| `id`              | Unique identifier of the artist    |
| `followers`       | Number of followers of the artist  |
| `genres`          | Genres associated with the artist  |
| `name`            | Name of the artist                 |
| `popularity`      | Popularity score of the artist     |

## Usage

### Song Recommender

The `song_recommender` function recommends similar songs based on the given song name. It compares the genres and audio features of the input song with other songs in the `song_library` and returns the top 5 most similar songs.

#### Example

```python
recommended_songs = song_recommender('Hail to the King')
print(recommended_songs)
```

## Artist Recommender

The `artist_recommender` function recommends similar artists based on the given artist name. It compares the genres, popularity, and follower count of the input artist with other artists in the `artist_library` and returns the top 5 most similar artists.

### Example

```python
recommended_artists = artist_recommender('Def Leppard')
print(recommended_artists)
```

## Complete Spotify Recommender

The `spotify_recommender` function combines the song and artist recommendation features. It takes a song name as input, recommends similar songs, and then recommends artists based on the contributing artists of the input song.

### Example

```python
spotify_recommender('Nero Forte')
```
This function will output a list of songs similar to "Nero Forte" and also recommend artists similar to those who contributed to the song.

### Notes

- If the input song or artist is not found in the library, the functions will display an appropriate message.
- The similarity score is calculated as the average of the cosine similarity between text vectors (genres) and numeric vectors (audio features or artist metrics).


