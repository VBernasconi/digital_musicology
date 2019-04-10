### Digital Musicology
# Understanding the impact of the Cold War on Billboard Charts:  _When the American society reflects on music creation_

### Introduction
The Cold War period, whose years from 1958 to 1995 will be analysed in the present project, saw the rise of many major and diverse cultural movements. This flourishing time also enabled a large increase in the diversity of musical genres. Regarding these prompt changes and the socio-economico-political climate, we would like to understand how major genres evolved over time and try to determine, in a second phase of the project, the possible correlations with concomitant historical events. In order to conduct the research, we worked with the Billboard Charts that provides the weekly top 100 listened musical pieces in the United States. The ranking of the Billboard is based on physical and digital sales, radio play, and online streaming in the United States.

### Research Question and Hypothesis
Regarding our main research question, which is to understand the evolution of music from 1958 to 1995 and how it might have been impacted by contemporary events, we developed three main hypothesis that will have to be tested throughout the conduct of the project:
1. Based on the 6 following selected features, we expect to see significant variations in a set of major genres:
    * **key**: no specific hypothesis was determined regarding this feature.
    * **loudness**: it corresponds to the overall loudness of a track in decibels (dB). A hypothesis would be to see an increase of loudness in rock-related genres musical pieces.
    * **duration_ms**: our hypothesis is that the duration of musical pieces may tend to be shorter, regarding the growing stressful context.
    * **time_signature**: our hypothesis is that, regarding the experimental artistic context, some new time signatures might arise. However there should be a high convergence to a 4:4 time signature.
    * **tempo**: the major hypothesis regarding this aspect it that musical pieces tend to have a faster tempo, regarding the stressful context for the US civil society
    * **mode**: according to what has been presented in class, we expect an increasing equilibrium between the repartition of major and minor modalities within musical piecess.
The two major hypothesis regarding these features are that music will tend to be shorter, and tempo faster (according to literature, an increase up to 120-125 beats per minute).
2. In general, we also expect to see divergent developments between the different genres. According to the increasing diversity of genres, we assume that the difference for the above features in-between similar genres, such as all the pop variety, is minimal.

The second part of the main research question is about how can the changes observed in the different musical genres be linked to the historical context. What is the plausibility of these relationships? Which human groups are most affected by these events and which genres are related to them?

3. With regard to this aspect of the question, we seek to observe significant changes related to the African American civil rights movement, which could be expressed e.g. in the soul genre. We also expect significant historic musical events related to the counterculture movement, such as Woodstock Musical Festival in 1969, to impact music at a long-term, especially rock and folk.


### Dataset

#### Data gathering and description of the dataset
The research is based on two datasets. The first dataset is composed of the Billboard weekly list (Billboard Top 100), between  1955 and 2017, found on the online platform [Kaggle](https://www.kaggle.com/), in csv format. This table contains 300'600 rows and eight columns, containing respectively the date of the week, the rank, the song title, the artist name, the number of weeks on charts, the musical piece's year of release, the track's popularity on Spotify and the artist popularity on Spotify. The rows between 1955 and 1958 are duplicated and low-quality data. By a brief visual evaluation of the data, it can be seen that the data concerning the Spotify database are mostly missing. The number of weeks on charts is also often false or missing.

Based on song titles and artist names from this first dataset, a query is made to the [Spotify API](https://developer.spotify.com/documentation/web-api/quick-start/) in order to retrieve the corresponding entry in the Spotify database. This requires registering with Spotify as a developer and obtaining a token to access the database. The API returns json-formatted answers. The completion of the dataset is then done in several steps. The first step is to find the corresponding identifier of each track in the Spotify database, based on the artist's name and the song title. During this first run, 69% of matches were found. In a second step, this rate is increased to 78% by isolating the main artist's name and the main tokens of the title and thus submitting a simplified request to the API.

Then, the identifier obtained for each track allows access to the track features contained in the database (danceability, energy, key, loudness, mode, speechiness, acousticness, instrumentalness, liveness, valence, duration_ms, time_signature). After that, the track audio features (tempo, mode) are also collected in a third query. Finally, a fourth query gathers the musical genre of the artists.

#### Preprocessing
Data from multiple queries were merged into a single dataset. Subsequently, the billboard data was aggregated with the API data to obtain a usable dataset containing: the titles of the two databases (Billboard and Spotify), the artist name of the two databases (Billboard and Spotify), the identifier in the Spotify database, the tracks features, the audio features, a vector of the dates of each week when the track was present in the billboard chart, and a vector including the successive ranks in the billboard chart. Finally, the highest rank in the ranking is also recovered and stored. The column containing the number of weeks spent on the chart, which was of poor quality, as indicated above, was removed. It can moreover be retrieved easily for the weeks list. For reasons of data density and quality, data prior to the week of 8 August 1958 are not retained. This final preprocessed dataset is stored in json format, which unlike csv is able to deal the vector type.

The data have two biases. The first is the fact that "only" 78% of them could be retrieved from the Spotify database. However, this seems relatively acceptable bias, all the more so if we adopt the standpoint that the musical pieces that are still available today and that have been digitized are the most representative of their period. Moreover, in the timeframe finally selected, this percentage reaches 91%. The second bias is related to the margin of error of Echonest algorithms when determining features.

#### Corpus selection
For reasons of data density and to be limited to the historical period covered by the research, only the rankings published between 8 August 1958 and 31 December 1995 have been kept in the corpus. The period extends after the end of the Cold War (until 1995) in order to see if post-Cold War changes in the political context may have influenced the music creation.

#### Features
To address the research hypotheses, we started by selecting the variables. When the algorithm to calculate a certain variable was unknown and the definition of this variable was not commonly accepted by the majority of the scientific community, we decided not to keep it for our research. Therefore, we decided to retain only six physical variables: the duration, the time signature, the tempo, the mode, the key, and the loudness, as well as two perceptual variables (i.e. issued from psychological inquiry and then extended with a machine learning algorithm): the energy and the valence. Energy is described by Spotify as a perceptual measure of intensity and activity, and energetic tracks feel fast, loud, and noisy. Valence is described by Spotify as musical positiveness conveyed by a track. Tracks with high valence will sound more positive, while tracks with low valence will sound more negative.

#### Description of the corpus
Finally, the corpus contains a total of 19,098 pieces of music representing 177,700 Billboard entries out of the 195,100 published over this period, i.e. 91%.


<img src="images/weeks_on_chart.png" alt="drawing" width="450"/>

As we can see, most musical pieces are staying less that 20 weeks on chart, with a maximum lifespan of 42.


<img src="images/features_description.png" alt="drawing" width="450"/>

Hereover, a table containing the continuous features' statistics.


<img src="images/songs_per_key.png" alt="drawing" width="450"/>


Finally, a plot displaying the distribution of the songs per key. One can observe that C is the most used root, followed by G, which is consistent with what we have seen in lectures. The diatonic scale is more used with the exception of B, which is a little less used that C#. Concerning the modality, 58% of the entries are classified as major, 18% as minor and 24% are not classified. For the time signature, 70% of the data are 4/4, 6% are 3/4, 0.6% are considered other (5:4 or 1:4) and 23.4% are not classified.


<img src="images/entries_per_year.png" alt="drawing" width="450"/>

In this plot, one can observe the first occurence of the songs per year. As the years go by, the number of unique songs entering in the top 100 diminishes. As our corpus begins the week of August 8, the year 1958 was not representative as it gives only information for 5 months and then was not plotted.

<img src="images/corr_features.png" alt="drawing" width="450"/>

One can observe that the physical variables (mode, time_signature, tempo, loudness, and duration) are only weakly correlated. The perceptual variables (energy and valence) are correlated with each other and to some of the physical variables. This is not surprising since both are covering similar perceptions of music. Energy explains the subject's perceptual sense of energy, while valence quantifies the subject's perceived positive feeling of the music. Therefore, the high correlation of energy with loudness is also intuitively expected. An interesting correlation to note is also that of energy and valence with time signature.

In total, there are 987 different musical genres and 4961 songs do not have a given genre (either empty or nan value). Following is an excerpt of the first mostly assigned genres names.

<img src="images/music_genre_tot.png" alt="drawing" width="180"/>

### Initial Analysis

#### Methodology 

##### 2. Musical genres
Due to the large amount of different genres, we decided to group them into more global categories. The latter was done based on the categorisation provided by the online database AllMusic and made easily retrivable by Wikipedia on their webpage <a href="https://en.wikipedia.org/wiki/List_of_music_styles"> List of music styles </a>. Hence, the content of the html page was extracted in order to list all genres and their corresponding subgenres into a json file <a href="https://github.com/ValentineCmoi/digital_musicology/blob/master/json/music_genres_classification.json"> music_genre_classification</a>. It was then used to assign for each subgenre of each song a main genre. When no corresponding main genre could be found, the name 'other' was attributed. Regarding this 'other' entry, it is important to understand that some genres, such as main genres listed above that corresponds to '**adult standards**', '**christmas**', '**motown**', '**mellow gold**' are not genres per se but rather categories that can group many different genres. Indeed, '**adult standards**' groups musical pieces that might be more attractive to an older audience (50 years old and above). Same applies with the '**christmas**' category, which groups songs that reffer to chrismas, and '**mellow gold**', which seems to have been invented by Spotify to group classic rock of the ‘60s, ‘70s, and ‘80s.

#### Results

##### 1. Features evolution
<img src="images/yearly_features_change/root.png" alt="drawing" width="900"/>
<img src="images/yearly_features_change/time_signature.png" alt="drawing" width="900"/>
<img src="images/yearly_features_change/mode.png" alt="drawing" width="900"/>
<img src="images/yearly_features_change/loudness.png" alt="drawing" width="900"/>
<img src="images/yearly_features_change/duration.png" alt="drawing" width="900"/>
<img src="images/yearly_features_change/tempo.png" alt="drawing" width="900"/>
<img src="images/yearly_features_change/energy.png" alt="drawing" width="900"/>
<img src="images/yearly_features_change/valence.png" alt="drawing" width="900"/>


##### 2. Musical genres
The distribution of genres was plotted using a heatmap :

<img src="images/genre_distribution.png" alt="drawing" width="2000"/>

Because of the dominance of the 'other' category, which makes hard to perceive the distribution of other main genres, it was decided to remove it from following heatmap:

<img src="images/genre_distribution_nother.png" alt="drawing" width="2000"/>

As we can see on these two heatmaps, there is a prevalence of rock musics between 1964 and 1990. Country music saw a decrease of popularity throughout the 70s and hip hop songs appeared later, with early uses in 1964 and 1969 before settling down in the late 70s. In order to better understand these movements of music genres, a similar heatmap with a normalized distribution for each genre was created:

<img src="images/genre_distribution_perc_nother.png" alt="drawing" width="2000"/>

On the above, we can clearly see that hip hop seems to have reached its pick of use for the studied time range in the early 90s, similarly to caribbean and caribbean-influenced songs. Other music genres benefit from a more linear distribution over time.

A third heatmap with a normalized distribution per year was finally produced in order to better see the dominance of some genres for each year.

<img src="images/genre_distribution_perc_year_nother.png" alt="drawing" width="2000"/>

#### Interpretation

##### 2. Musical genres

With the different heatmaps generated, we can clearly see a dominance of rock music from the mid-60s to the early 90s. Before the rise of rock music, country music seems to have been more dominent. We can also see that musical genres, such as hip hop, caribbean and electronic appeared later on the musical scene. 

The fact that there is a greater proportion of songs listed as 'other', especially at the beginning of the studied period, in the early 60s, can be explained by the fact that these years are nowadays considered as _nostalgic_ years. They include a lot of music that can be considered as _old_ and that could easily fit the '**adult standards**' category. Another explaination could be the fact that these early years were the laboratory of diverse research and novelties in terms of musical genres and that many of them were not retained by history.

In a general way this first set of results shows the great emergence of different musical styles over the studied period. The fact that we had to group the large amount of genres to more general classes and that this evolution is still perceivable is an interesting proof of that phenomenon. The great majority of top listed titles from which rock music benefits shows not only its popularity, but is also a hint of the diversity of subgenres that occured within this style.

### Conclusion (interpretation en lien avec questions de recherche)

### Discussion (critique de la conclusion)



### Exploratory analysis

### Methods
The first part of the methodology will be based on a visual graphical approach, aimed at establishing observations related to the different genres. The method will work on a weekly granularity and identification of statistically significant changes relative to a 95% confidence interval. The calculation of partial temporal derivatives, carried out over periods of variable granularity, will allow one to observe trends, of varying degrees of slowness depending on the granularity. In order to gain insights on the relative changes from one genre to another, and to better visualize the specific drift of each genre, a degree two Principal Component Analysis will be used.


### Literature
- Karen A. Cerula, "Social Disruption and Its Effects on Music: An Empirical Analysis", _Social Forces_, Vol. 62, Issue 4, June 1984, pp. 885-904, [Accessed on: <a href= https://doi.org/10.1093/sf/62.4.885> https://doi.org/10.1093/sf/62.4.885</a>]
- Richard A. Peterson and David G. Berger, "Cycles in Symbol Production: The Case of Popular Music", _American Sociological Review_, Vol. 40, No. 2, April 1975, pp. 158-173,  [Accessed on: <a href= https://www.jstor.org/stable/2094343> https://www.jstor.org/stable/2094343</a>]
-  Eric Clarke, Nicholas Cook, "Empirical Musicology: Aims, Methods, Prospects", Oxford University Press, 2004
- Timorhty J. Dowd, "Production perspectives in the sociology of music", _Poetics_, Vol. 32, Issue 3-4, pp. 235-246,  [Accessed on: <a href= https://doi.org/10.1016/j.poetic.2004.05.005> https://doi.org/10.1016/j.poetic.2004.05.005</a>]
- Peter J. Schmelz, "Introduction: Music in the Cold War", _The Journal of Musicology_, Vol. 26, No. 1, 2009, pp. 3-16 [Accessed on: <a href= https://www.jstor.org/stable/10.1525/jm.2009.26.1.3> https://www.jstor.org/stable/10.1525/jm.2009.26.1.3</a>]
- Matthias Mauch, Robert M. MacCallum, Mark Levy, and Armand M. Leroi, "The Evolution of Popular Music: USA 1960-2010", _Royal Society Open Science_, Vol. 2, No. 5, May 2015, [Accessed on: <a href= https://doi.org/10.1098/rsos.150081> https://doi.org/10.1098/rsos.150081</a>]

It seems that a great work was conducted during the 70s and 80s in order to understand the social significance of music and its relationship to sociological events. Indeed, the Cold War saw the emergence of major popular cultural movements. Many artistic fields, starting by art historians, were trying to understand the impact and influences of the political situation. More recently, in 2006, the <a href= http://ams-net.org/cwmsg/>AMS Cold War and Music Study Group</a> was created by the American Musicological Society in order to understand the impact of this important event on the field. However, most of these empirical studies were focusing on lyrics and genres of music, on the predominance of certain musicians on the market and on the impact of leading recording companies in the music industry. It seems that no direct analysis of the technical music properties, such as harmony, keys or tempo, and their evolution through the years was put in relationship to the sociological context. The idea would be to go as well from the performing social context to the music generated, but to determine the structural impact rather than the style or genre evolutions.
