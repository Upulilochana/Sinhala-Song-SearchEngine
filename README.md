# Sinhala-Song-SearchEngine

This is a simple Sinhala song lyrics search engine created using Elasticsearch and node js.

## Getting Started

### Setting Up Elasticsearch
this project created using Elasticsearch version 7.8.0.
* Download [ElasticSearch](https://www.elastic.co/downloads/elasticsearch)
* Unzip the Downlooaded ZIP or TAR.GZ file and direct into bin folder 
* Run elasticsearch.bat file in windows operating system.
* Now Started an ElasticSearch Instance on the port 9200

## Running the project  

### Run data.js file

$ node data.js

### Run index.js file

$ node index.js

### Go to http://localhost:3001/

Start search sinhala songs based on lyrics,writers,genre,music,artist.

## Structure of the Data
sinhala_song_corpus.js file contains the Song Corpus for the project 

Each song contains the following data fields.
1. Title 
2. Artist 
3. Genre 
4. Writer 
5. Music
6. Visits 
7. Lyrics

## Functionalities


* songs can be search based on following fields(fillter all the results)

1. title -result songs which includes this lyrics
>Eg:ජගන් මෝහිනී 
2. lyric  -result songs which includes this lyrics
>Eg:චාරු දේහේ නුරා
3. music  -result all songs a musician contributes
>Eg:ජයන්ත ගමගේ සංගීතමය ගීත
4. artist  -result all songs an artist contributes 
>Eg:ක්ලැරන්ස් විජේවර්ධන ගයන ගීත
5. writer -result all songs a writer contributes
>Eg:කරුණාරත්න අබේසේකර ලියූ ගීත

* songs can search on definite range
 >Eg:ඇන්ජලින් ගුණතිලක ගයන ගීත 7

* Most popular songs can search
 >Eg:ඇන්ජලින් ගුණතිලක ගයන ගීත හොදම 7<br>
 (The search result is sorted based on the visits value per each song and the best 7 songs are returned )
 
* Search phrases support synonyms of the keywords
  >Eg:Presence of any word out of'කීව', 'කී', 'ගායනා කරන', 'ගයන', 'ගායනා', 'හඩින්', 'කියනා <br>
  identifies the search as a search for an artist.

## Indexing and Querying Techniques

### Boosting
Boosting has been used as the main query optimization technique. Each field of a search is boosted based on the field which user search.<br>
>Eg:ක්ලැරන්ස් විජේවර්ධන ගයන ගීත <br>
boost the artist field by a certain value. 

### Rule Based Classification
classify user search into different search queries and apply different rules for getting result.<br>
>Eg:if the input contains හොදම 7<br>
apply range query and filter 7 result based on visits value.




