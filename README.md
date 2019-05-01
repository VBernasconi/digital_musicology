### Digital Musicology - Spring semester 2019

# Understanding the impact of the Cold War on Billboard Charts:  _When the American society reflects on music creation_

### Group members
- Marion Kramer: marion.kramer@epfl.ch
- Rémi Petitpierre: remi.petitpierre@epfl.ch
- Valentine Bernasconi: valentine.bernasconi@epfl.ch

### Structure of the repository

__data/__
* _Billboard-Weekly-Songs-With-Song-And-Artist-Spotify-Popularity.csv_ : Contains the initial Billboard dataset
* _dataset.csv_ : An intermediary version of the API-scrapped data
* _artists_genres.csv_ : An intermediary version of the API-scrapped data
* _corpus.csv_ : The cleaned and preprocessed corpus in csv format (main dataset is in json format, cf. json/ folder)

__json/__
* _corpus.json_ : The cleaned and preprocessed corpus in json format
* _database_genres_classification.json_ : The corpus with corresponding main genre category for each subgenre
* _genre_categories_grouped.json_ : The corpus with on a single row for each title the subgenres and corresponding main genres
* _music_genres_classification.json_ : json file containing the main music genre categories and their corresponding subgenres

__images/__
* This repository just contains the images found in the .md milestones files

__Home repository__
* _API_scrapper.ipynb_ : Jupyter notebook containing the code used to scrap the Spotify API
* _Extract_corpus.ipynb_ : Jupyter notebook containing the code used to isolate and unify the datasets from different sources, clean them, formate them and extract the corpus out of it
* _Basic_statistics.ipynb_ : Jupyter notebook containing the code used to compute the basic statistics described in milestone2.md
* _Exploratory_analysis.ipynb_ : Jupyter notebook containing the code used to compute the features change and the salient drifts, presented in milestone 3
* _Machine_learning.ipynb_ : Jupyter notebook containing the code used to cluster the songs, and to investigate the characteristic features of the various genres, as presented in milestone 4
* _Genres_classification.ipynb_ : Jupyter notebook containing the code used to classify the subgenres into greater categories of genres based on the classification retrieved with the help of Musical_genres_scrapper.ipynb. Contains also research on data with time signature 1/4
* _Musical_genres_scrapper.ipynb_ : Jupyter notebook containing the code used to retrieve the main genre classification from Wikipedia
* _milestone1.md_ : Project milestone 1 description
* _milestone2.md_ : Project milestone 2 description
* _milestone3.md_ : Project milestone 3 description – exploratory analysis
* _milestone4.md_ : Project milestone 3 description – final results and interpretation
