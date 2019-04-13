### Digital Musicology
# Understanding the impact of the Cold War on Billboard Charts:  _When the American society reflects on music creation_

## Introduction
The Cold War period, whose years from 1958 to 1995 will be analysed in the present project, saw the rise of many major and diverse cultural movements. This flourishing time also enabled a large increase in the diversity of musical genres. Regarding these prompt changes and the socio-economico-political climate, we would like to understand how major genres evolved over time and try to determine, in a second phase of the project, the possible correlations with concomitant historical events. In order to conduct the research, we worked with the Billboard Charts that provides the weekly top 100 listened musical pieces in the United States. The ranking of the Billboard is based on physical and digital sales, radio play, and online streaming in the United States.

## Research Question and Hypothesis

Our main research question is to understand the evolution of music from 1958 to 1995 and how this evolution have been impacted by contemporary events. As the music is composed of different musical genres, a second part of the question research is about how can the change observed in these genres be linked to the historical context. What is the plausibility of theses relationships ? Which humans groups are the most affected by theses events and which genres are related to them ? 
Regarding our main research question, we developed three main hypothesis that will have to be tested throughout the conduct of the project:

1. With regard to the second part of the research question, we seek to observe significant change related to the African American civil rights movement, which could be expressed e.g. in the soul genre. We also expect significant historic musical events related to the counterculture movement, such as Woodstock Musical Festival in 1969, to impact music at a long-term, especially rock and folk.

2. In general, we also expect to see divergent developments between the different genres (pop, rock, hip hop, etc). However, as the number of different genres increases through the year, many of these genres can be classified as subparts of the major genres, e.g. bubble gum pop is a subcategory of the pop genre. Knowing this, we assume that the difference for the chosen features is minimal between genres belonging to the same major genre.

3. Based on the 6 following features, we expect to see significant variation in a set of major genres:
    * **key**: no specific hypothesis was determined regarding this feature.
    * **loudness**: it corresponds to the overall loudness of a track in decibels (dB). Our hypothesis would be to see an increase of loudness in rock-related genres musical pieces.
    * **duration_ms**:  hypothesis is that the duration of musical pieces may tend to be shorter, regarding the growing stressful context.
    * **time_signature**: our hypothesis is that, regarding the experimental artistic contexts, some new time signatures might arise. However there should be a high convergence to a 4:4 time signature.
    * **tempo**: our major hypothesis regarding this aspect is that musical pieces tend to have a faster tempo, regarding the stressful context for the US civil society (according to literature, an increase up to 120-125 beats per minute).
    * **mode**: according to what has been presented in class, we expect an increasing equilibrium between the repartition of major and minor modalities within musical pieces.

## Dataset

### Data gathering and description of the dataset
The research is based on two datasets. The first dataset is composed of the Billboard weekly list (Billboard Top 100), between  1955 and 2017, found on the online platform [Kaggle](https://www.kaggle.com/), in csv format. This table contains 300'600 rows and eight columns, containing respectively the date of the week, the rank, the song title, the artist name, the number of weeks on charts, the musical piece's year of release, the track's popularity on Spotify and the artist popularity on Spotify. The rows between 1955 and 1958 are duplicated and low-quality data. By a brief visual evaluation of the data, it can be seen that the data concerning the Spotify database are mostly missing. The number of weeks on charts is also often false or missing.

Based on song titles and artist names from this first dataset, a query is made to the [Spotify API](https://developer.spotify.com/documentation/web-api/quick-start/) in order to retrieve the corresponding entry in the Spotify database. This requires registering with Spotify as a developer and obtaining a token to access the database. The API returns json-formatted answers. The completion of the dataset is then done in several steps. The first step is to find the corresponding identifier of each track in the Spotify database, based on the artist's name and the song title. During this first run, 69% of matches were found. In a second step, this rate is increased to 78% by isolating the main artist's name and the main tokens of the title and thus submitting a simplified request to the API.

Then, the identifier obtained for each track allows access to the track features contained in the database (danceability, energy, key, loudness, mode, speechiness, acousticness, instrumentalness, liveness, valence, duration_ms, time_signature). After that, the track audio features (tempo, mode) are also collected in a third query. Finally, a fourth query gathers the musical genre of the artists.

### Preprocessing
Data from multiple queries were merged into a single dataset. Subsequently, the billboard data was aggregated with the API data to obtain a usable dataset containing: the titles of the two databases (Billboard and Spotify), the artist name of the two databases (Billboard and Spotify), the identifier in the Spotify database, the tracks features, the audio features, a vector of the dates of each week when the track was present in the billboard chart, and a vector including the successive ranks in the billboard chart. Finally, the highest rank in the ranking is also recovered and stored. The column containing the number of weeks spent on the chart, which was of poor quality, as indicated above, was removed. It can moreover be retrieved easily for the weeks list. For reasons of data density and quality, data prior to the week of 8 August 1958 are not retained. This final preprocessed dataset is stored in json format, which unlike csv is able to deal the vector type.

The data have two biases. The first is the fact that "only" 78% of them could be retrieved from the Spotify database. However, this seems relatively acceptable bias, all the more so if we adopt the standpoint that the musical pieces that are still available today and that have been digitized are the most representative of their period. Moreover, in the timeframe finally selected, this percentage reaches 91%. The second bias is related to the margin of error of Echonest algorithms when determining features.

### Corpus selection
For reasons of data density and to be limited to the historical period covered by the research, only the rankings published between 8 August 1958 and 31 December 1995 have been kept in the corpus. The period extends after the end of the Cold War (until 1995) in order to see if post-Cold War changes in the political context may have influenced the music creation.

### Features
To address the research hypotheses, we started by selecting the variables. When the algorithm to calculate a certain variable was unknown and the definition of this variable was not commonly accepted by the majority of the scientific community, we decided not to keep it for our research. Therefore, we decided to retain only six physical variables: the duration, the time signature, the tempo, the mode, the key, and the loudness, as well as two perceptual variables (i.e. issued from psychological inquiry and then extended with a machine learning algorithm): the energy and the valence. Energy is described by Spotify as a perceptual measure of intensity and activity, and energetic tracks feel fast, loud, and noisy. Valence is described by Spotify as musical positiveness conveyed by a track. Tracks with high valence will sound more positive, while tracks with low valence will sound more negative.

### Description of the corpus
Finally, the corpus contains a total of 19,098 pieces of music representing 177,700 Billboard entries out of the 195,100 published over this period, i.e. 91%.


<img src="images/weeks_on_chart.png" alt="drawing" width="450"/>

As we can see, most musical pieces are staying less that 20 weeks on chart, with a maximum lifespan of 42.


<img src="images/features_description.png" alt="drawing" width="450"/>

Hereover, a table containing the continuous features' statistics. The perceptual variables (energy and valence) are scored on a scale without unit from 0 to 1, slightly biased upwards, but well distributed. The average duration of the songs is about three and a half minutes, with a high variance.  Tempo is measured in beat per minute (bpm), with an average of two beats per second. Loudness is measured in dB. It should be remembered that this scale is logarithmic, and that the variance is therefore greater than it seems.

<img src="images/songs_per_key.png" alt="drawing" width="450"/>


Finally, a plot displaying the distribution of the songs per key. One can observe that C is the most used root, followed by G, which is consistent with what we have seen in lectures. The diatonic scale is more used with the exception of B, which is a little less used that C#. Concerning the modality, 58% of the entries are classified as major, 18% as minor and 24% are not classified. For the time signature, 70% of the data are 4/4, 6% are 3/4, 0.6% are considered other (5:4 or 1:4) and 23.4% are not classified.


<img src="images/entries_per_year.png" alt="drawing" width="450"/>

In this plot, one can observe the first occurence of the songs per year. As the years go by, the number of unique songs entering in the top 100 diminishes. As our corpus begins the week of August 8, the year 1958 was not representative as it gives only information for 5 months and then was not plotted.

<img src="images/corr_features.png" alt="drawing" width="450"/>

One can observe that the physical variables (mode, time_signature, tempo, loudness, and duration) are only weakly correlated. The perceptual variables (energy and valence) are correlated with each other and to some of the physical variables. This is not surprising since both are covering similar perceptions of music. Energy explains the subject's perceptual sense of energy, while valence quantifies the subject's perceived positive feeling of the music. Therefore, the high correlation of energy with loudness is also intuitively expected. An interesting correlation to note is also that of energy and valence with time signature.

In total, there are 987 different musical genres and 4961 songs do not have a given genre (either empty or nan value). Following is an excerpt of the first mostly assigned genres names.

<img src="images/music_genre_tot.png" alt="drawing" width="180"/>

## Initial Analysis

### Methodology 

#### 1. Features evolution
To observe the evolution of the different features over time, annual granularity is preferred. Indeed, this granularity allows to observe trends clearly and limit noise. The 95% confidence interval is also represented so that trends can be visually identified. Categorical variables are represented according to their share in the total number of observations. 

In a second step, the salient observations are mathematically identified and extracted. To detect salient observations, the annual evolution of each feature is smoothed by convolution with a 5-year uniform smoothing filter. A replication padding is carried out to avoid shrinking. Then, the 95% interval of this representation of this smoothed annual evolution is calculated. The lower and upper bounds of this range contain non-salient observations of the distribution, while observations outside are considered salient. This procedure allows to highlight significant drifts beyond the medium-term evolution of the music, the latter being already visible in the other graphs. To also include the variations of the categorical variables, the latter are represented as integers. Finally, the salient observations of the different features are gathered in a single list so that they can represent and observe the concomitant drifts. 

#### 2. Musical genres
Due to the large amount of different genres, we decided to group them into more global categories. The latter was done based on the categorisation provided by the online database AllMusic and made easily retrivable by Wikipedia on their webpage <a href="https://en.wikipedia.org/wiki/List_of_music_styles"> List of music styles </a>. Hence, the content of the html page was extracted in order to list all genres and their corresponding subgenres into a json file <a href="https://github.com/ValentineCmoi/digital_musicology/blob/master/json/music_genres_classification.json"> music_genre_classification</a>. It was then used to assign for each subgenre of each song a main genre. When no corresponding main genre could be found, the name 'other' was attributed. Regarding this 'other' entry, it is important to understand that some genres, such as main genres listed above that corresponds to '**adult standards**', '**christmas**', '**motown**', '**mellow gold**' are not genres per se but rather categories that can group many different genres. Indeed, '**adult standards**' groups musical pieces that might be more attractive to an older audience (50 years old and above). Same applies with the '**christmas**' category, which groups songs that reffer to chrismas, and '**mellow gold**', which seems to have been invented by Spotify to group classic rock of the ‘60s, ‘70s, and ‘80s.

### Results

#### 1. Features evolution
##### 1.1 Global changes

###### 1.1.1 Root change <a name="#rootchange"></a>
<img src="images/yearly_features_change/root.png" alt="drawing" width="900"/>
We can see a dominance of the C and G tonics throughout the studied time range. However, C seems to slowly decreases in the early 90s, in favor of the C#. Others dominant roots that seem to grow over the years and compete with the two firsts in the late 70s and early 80 are D and A. The use of other roots is rather constant, with a slight increase in the use of F# in the mid 90s, whereas D# seems to vanish a bit from common usage at that same time. 

###### 1.1.2 Time signature <a id="#timesignaturechange"></a>
<img src="images/yearly_features_change/time_signature.png" alt="drawing" width="900"/>
In term of time signature, there is a great leading use of 4-time during the studied period, which even seems expand at the expense of the other types of time signatures. Hence, the 1 time signature seems to vanish, as well as the 5-time. The 3-time, which was still benefiting from a better share of percentages in the early years studied, namely around the 60s, slowly decreases and seems to reach its lower peak around the mid 80s.

###### 1.1.3 Mode <a id="#modechange"></a>
<img src="images/yearly_features_change/mode.png" alt="drawing" width="900"/>
Throughout the studied period, we can see a leading majority in the use of major modes. However, the use of minor modes slowly increases over the years and benefits from a better share of percentage of use at the end of the given time range, going from less than 20% of use in 1959 to almost 40% in 1995.

###### 1.1.4 Loudness <a id="#loudnesschange"></a>
<img src="images/yearly_features_change/loudness.png" alt="drawing" width="900"/>
<img src="images/drifts/loudness.png" alt="drawing" width="900"/>

###### 1.1.5 Duration <a id="#durationchange"></a>
<img src="images/yearly_features_change/duration.png" alt="drawing" width="900"/>
<img src="images/drifts/duration.png" alt="drawing" width="900"/>

###### 1.1.6 Tempo <a id="#tempochange"></a>
<img src="images/yearly_features_change/tempo.png" alt="drawing" width="900"/>
<img src="images/drifts/tempo.png" alt="drawing" width="900"/>

###### 1.1.7 Energy <a id="#energychange"></a>
<img src="images/yearly_features_change/energy.png" alt="drawing" width="900"/>
<img src="images/drifts/energy.png" alt="drawing" width="900"/>
The energy tends to rise slowly during the whole period, in four consequent steps. A first significant step occurs between 1962 and 1964. The second step, in 1970, appears to be driven by a salient event in June-July 1970. The third step takes place between 1973 and 1974 and the fourth and last step occurs between 1982 and 1984 and is preceded by a low-bound event which begins in September 1981 and ends in January 1982.

###### 1.1.8 Valence <a id="#valencechange"></a>
<img src="images/yearly_features_change/valence.png" alt="drawing" width="900"/>
<img src="images/drifts/valence.png" alt="drawing" width="900"/>
The valence seems to be relatively stable until 1987. It falls significantly and durably at the end of the Cold War. This decrease is progressive rather than sudden but consequent though. 

One can observe four major events in the valence salient drifts figure. The first occurs in July-August 1976, the second in November-December 1977, the third spread from March to August 1979 and the last event takes places between September 1981 to January 1982. These events occur in the form up and down cyclic events. The two last peaks are clearly visible also at year granularity. 

##### 1.2 Drifts
Example of the identification of salient drifts with regard to the general trend over 5 years. This type of graph was created for each of the eight features. The red dots represent a salient drift exceeding the upper bound of the annual average smoothed over 5 years (at a 95% confidence interval), while the blue dots represent a salient drift exceeding the lower bound of this medium-term trend.

<img src="images/drifts/drift_counts.png" alt="drawing" width="900"/>
This graph represents the sum of the drifts, month by month, for each of the eight features. Denser regions represent periods when many drifts have occurred concurrently, while higher peaks represent a cross-sectional impact on several features at the same time. The pink highlights represent the major events, defined as a suite or a stack of at least 3 events within a three-month period. 

#### 2. Musical genres
The distribution of genres was plotted using a heatmap :

<img src="images/genre_distribution.png" alt="drawing" width="2000"/>

Because of the dominance of the 'other' category, which makes it hard to perceive the distribution of other main genres, it was decided to remove it from following heatmap. Indeed, the 'other' category encompass non-musical genre classifications, such as '**adult standards**', '**christmas**' or '**mellow gold**', as well as all **_None_** attributed titles. The removal of 'other' should hence not affect the results but provides more visibility.

<img src="images/genre_distribution_nother.png" alt="drawing" width="2000"/>

As we can see on these two heatmaps, there is a prevalence of rock musics between 1964 and 1990. Country music saw a decrease of popularity throughout the 70s and hip hop songs appeared later, with early uses in 1964 and 1969 before settling down in the late 70s. In order to better understand these movements of music genres, a similar heatmap with a normalized distribution for each genre was created:

<img src="images/genre_distribution_perc_nother.png" alt="drawing" width="2000"/>

On the above, we can clearly see that hip hop seems to have reached its pick of use for the studied time range in the early 90s, similarly to caribbean and caribbean-influenced songs. Other music genres benefit from a more linear distribution over time.

A third heatmap with a normalized distribution per year was finally produced in order to better see the dominance of some genres for each year.

<img src="images/genre_distribution_perc_year_nother.png" alt="drawing" width="2000"/>

### Interpretation

#### 1. Features evolution
##### 1.1 Global changes
As we have seen from the results of the [root changes](######1.1.1-root-change), there is a certain homogeneity in-between the different keys used and the traditional use of C seems to decrease a bit toward the end of the studied period. A possible interpretation would be the fact that the end of the 21th Century was at the heart of musical explorations, which pairs with the arrival of new musical genres. Indeed, the last half of the Century saw the emergence of rock, pop or hip hop, just to name a few. This emergence is probably accompanied by a slight shift in the conventional musical instruments used, such as the guitar for rock songs.  Hence, a possible explanation of this small modulation of root used would be that composers had to find solutions in order to better suit the majority of instruments used. 

Regarding these results and the comparison with musical genres, it is interesting to see from <a href= “https://insights.spotify.com/int/2017/10/03/genres-and-key-signatures/”>Spotify insight</a> the different key signatures of each style. From their work, we can see that Rock music tends to use both C and D followed by G, which explains the similar repartition of these three root in our plot, since it seems that the genre is leading the Billboard chart in greater parts of our studied period.

In terms of time signature, the 4/4 meter is the most commonly used type in western music, and the latter is greatly showed by the obtained results. The use of 4/4 allows more time to produce notes in-between each measure, whereas the ¾ meter is much more restricted and marked as a Waltz. Another interpretation is also the fact that there is a great emergence of rock throughout these years, as well as pop, country and blues at the early stages of the studied period, which all use in majority 4 times.

The results regarding the different modes used can be addressed with respect to their affective quality. Indeed, previous <a href="https://www.jstor.org/stable/1416710?casa_token=BwZlFn70tigAAAAA:BBdwfU8J62HJlOxtoYbNibrotbpnr47ZDMI-ynZ8XFavGZseefEZT5-UN-H61DuRZKBIUB6H6L6PS1oLw9tGahhXF70tgVY22ZDo8R-07_bkVPMWQ9TB&seq=1#metadata_info_tab_contents">researches</a> have shown that major is usually felt as being more dynamic, bright, happy and more natural and fundamental than the minor. The latter would convey a darker or more depressive emotion. Hence, the slight increase of minor mode toward the end of the studied period of times can be put in correlation with the observed valence value that significantly decreases in the early 90s. These results would then mean that people at the end of the 21st Century tended to listen a bit more to more sad music, whereas the American population of the 60s was looking for more joyful music. This shift in emotion conveyed by songs can have many different interpretations, one being the change in the way people consume music. More research will have to be done toward that direction, but one could imagine that people were for example more dancing in the 60s and 70s and using music for that purpose, whereas in the 90s, with the arrival of new technologies such as the Walkman, the purpose of music consumption changed and became more of a personal experience and people were maybe looking for more strong feelings transmissions.

As explained in the introduction, valence is a perceptual variable describing the subjective positive vibe of the music. One can note that [the drop of the valence](#valencechange), at the end of the Cold War, is concomitant with the fall of rock and pop. Both represent a significative part of the corpus and in appears to be a reasonable assumption to say that both may be linked to a high valence. This can be a factor of explanation of the valence drop. Another factor could be linked to the rise of the electronical music, such as techno. It was noted in the introduction that valence and energy are correlated features. On the contrary, during this period, both follow opposite paths. The techno-related music hypothesis is plausible it the sense that it might feel more energic but not very emotional, and therefore result in a lower valence but in a higher energy.

On the other hand, the perceived [energy](#energychange) of music rises by nearly a third over the period, a very clear increase. This increase echoes also the increase in loudness. Both seem to be part of a broader economical-artistic trend that is reflected in many fields, <a href="https://journals.sagepub.com/doi/abs/10.1068/i0441aap">including e.g. cinema</a>. This movement is characterized by more frenetic artistic creations, always more stimulating for customers, in a creative context that addresses ever-increasing audiences and faces a production canonization.

##### 1.2 Major events

| Event number | Dates                  | Features changes                                | Historical events |
|--------------|------------------------|-------------------------------------------------|-------------------|
| 1            | Dec. 1959 – Feb. 1960  | low energy, low loudness                        |                   |
| 2            | Dec. 1960 – Feb. 1961  | low energy, low tempo, root change              |                   |
| 3            | Nov. 1963 – May 1964   | high loudness, short duration                   |                   |
| 4            | Jul. 1974 – Sep. 1974  | more 4/4                                        |                   |
| 5            | Mar. 1979 – Oct. 1979  | high valence, high tempo, more 4/4, root change |                   |
| 6            | Sep. 1981 – Aug. 1982  | low valence, low energy, short duration         |                   |
| 7            | May. 1983 – Jul. 1983  | high tempo, more 4/4                            |                   |
| 8            | Jan. 1984 – Apr. 1984  | high loudness                                   |                   |
| 9            | Apr. 1987 – Jun. 1987  | more 4/4                                        |                   |
| 10           | Oct. 1989 – Mar. 1990  | long duration, more 4/4                         |                   |

#### 2. Musical genres

With the different heatmaps generated, we can clearly see a dominance of rock music from the mid-60s to the early 90s. Before the rise of rock music, country music seems to have been more dominent. We can also see that musical genres, such as hip hop, caribbean and electronic appeared later on the musical scene. 

The fact that there is a greater proportion of songs listed as 'other', especially at the beginning of the studied period, in the early 60s, is explained by the fact that these years are nowadays considered as _nostalgic_ years. 'other' thus includes categories such as '**adult standards**', '**christmas**' or '**mellow gold**', which are not musical genres but groupings of a variety of musical genres based on subjective criterias. 'other' also inglobes all **_None_** attributed titles, as explained previously. 

However, another explaination of the fact that there is a prevalence of 'other' at the specific given period could be the fact that these early years were the laboratory of diverse research and novelties in terms of musical genres and that many of them were not retained by history, despite the popularity of one song at some point.

In a general way this first set of results shows the great emergence of different musical styles over the studied period. The fact that we had to group the large amount of genres to more general classes and that this evolution is still perceivable is an interesting proof of that phenomenon. The great majority of top listed titles from which rock music benefits shows not only its popularity, but is also a hint of the diversity of subgenres that occured within this style.

## Conclusion (interpretation en lien avec questions de recherche)

## Discussion (critique de la conclusion)
### Arising Difficulties

A major difficulty encountered was the diversity of genres. It was a discovery at first, because such a variety was not expected. We then had to find a suitable classification in order to group these categories. Many music styles classifications exist and can depend on the year such classifications were created and the prevalence of specific music styles. However, big classes, such as '**Rock**', '**Pop**', '**Blues**' and '**Jazz**' seem to be common to most of them. We finally chose a classification that could both show the emergence of new styles and would show the diversity of styles presented in the USA, at the years of our dataset. We then had to find online an easily retrievable classification with corresponding subgenres. In the end, the music style classification from AllMusic, made available by Wikipedia, was chosen. It corresponds the following classification:
'**blues**', '**caribbean and caribbean-influenced**', '**r&b and soul**', '**rock**', '**country**', '**electronic music**', '**folk**', '**hip hop**', '**jazz**', '**latin**', '**pop**'.

Did you encounter any difficulties? Which kind? Are they related to the data, the methods you chose, or your specific questions?

How are you going to deal with them? Propose clear and feasible solutions!

### Interesting Problems

Did you find something unexpected?

Did you encounter problems that can’t be solved given the limits of your project?

### Next steps towards the final analysis



## Literature
- Karen A. Cerula, "Social Disruption and Its Effects on Music: An Empirical Analysis", _Social Forces_, Vol. 62, Issue 4, June 1984, pp. 885-904, [Accessed on: <a href= https://doi.org/10.1093/sf/62.4.885> https://doi.org/10.1093/sf/62.4.885</a>]
- Richard A. Peterson and David G. Berger, "Cycles in Symbol Production: The Case of Popular Music", _American Sociological Review_, Vol. 40, No. 2, April 1975, pp. 158-173,  [Accessed on: <a href= https://www.jstor.org/stable/2094343> https://www.jstor.org/stable/2094343</a>]
-  Eric Clarke, Nicholas Cook, "Empirical Musicology: Aims, Methods, Prospects", Oxford University Press, 2004
- Timorhty J. Dowd, "Production perspectives in the sociology of music", _Poetics_, Vol. 32, Issue 3-4, pp. 235-246,  [Accessed on: <a href= https://doi.org/10.1016/j.poetic.2004.05.005> https://doi.org/10.1016/j.poetic.2004.05.005</a>]
- Peter J. Schmelz, "Introduction: Music in the Cold War", _The Journal of Musicology_, Vol. 26, No. 1, 2009, pp. 3-16 [Accessed on: <a href= https://www.jstor.org/stable/10.1525/jm.2009.26.1.3> https://www.jstor.org/stable/10.1525/jm.2009.26.1.3</a>]
- Matthias Mauch, Robert M. MacCallum, Mark Levy, and Armand M. Leroi, "The Evolution of Popular Music: USA 1960-2010", _Royal Society Open Science_, Vol. 2, No. 5, May 2015, [Accessed on: <a href= https://doi.org/10.1098/rsos.150081> https://doi.org/10.1098/rsos.150081</a>]
- Hevner, K. (1935). "The Affective Character of the Major and Minor Modes in Music". The American Journal of Psychology, 47(1), 103-118. www.jstor.org/stable/1416710
- Kenny Ning, Eric Humphrey, Eliot Van Buskirk, "Genres in the Key of Life: Different Music Uses Different Scales", October 2017, https://insights.spotify.com/int/2017/10/03/genres-and-key-signatures/
- Eliot Van Buskirk, "The Most Popular Keys of All Music on Spotify", May 2015, https://insights.spotify.com/us/2015/05/06/most-popular-keys-on-spotify/
- James E Cutting, Kaitlin L Brunick,  Jordan E DeLong, & others, "Quicker, Faster, Darker: Changes in Hollywood Film over 75 Years", _i-Perception_, Vol 2, Issue 6, pp.569-576, January 2011, [Accessed on: <a href= https://doi.org/10.1068/i0441aap> https://doi.org/10.1068/i0441aap</a>]

It seems that a great work was conducted during the 70s and 80s in order to understand the social significance of music and its relationship to sociological events. Indeed, the Cold War saw the emergence of major popular cultural movements. Many artistic fields, starting by art historians, were trying to understand the impact and influences of the political situation. More recently, in 2006, the <a href= http://ams-net.org/cwmsg/>AMS Cold War and Music Study Group</a> was created by the American Musicological Society in order to understand the impact of this important event on the field. However, most of these empirical studies were focusing on lyrics and genres of music, on the predominance of certain musicians on the market and on the impact of leading recording companies in the music industry. It seems that no direct analysis of the technical music properties, such as harmony, keys or tempo, and their evolution through the years was put in relationship to the sociological context. The idea would be to go as well from the performing social context to the music generated, but to determine the structural impact rather than the style or genre evolutions.
