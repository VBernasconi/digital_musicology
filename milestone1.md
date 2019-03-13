### Digital Musicology
# Understanding the impact of the cold war on Billboard Charts:  _When the american society reflects on music creation_

### Dataset: [Spotify API](https://developer.spotify.com/documentation/web-api/quick-start/)

### Research Questions
Underlying research questions we will try to answer through the project:
* How major socio-economical changes derived from the Cold War impacted american popular music from the Billboard chart ?
* What are the musical features and/or genres that were more impacted by these events?
* Were the various genres impacted in different ways?

We decided to study the impact of the Cold War on the Billboard Chart songs with the help of the metadata and audio features given by Spotify. We chose the Cold War as historical background for this analysis as it was a key period of American history, and it had a huge effect on the society and the economy. In order to perform this analysis, we will look at socio-economical indicators such as GDP, minimum wages or even mass shootings in connection with the songs of the Billboard chart.

We are really interested in these research questions as it will allow us to discover a new way to apprehend music and also to see which impact history can have on music. For the moment, we don't have particular expectations regarding the possible outcomes of this research, as the aim is precisely to identify the salient musical and audio features that are the most related to the context.

### Concepts and Data
In concrete terms, the project seeks to study how music in the United States is impacted by social, economic and historical phenomena (referred hereafter as event). To achieve this, we will use the [Billboard Top 100](https://www.billboard.com/charts/hot-100), which each week ranks the 100 most popular music in the United States. We will cross these musics with the [Spotify metadata database](https://developer.spotify.com/), accessible through an API. This database allows you to directly retrieve musical metadata. The available metadata are the following :
* Fundamental music properties (key, modality (minor/major), meter, beats intervals, pitches, list of timbres)
* Audio properties (loudness, speechiness, instrumentalness)
* Mood indicators (tempo, valence, energy, danceability)
* Context (liveness, acousticness)
* Categorical (genre, artist)
* Other (duration, title)

The operationalization of indicators such as danceability was performed by [Echonest](http://the.echonest.com/) on behalf of Spotify and is described in the [API references](https://developer.spotify.com/documentation/web-api/reference/). The impact will be measured through a correlation with other event indicators. Data on these indicators are available on the [Kaggle platform](https://www.kaggle.com/datasets) and on the [US government database](https://www.data.gov/).

### Methods
We seek to highlight differences in Billboard chart top songs' audio features during and after the Cold War. To do so, we plan to use mathematical indicators to identify the metadata that are most strongly correlated with event indicators. We also plan to establish a regression between metadata and event indicator. Categorical data will be processed by dummy variable encoding. To determine which events have the greatest impact on the evolution of music and also which musical variables are the most impacted, we will use the Principal Component Analysis method.

### Literature
- Karen A. Cerula, "Social Disruption and Its Effects on Music: An Empirical Analysis", _Social Forces_, Vol. 62, Issue 4, June 1984, pp. 885-904, [Accessed on: <a href= https://doi.org/10.1093/sf/62.4.885> https://doi.org/10.1093/sf/62.4.885</a>]
- Richard A. Peterson and David G. Berger, "Cycles in Symbol Production: The Case of Popular Music", _American Sociological Review_, Vol. 40, No. 2, April 1975, pp. 158-173,  [Accessed on: <a href= https://www.jstor.org/stable/2094343> https://www.jstor.org/stable/2094343</a>]
-  Eric Clarke, Nicholas Cook, "Empirical Musicology: Aims, Methods, Prospects", Oxford University Press, 2004
- Timorhty J. Dowd, "Production perspectives in the sociology of music", _Poetics_, Vol. 32, Issue 3-4, pp. 235-246,  [Accessed on: <a href= https://doi.org/10.1016/j.poetic.2004.05.005> https://doi.org/10.1016/j.poetic.2004.05.005</a>]
- Peter J. Schmelz, "Introduction: Music in the Cold War", _The Journal of Musicology_, Vol. 26, No. 1, 2009, pp. 3-16 [Accessed on: <a href= https://www.jstor.org/stable/10.1525/jm.2009.26.1.3> https://www.jstor.org/stable/10.1525/jm.2009.26.1.3</a>]

It seems that a great work was conducted during the 70s and 80s in order to understand the social significance of music and its relationship to sociological events. Indeed, the Cold War saw the emergence of major popular cultural movements and many artistic fields, starting by art historians, were trying to understand the impact and influences of the political situation. More recently, in 2006, the <a href= http://ams-net.org/cwmsg/>AMS Cold War and Music Study Group</a> was created by the American Musicological Society in order to understand the impact of this important event on the field. However, most of these empirical studies were focusing on lyrics and genre of musics, the predominance of certain musicians on the market and the impact of leading recording companies in the music industry. It seems that no direct analyse of the technical music properties, such as harmony, keys or tempo, and their evolutions through the years was put in relationship to these sociological context. The idea would be to go as well from the performing social context to the music generated, but to determine the structural impact rather than the style or genre evolutions.
