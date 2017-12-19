# Evolution of sustainable development interests in society during the last century

# Group members

- Mathilde Guillaumot
- Priscille Guerrier de Dumast
- Hippolyte Lefebvre

# Abstract
In a time where ressources are diminishing and population is growing, the theme of sustainable development is naturally becoming central in topical issues. When we see the state of our planet it raises a lot of questions on our lack of interest on these issues and the difficulty to integrate them in the social most important matters. Our main goals are to understand how sustainable development related thematics are now interfering with topical society’s interests and how it is received by its people. Also, it is important to understand in which context we talk about those issues and how we talk about them. Do authorities and media like newspapers act in favor of giving a bigger place for this theme on the politics plate or not? In order to draw up an analysis on this trend, we are going to use the archives of the Gazette de Lausanne and the Journal de Genève that gather 200 years of journalistic work and have followed society main interests over the time.

# Research questions
- An interesting question is about trying to understand to what extent sustainable development related subjects are expanding in the news and when social authorities through newspaper media started to initiate a raise in people’s awareness of the way to deal with our ressources and the way we split it between all human population. 
- Another interesting fact is to see that it is a dividing subject between people who believe in taking good care of our planet to make it flourish and the ones who do not have this long term vision and are simply not affected by those matters. In that sense, it would be interesting to see in which context we are talking about these issues, i.e. when talking about ecology only or also when debating of education needs, economy and all these various aspects of our society. Is it done in a positive or negative way?
- Wrongly, some people tend to picture a sustainable development activist as a what we used to call a « hippie ». What has lead people to think that? What is the media responsibility in it?

# Dataset
The dataset provided by Le Temps gathers 200 years of newspapers archives is a mine of information on society’s interests trends over the time. We want to explore it with our prism regarding sustainable development and provide an analysis on this topic’s vision and evolution over the time. When did we start to talk about sustainable development? It was certainly not mentioned in those terms at the time, what did set the stage to this matter? This dataset is wide and gives us the opportunity to explore a lot of data. First of all, we intend to focus on the last 100 years of archives because we consider that prior to that time, there is not much to find on these problematics in the newspaper. Le Temps archives website enables us to explore the data and research information by name entities. Indeed, when typing the term sustainable development, a graphic is displayed showing the occurrences of this term and not much is found in the 19th century. Secondly, we intend to focus on newspaper articles titles to explore the data. We think that titles reveals the spirit of an article enough to extract consistent information from it only. Also it will in a way, reduce our amount of data and make it easier for us to process and analyze it at first. 
At this stage of the project, we have not played around enough with the dataset to give more explanation on the way we are certain to analyze the data. For now, we have focused, as stated above, on delimiting the amount of data we want to consider of our analysis.


# A list of internal milestones 

### Milestone 1

Get the data of the 2 newspapers (Journal de Genève and Gazette de Lausanne), predecessors to Le Temps, and start exploring it using Pandas in an IPython notebook.

Play with SPARQL request from the website to get on-demand and precise data.
http://www.letempsarchives.ch/sparql

Fill the project repo with a notebook containing data collection and descriptive analysis, properly commented.

Update the notebook with a more structured and informed time plan for what comes next (till the presentation).


### Milestone 2

For this second milestone we had as a main goal to perform a first exploration of our data and identify some trends that we will need to analyze for Milestone 3. We also considered this milestone as a step to settle or not our project ideas and identify the possible constraints. We expressed in our TA questions of milestone 1 the question of using 100 or 200 years of data and decided to take the last 100 years as recommended. So we ran our first analysis as followed:

- We loaded the data of the 2 newspapers (Journal de Genève and Gazette de Lausanne) and started to process it in order to obtain a clean and useable dataset. Indeed, there were under XML format so we used beautiful soup parser to extract the data. The final purpose was to get the dataset into two lists for each journal : one gathering the articles names and the other the issue dates of these articles. We obtained the two sets of lists containing each more than 2 million articles.

- Using pandas, and after some format conversion, we created two data frames corresponding to each newspaper's articles and related issue dates.

- We wanted to know when the public sphere got interested into the environnement related subjects. So as a first simple analysis, we went through all the articles titles and tried to see if the terms "environnement" and "écologie" were frequently expressed during the XXth century. It resulted in the creation of data frames with only the rows of articles mentioning these terms in their title. For name matching we used the "str.contains" method.

As a result, we displayed a countplot with the number of occurences of the terms in articles titles per year and saw that the numbers of articles published which title contained one of the two terms were the highest between 1985 ad 1990. These results seem coherent at first sight because sustainable development and green concerns were discussed a lot during the eighties. Results are pretty much the same for both newspapers.

But we definitely need to expand our matching "green" vocabulary list because currently, with our methods, by scanning for "écologie" we also get words like "gynécologie". Moreover we need to pay attention to words such as "environment" that can mean different things (such as cultural environment, social environment, etc...). The main idea for us now is to dig into the ecology documentation to create a robust list of terms that will help us find out when the main peaks of interest in ecology were during the 20th century using the occurences plots mentioned above.  

As a second step after having tried our expanded list, and if the results seem to be still perfectible, we consider scanning directly in each article but this will be highly computer consuming.

As indicated above, a challenge will be to expand our matching list and to find out if it exists some more powerful matching function. Why not Sequence matcher we used for HW2 ?

Once the pre-processing will be considered optimal we have two main objectives:

- We want to learn in which context we used to talk about ecology at the time and we want to know how these articles are related to other subjects. Thus, we want to apply some machine learning algorithms to the selected ecology friendly articles by retrieving the full articles text and try to learn the context of the articles by finding out to which subjects these articles were related (economy? politics?, etc...). (This will be done in the same spirit as in HW 4)

- As a wish to implement techniques we have seen in class, we also thought of displaying a map gathering occurences counts per canton even though we are aware that the two newspapers were local newspapers (Geneva and Lausanne) and for some neighbor countries such as France, Germany or Italy. 


### Milestone 3

From Milestone 2, we have determine a list of steps to perform to get to good topic modeling:
- Step 1: How many untitled articles over time and total are there in the datasets? After having dealt with this question, we can choose a strategy to deal with untitled articles
- Step 2: Grow our taxomony list of words to extract "green" articles from the dataset
- Step 3: Filter "green" articles by title and then retrieve full content
- Step 4: Statistics on extracted articles (problem need to be qualified and quantified)
- Step 5: Perform topic modeling

Step 1: 

Regarding the amount of untitled articles, we could not just drop them out of our dataset. Fortunately, it appeared that very frequently the main topics treated in one article were mentioned at the very beginning of the article content so we matched our list of words with the 100 first characters of each untitled article with pretty good results even if only less than 100 hundred articles for each journal were retrieved it is always articles that needed to be present in our processed dataset despite missing a title.

Step 2:

We established at first a list of almost 200 key words from the ecological lexical. We decided to limit ourselves with 58 words because of the rarity of their use in the french language and the amount of data to process. 21 words out of these 58 ones were retrieved in one or both of the journals (GDL and JDG):

’agriculture durable’, ’biodiversité’,’biodégradable’, ’biomasse’, ’biotope’, ’biozone’,’changement climatique’, ’climax’,’compostage’,’diversité’, biologique’, ’déforestation’, ’environnement’,’environnemental’, ’espace vert’, ’gaz à effet de serre’, ’micro-climat’, ’reboisement’,’réchauffement climatique’, ’réchauffement global’, 'écologie', 'écotaxe'

Step 3: 

This time we used the "re" package and its search fonction to fully match words and avoid mistakes such as "écologie/gynécologie" like we got previously. After what, we extracted the articles matching one of the "green" words.
Again, based on the amount of data we had at our disposal we retrieved "green" articles full text from our lists of articles titles which matched words in our 58 words long list defined. 

Step 4: 

We noticed that the two main represented words were "environnement" and "écologie" which could be expected. We had to verify that the predominance of the word "environnement" was not due to its massive use in several contexts but it appeared that it was indeed mostly related to "green" subjects and topic modeling proved that it did not bring too much bias keeping the eventual articles not related to "green" subjects but mentioning the word "environnement". What is interesting is that these two words distributions in both journals are really similar. This may indicate that ecology is covered by the two journals in the same way which is not unreasonable since the two newspapers should cover the same local news due to their geographical proximity.
The time period that is mostly concerned with these "green" subjects seem to be 1982-1992 which would coincide with global green awareness and with some ecological disaster (such as Tchernobyl).

Step 5: 

Topic modeling has enable us to portray what were the association between topics learnt and the categories of articles retrieved by a specific "green" word. It also showed that our analysis assumptions were acceptable as the topics extracted from our data related to "green" topics. The top words of the topics learnt also got to tell more about the themes that were associated with one category of "green" subject. 


Regarding work split, we did as following:

- Mathilde Guillaumot: Data pre-processing, Handling of untitled articles, Green articles extraction and analysis, Topic modeling, Wrote the report + Readme updates (Will be presenting the poster)

- Priscille Guerrier de Dumast: "green" words matching list and means to retrieve green articles

- Hippolyte Lefebvre: Selection and processing of keywords and full list matching with the two datasets with extraction of match words, readme updates


# Questions for TAs

### Milestone 1

- We saw that data are heavy, and available on the cluster. Do we need a VPN to access it ? 

- Would you recommend study the 200 years and then potentially keep only the last 100 ? Or directly work on the last 100 ?

### Milestone 2

- Using only the articles titles seems a bit biased to us to really identify articles dealing with sustainable content. Would you recommend processing all the articles content even though it will be highly computer consuming ? We believe that on more than 2 million articles, this may not be necessary because our dataset is huge. 

- When digging into the dataset we found some "Untitled Article" titles, we decided arbitrarly to get rid of these ones, is this assumption going to bias the results much? Unfortunately, we have to make choices in order to reduce the amount of data...
