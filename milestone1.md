# Digital Musicology
## Understanding historical impacts on music creations _d_

### Dataset: [Spotify API](https://developer.spotify.com/documentation/web-api/quick-start/)

### TODO:
- Définir une région du monde
- Définir une période spécifique
- Définir un type de musique

### Research Question
We want to study the impact of the Cold War on the Billboard Chart songs with the help of the metadata and audio features given by Spotify. We decided to choose the Cold War as historical background for the analysis because it was a big event for American society, and it had a huge effect on the society and the economy. In order to perform this analysis, we will look at socio-economical indicators such as minimum wages or mass shooting in addition to the songs of the Billboard chart.

In a larger context, the idea of the project is to see if the Billboard chart reflects the changes happening in the American society in a historic-socio-economical context, and then to see if the Billboard chart is an indicator about the American society.

We are really interested in this research question because it will permit us to discover a new way to apprehend music and also to see which impact history can have on music.

Possible outcomes are to see differences in audio features between songs that were in the Billboard Chart during the Cold War and the ones that were in it after, but also to see correlations between audio features of songs and socio-economical indicators.

### Concepts and Data
In concrete terms, the project seeks to study how music in the United States is impacted by social, economic and historical phenomena (referred hereafter as event). To achieve this, we will use the [Billboard Top 100](https://www.billboard.com/charts/hot-100), which each week ranks the 100 most popular music in the United States. We will cross these musics with the [Spotify metadata database](https://developer.spotify.com/), accessible through an API. This database allows you to directly retrieve musical metadata. The available metadata are the following :
* Fundamental music properties (key, modality (minor/major), meter)
* Audio properties (loudness, speechiness, instrumentalness)
* Mood indicators (tempo, valence, energy, danceability)
* Context (liveness, acousticness)
* Categorical (genre, artist)
* Other (duration, title)

The operationalization of indicators such as danceability was performed by [Echonest](http://the.echonest.com/) on behalf of Spotify and is described in the [API references](https://developer.spotify.com/documentation/web-api/reference/). The impact will be measured through a correlation with other event indicators. Data on these indicators are available on the [Kaggle platform](https://www.kaggle.com/datasets) and on the [US government database](https://www.data.gov/).

### Methods
We plan to use mathematical indicators to identify the metadata that are most strongly correlated with event indicators. We also plan to establish a regression between metadata and event indicator. Categorical data will be processed by dummy variable encoding. To determine which events have the greatest impact on the evolution of music and also which musical variables are the most impacted, we will use the Principal Component Analysis method.

### Literature
- State-of-the-art regarding the research question (at least 3 publications)
- Which issues are not yet addressed ant that the project could supplement

### Support
- Do we need support from the TAs?
