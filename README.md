# Overview
This is a project respository for DSC232 Big Data Analytics with Spark | Group Project Title: **Understanding and Predicting Spotify Trends to Improve Personalization and ROI**

[UNFINISHED]

## 1. Introduction 

### Dataset Selection
For the needs of this course and our project, we prospected a few datasets of adequate sizes. [Perhaps vaguely mention other data sets we considered, and why they were less appealing]. Upon investigating data sets that fit both the size requirements and was of enough relative salience and interest, we selected the Spotify dataset [link to either notebook or original data set]. This data set contained enough specific information and properties, and real world relevance, that it was determined as useful for exploring data science efforts.

### Relevance: Economic Impact and Industry Background 
“The single most important distinction between “born digital” enterprises and legacy companies is not their people, data sets, or computational resources, but a clear real-time commitment to deliver accurate, actionable customer recommendations.”  - Michael Schrage, Harvard Business Review (Schrage, 2017)

Music selection and streaming services at large are major economic drivers, with key players in this industry including Spotify, Apple Music, Amazon Music, and Tidal. Netflix, which deals with streaming video (Movies, Television Series, etc), has a similar model: both use collaborative filtering, content-based filtering, and hybrid methods to recommend content. Machine learning models analyze user behavior, preferences, and interactions to generate recommendations.

#### Importance of Recommender Systems & Personalization
Accurate and actionable recommendations contribute to many areas of the streaming economy. Here is a list of key reasons in this space:
1. User Engagement and Retention:
   1. Personalized Playlists: Spotify's "Discover Weekly" and "Release Radar" playlists are examples of how personalized recommendations can keep users engaged by introducing them to new music tailored to their tastes.
   1. User Experience: A personalized experience makes the platform more enjoyable and user-friendly, encouraging users to spend more time on the app.
1. Content Discovery:
   1.Long Tail Content: Recommender systems help users discover less popular or niche content that they might not find otherwise, increasing the overall consumption of the platform's library. See Björklund et al (2022), which indicates nearly half of the time the Spotify users place the recommended songs in their playlist.
   1. Artist Exposure: New and lesser-known artists can gain exposure through personalized recommendations, which can be crucial for their growth and success.
1. Economic Impact:
   1. Increased Revenue: By keeping users engaged and satisfied, personalized recommendations can lead to higher subscription rates and reduced churn, directly impacting the company's revenue.
   1. Advertising: For free-tier users, personalized ads can be more effective, leading to higher ad revenues.
   1. Data Monetization: The data collected through user interactions with personalized content can be valuable for market research and targeted marketing campaigns.

From user engagement and retention, to content discovery, to economic impact, it’s clear that recommender systems are valuable. 

### Overview of Findings
 
Given the salience of recommender systems in our economy, the next question is how can our model and data science efforts contribute to these practices; what follows is a broader summary of our findings and how they are discussed in the paper ahead.

Our chosen data set is composed of stream counts by region, by time period, and by track, accompanied by a myriad of metrics related to each track (energy, danceability, length, etc), and popularity is ranked and comparatively scored. This lends us to the following sense of what we can offer in the lines of recommendation systems: 
Our effort is not suited to perform user-level analysis/predictions/research
It is suited to perform region-level, track-level, artist-level, genre-level, or time period based analysis/predictions/research

Because we were able to perform analyses around top tracks, artists, etc in each region, and create models that reasonably predict popularity for a given track based on the accompanying metrics and information, we have decided on multidimensional clustering as a viable final tuned model output for our project. We will further discuss this process below: we will cover Figures (B), Methods (C), Results (D), Discussion, and Conclusion (F). 





## 2. Figures

## 3. Methods
### Data Exploration
### Preprocessing: 
### Model 1
### Model 

## 4. Results
### Data Exploration
### Preprocessing: 
### Model 1
 


## 5. Discussion 
### Data Exploration: Exploratory Data Analysis (EDA)
### Preprocessing: 
### Model 1
### General Discussion 

## 6.Conclusion

## 7. Collaboration 

 







# To-Be Archived: Previous ReadMe Structure
## Materials
- Written Report (forthcoming)
- [Project Abstract](https://github.com/ntd002/DSC232/blob/Milestone1/Spotify%20Audio%20Data%20Abstract.pdf)
- [Milestone 1](https://github.com/ntd002/DSC232/tree/Milestone1)

## Milestone 2
[Milestone 2](https://github.com/ntd002/DSC232/tree/Milestone2): Following the [data exploration step](https://github.com/ntd002/DSC232/tree/Milestone1), we will begin the initial minor preprocessing of our dataset to prepare it for training models in the following [Milestone 3](https://github.com/ntd002/DSC232/tree/Milestone3). This process will include checking for and dropping all instances with null values for any of the columns. Next, we'll continue this method by removing any duplicate instances from our data. The dataset will be examined to review the data types of each attribute, and a decision will be made for which columns should be converted from string to integer to facilitate the application of different models. Lastly, there will be careful review to ensure that indentations, delimiters, and other formatting charactersitics are considered when loading the dataset into a dataframe used for analysis. In conclusion, there will be many steps taken in the initial preprocessing stage to transform our data to adopt a more useful format for our future modelling applications.

## Milsteone 3
[Milestone 3](https://github.com/ntd002/DSC232/tree/Milestone3): Preprocessing of the original dataset included creating 4 new binary columns stating whether or not a song is explicit (contains cussing), its popularity increased, decreased, or remained the same. There were also a handful of attributes whose distributions did not demonstrate a normal gaussian distribution, and were therefore normalized to be used in our machine learning models.

The first few models tested were Random Forest Classifiers to determine if variables like profanity and popularity change of a song can be predicted using other attributes. The next category of models ran were K-Means Clusters on samples of the full dataset, where attributes like energy, danceability, popularity, and valence were used to group songs together. Finally, multiple Linear Regression models were used to predict stream count using rank and popularity, predict rank using popularity and stream count, and predicting popularity using several other features.

Our Random Forest Classification and K-Means Clustering models fit in the ideal range for model complexity, as they are neither underfit or overfit. There is a healthy difference between the test error and training error, and the test error is close to minimized. However, all of our Linear Regression models performed poorly and are severely underfit as demonstrated by the very low correlation values and high RMS error.

From our first few attempts, the Random Forest Classification models appear to yield the most promising results and can serve as a reliable tool to predict a new song’s attributes. We will look to further refine these models by attempting to tune the parameters and combinations of inputs used.

## Milstone 4
[Milestone 4](https://github.com/ntd002/DSC232/tree/Milestone4?tab=readme-ov-file) 
