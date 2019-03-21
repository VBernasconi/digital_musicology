### Digital Musicology
# Understanding the impact of the Cold War on Billboard Charts:  _When the american society reflects on music creation_

### Dataset: [Spotify API](https://developer.spotify.com/documentation/web-api/quick-start/)

### Introduction
The Cold War period, whose studied years for this project are from 1958 to 1995, saw the rise of many major and diverse cultural movements. This flourishing time also enabled an important increase in the diversity of musical genres. Regarding these prompt changes and the socio-econo-political climate, we would like to understand how major genres evolved over time and try to determine, in a second phase of the project, the possible correlations with corresponding important events. In order to conduct the research, we worked with the Billboard Charts that weekly provides the top 100 listened musics in the United States.

### Research Question and Hypothesis
Regarding our main research question, which is to understand the evolution of music from 1958 to 1995 and how it might have been impacted by contemporary events, we developed two major hypothesis that will have to be validated or invalidated throughout the conduct of the project:
1. Based on the following 6 selected features, we expect to see significant variations in a selected range of major genres:
    * **key**: no specific hypothesis was determined regarding this feature.
    * **loudness**: it corresponds to the overall loudness of a track in decibels (dB). A hypothesis would be to have an increase of loudness in rock-related genres musics.
    * **duration_ms**: our hypothesis is that the duration of musics tend to be shorter, regarding the growing stressful context.
    * **time_signature**: our hypothesis is that, regarding the experimental artistic context, some new time signatures might arrise, however there should be an important convergence to a 4:4 time signature (regarding the fact that there are no valses).
    * **tempo**: the major hypothesis regarding this aspect it that musics tend to have a faster tempo, regarding the stressful context of their productions
    * **mode**: according to what has been presented in class, we expect an increasing equilibrium between the repartition of major and minor modalities within musics.
The two major hypothesis regarding these features are that music will tend to be shorter and tempo faster (according to literature, an increase up to 120 to 125 beats per minute)
2. According to the increasing diversity of genres, we assume that the difference for the above features in-between similar genres, such as all the pop variety, is minimal.

### Data description

#### Datasets
The research is based on two datasets. The first dataset is composed of the Billboard weekly list (Billboard Top 100), between  1953 and 2017. For reasons of data density and to be limited to the historical period covered by the research, only the rankings published between 8 August 1958 and 31 December 1995 have been kept in the corpus. The period extends after the end of the Cold War in order to see if changes in political situation may have influenced the music creation. 

#### Genre selection
Because of the important variety of genres that appeared throughout the studied period from 1955 to 1990, we decided to group them under the following more general categories:
* **Pop**: the Pop genre groups all its derivative, such as New wave pop, Brill building pop, Bubblegum pop, adult standards....
* **Rock**: [soft rock, album rock, folk rock, classic rock, rock and roll]
* **Country**: Country music and its derivative, such as country rock
* **Reggae**
* **Disco**: [disco, post-disco, funk]
 * **Electro**
* **Soul**: [classic soul, southern soul, quiet storm]
* **R&B**: [urban contemporary]
* **Metal**: [ hard rock, psychedelic rock, grunge]
* **Blues**: [british blues]
* **Jazz**: [jazz funk, vocal jazz]
* **Folk**

### Concepts
To address the research hypotheses, we started by selecting the variables. When the algorithm to calculate a certain variable was unknown and the definition of this variable was not commonly accepted by the majority of the scientific community, we decided not to keep it for our research. Therefore, we decided to retain only six physical variables : the duration, the time signature, the tempo, the mode, the key, and the loudness, as well as two perceptual variables (i.e. issued from psychological inquiry and then extended with a machine learning algorithm) : the energy and the valence.


### Methods
We seek to highlight differences in Billboard chart top songs' audio features during and after the Cold War. To do so, we plan to use mathematical indicators to identify the metadata that are most strongly correlated with event indicators. We also plan to establish a regression between metadata and event indicator. Categorical data will be processed by dummy variable encoding. To determine which events have the greatest impact on the evolution of music and also which musical variables are the most impacted, we will use the Principal Component Analysis method.

### Literature
- Karen A. Cerula, "Social Disruption and Its Effects on Music: An Empirical Analysis", _Social Forces_, Vol. 62, Issue 4, June 1984, pp. 885-904, [Accessed on: <a href= https://doi.org/10.1093/sf/62.4.885> https://doi.org/10.1093/sf/62.4.885</a>]
- Richard A. Peterson and David G. Berger, "Cycles in Symbol Production: The Case of Popular Music", _American Sociological Review_, Vol. 40, No. 2, April 1975, pp. 158-173,  [Accessed on: <a href= https://www.jstor.org/stable/2094343> https://www.jstor.org/stable/2094343</a>]
-  Eric Clarke, Nicholas Cook, "Empirical Musicology: Aims, Methods, Prospects", Oxford University Press, 2004
- Timorhty J. Dowd, "Production perspectives in the sociology of music", _Poetics_, Vol. 32, Issue 3-4, pp. 235-246,  [Accessed on: <a href= https://doi.org/10.1016/j.poetic.2004.05.005> https://doi.org/10.1016/j.poetic.2004.05.005</a>]
- Peter J. Schmelz, "Introduction: Music in the Cold War", _The Journal of Musicology_, Vol. 26, No. 1, 2009, pp. 3-16 [Accessed on: <a href= https://www.jstor.org/stable/10.1525/jm.2009.26.1.3> https://www.jstor.org/stable/10.1525/jm.2009.26.1.3</a>]
- Matthias Mauch, Robert M. MacCallum, Mark Levy, and Armand M. Leroi, "The Evolution of Popular Music: USA 1960-2010", _Royal Society Open Science_, Vol. 2, No. 5, May 2015, [Accessed on: <a href= https://doi.org/10.1098/rsos.150081> https://doi.org/10.1098/rsos.150081</a>]

It seems that a great work was conducted during the 70s and 80s in order to understand the social significance of music and its relationship to sociological events. Indeed, the Cold War saw the emergence of major popular cultural movements and many artistic fields, starting by art historians, were trying to understand the impact and influences of the political situation. More recently, in 2006, the <a href= http://ams-net.org/cwmsg/>AMS Cold War and Music Study Group</a> was created by the American Musicological Society in order to understand the impact of this important event on the field. However, most of these empirical studies were focusing on lyrics and genre of musics, the predominance of certain musicians on the market and the impact of leading recording companies in the music industry. It seems that no direct analyse of the technical music properties, such as harmony, keys or tempo, and their evolutions through the years was put in relationship to these sociological context. The idea would be to go as well from the performing social context to the music generated, but to determine the structural impact rather than the style or genre evolutions.
