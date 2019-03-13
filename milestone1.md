# Digital Musicology
## Understanding historical impacts on music creations _d_

### Dataset: [Spotify API](https://developer.spotify.com/documentation/web-api/quick-start/)

### TODO:
- Définir une région du monde
- Définir une période spécifique
- Définir un type de musique

### Research Question
- What do we want to study
- What are possible outcomes

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
