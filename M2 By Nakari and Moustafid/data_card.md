# Data card — M2

**Pair names:** Amine Nakari and Salaheddine Moustafid

**Source (from the curated list):** TMDB

**Registered scope:** English-original-language movies released January 1, 2015–October 4, 2026, with at least 100 TMDB votes; adult and video entries excluded.

## Source

The Movie Database (TMDB), API v3: GET /discover/movie for movie records and GET /genre/movie/list for genre names. Base URL: https://api.themoviedb.org/3.

## Collection method & dates

Python requests and pandas; Bearer token read from an .env file. Page-number pagination: 273 movie pages, up to 20 results per page, plus the genre request. JSON responses were cached locally, with retries and delays. Collection ran on October 5, 2026, 10:13:49–10:16:02 UTC. The release-date window is January 1, 2015–October 4, 2026.

## Scope & size

A collection of english-original-language movies in the provided release window, at least 100 TMDB votes (adult and video entries excluded). Raw tables: 5,455 unique movies with 10 columns; 13,697 movie–genre associations with 3 columns, covering 19 genres. Cleaning retains all rows: dates were converted to datetime and a missing_genre flag was added. 
## Schema

Movies: id (int64), unique movie identifier; genre_ids (list of integers), assigned genres; title and original_title (text), display and original titles; original_language (text), language code; overview (text), plot summary; release_date (text originally, turned into datetime), release date; popularity (float64), TMDB attention score; vote_average (float64), audience rating on 0–10; vote_count (int64), number of rating votes. Added: missing_genre (bool), empty genre list indicator. Genre table: movie_id (int64), movie reference; genre_id (int64), genre identifier; genre_name (text), genre label.

## Known biases & limitations

The English-language and 100-vote filters exclude movies with other languages, unrated films and films with few ratings. Recent films have had less time to accumulate votes. Coverage of 2026 is partial (only up to October 4th). Ratings and popularity reflect the values at the time of the snapshot. TMDB coverage and self-selected voters may not represent all movies or audiences. One movie with ID 1140817, has no genre and thus was retained and flagged, with no invented genre. Genre groups overlap. There were no nulls, duplicate IDs/pairs. Large values were retained (movies with very high vote_count and averages).

## License / ToS

Use is governed by TMDB API terms, not an assumed open-data license. TMDB permits free non-commercial API use with attribution; commercial use requires a commercial arrangement. Follow TMDB attribution/logo requirements and retain its notice: “This product uses the TMDB API but is not endorsed or certified by TMDB.” References: https://developer.themoviedb.org/docs/faq and https://www.themoviedb.org/api-terms-of-use. Data are kept local for this academic project.

## GDPR note

The dataset contains movie information and aggregate ratings. We did not collect user accounts, individual votes, reviews, or contact details. Plot summaries may mention real people, but we do not analyse individuals. API credentials are not included in the submission.
