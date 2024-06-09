# DSC232 Group Project
## Overview

This is the project repository for DSC232R Big Data Analytics with Spark at UCSD in SP24. Group Project Title: **Understanding and Predicting Spotify Trends to Improve Personalization and ROI**.

It contains a detailed analysis of a [large Spotify Audio dataset](https://www.kaggle.com/datasets/sunnykakar/spotify-charts-all-audio-data/data).

Below you can find the final writeup and here is the link to our [Jupyter Notebook](https://github.com/ntd002/DSC232/blob/Milestone4/SpotifyWorkspace.ipynb) if you'd like to explore further!

## 1. Introduction
### 1.1 Dataset Selection 
For the needs of this course and our project, we prospected a few datasets of adequate sizes. Upon investigating data sets that fit both the size requirements and was of enough relative salience and interest, we selected the [Spotify Audio dataset](https://www.kaggle.com/datasets/sunnykakar/spotify-charts-all-audio-data/data). This data set contained enough specific information and properties, and real world relevance, that it was determined as useful for exploring data science efforts.
### 1.2 Relevance: Economic & Industry Background
“The single most important distinction between “born digital” enterprises and legacy companies is not their people, data sets, or computational resources, but a clear real-time commitment to deliver accurate, actionable customer recommendations.” 
- Michael Schrage, Harvard Business Review (Schrage, 2017)

Music selection and streaming services at large are major economic drivers, with key players in this industry including Spotify, Apple Music, Amazon Music, and Tidal. Netflix, which deals with video streaming (Movies, Television Series, etc.), has a similar model: both use collaborative filtering, content-based filtering, and hybrid methods to recommend content. Machine learning models analyze user behavior, preferences, and interactions to generate recommendations.
### 1.3 Importance of Recommender Systems & Personalization
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











### 1.4 Overview of Findings
Given the salience of recommender systems in our economy, the next question is how can our model and data science efforts contribute to these practices; what follows is a broader summary of our findings and how they are discussed in the paper ahead.

Our chosen data set is composed of stream counts by region, by time period, and by track, accompanied by a myriad of metrics related to each track (energy, danceability, length, etc), and popularity is ranked and comparatively scored. This lends us to the following sense of what we can offer in the lines of recommendation systems: 
1. Our effort is not suited to perform user-level analysis/predictions/research
1. It is suited to perform region-level, track-level, artist-level, genre-level, or time period based analysis/predictions/research.

Because we were able to perform analyses around top tracks, artists, etc. in each region, and create models that reasonably predict popularity for a given track based on the accompanying metrics and information, we have decided on multidimensional clustering as a viable final tuned model output for our project. We will further discuss this process in the next sections.

 


## 2. Figures
![2429DA20-05B0-4497-AE54-8739659580BC](https://github.com/ntd002/DSC232/assets/130802143/67dbc857-3e9a-43fc-a355-cb88772a6e2f)![image](https://github.com/ntd002/DSC232/assets/130802143/f79e1ac2-52ce-4e22-95d4-7a32e3b56631)

**Figure 1:** Spotify as a global leader in streaming music subscription markets [(Mulligan, 2022)](https://www.midiaresearch.com/blog/music-subscriber-market-shares-2022
).

![B99B3902-F5DF-4F5B-8280-951AED11A0DB](https://github.com/ntd002/DSC232/assets/130802143/ffecfc92-dfbc-4efa-8932-ed8e5370a0eb)![image](https://github.com/ntd002/DSC232/assets/130802143/9256cbb2-067d-46e9-beac-977325ffef39)

**Figure 2:** Spotify quarterly revenue from 2016 to 2023 [(Iqbal, 2024)](https://www.businessofapps.com/data/spotify-statistics/).

![60500255-9BAF-4EFA-8316-F69699CECB64](https://github.com/ntd002/DSC232/assets/130802143/c356c6a8-e532-4295-92f2-f8c8f58b9476)![image](https://github.com/ntd002/DSC232/assets/130802143/441fa9d3-4744-48b9-ab68-6117e376b49e)

**Figure 3:** Spotify number of annual users from 2015 to 2023 [(Iqbal, 2024)](https://www.businessofapps.com/data/spotify-statistics/).








## 3. Methods
### 3.1 Data Exploration
[Milestone 2](https://github.com/ntd002/DSC232/tree/Milestone2): Following the [data exploration step](https://github.com/ntd002/DSC232/tree/Milestone1), we will begin the initial minor preprocessing of our dataset to prepare it for training models in the following [Milestone 3](https://github.com/ntd002/DSC232/tree/Milestone3). This process will include checking for and dropping all instances with null values for any of the columns. Next, we'll continue this method by removing any duplicate instances from our data. The dataset will be examined to review the data types of each attribute, and a decision will be made for which columns should be converted from string to integer to facilitate the application of different models. Lastly, there will be careful review to ensure that indentations, delimiters, and other formatting characteristics are considered when loading the dataset into a dataframe used for analysis. After these changes were made, we searched for subsets of the data including the top 10 artists, the top 10 regions and the top 10 songs that were referenced the most frequently in Spotify music popularity lists. In conclusion, there will be many steps taken in the initial preprocessing stage to transform our data to adopt a more useful format for our future modeling applications.





### 3.2 Preprocessing
[Milestone 3](https://github.com/ntd002/DSC232/tree/Milestone3): Preprocessing of the original dataset included creating 4 new binary columns stating whether or not a song is explicit (contains profanity), its popularity increased, decreased, or remained the same. There were also a handful of attributes whose distributions did not demonstrate a normal gaussian distribution, and were therefore normalized to be used in our machine learning models.
### 3.3 Model 1
The first few models tested were Random Forest Classifiers to determine if variables like profanity and popularity change of a song can be predicted using other attributes. 
### 3.4 Model 2
The next category of models ran were K-Means Clusters on samples of the full dataset, where attributes like energy, danceability, popularity, and valence were used to group songs together.
### 3.5 Model 3
Finally, multiple Linear Regression models were used to predict stream count using rank and popularity, predict rank using popularity and stream count, and predicting popularity using several other features.
### 3.6 Model 4: Final Model
Based on sample prototyping, we chose 5 audio metrics dimensions to create the best possible clustering analysis of every track reported by Spotify in the dataset. We chose these audio metrics for the cluster analysis as the silhouette score performed the best in comparison to other groups of columns. 

The 5 chosen dimensions are:
1. af_danceability
1. af_energy
1. af_loudness_normalized
1. af_acousticness
1. af_speechiness


This final clustering model could be useful for recommender systems, providing new tracks that are similar to a specific chosen track, or general track segmentation analysis.

While we can't visualize all 5 dimensions of our cluster model simultaneously, we can visualize 2-dimensional slices to get a feel for how the model is grouping various metrics. We will visualize four 2D slices of our trained cluster model.
To further experiment with our trained cluster model, we will pick a sample of random tracks, and then for each we will pick a random track from the same cluster as the original track. The "recommended" track may not be the same artist or genre as the original, but given the supplied 5 audio metrics, has been identified by our cluster model as being similar to the original.
## 4. Results
### 4.1 Data Exploration

![B62F16F2-7B77-421C-85CF-3B223905E8B6](https://github.com/ntd002/DSC232/assets/130802143/74f69faa-b386-4672-84dd-5c2e97fb4d6f)![image](https://github.com/ntd002/DSC232/assets/130802143/29f4222a-fbfa-4509-bd00-877f2bfa1552)
Figure 4: Datatypes of revised dataframe.

![1A3D1E1B-DAF8-47E6-A9D9-3F238DC6A220](https://github.com/ntd002/DSC232/assets/130802143/8d30eec6-c076-4125-8cb1-0d5b1c99fd65)![image](https://github.com/ntd002/DSC232/assets/130802143/d34f3669-f94e-46f9-9b9a-14c8cc648ffb)
Figure 5: Record count for top 20 regions in descending order.

![BDAD118E-5CD7-463C-B00F-8B19CDA88942](https://github.com/ntd002/DSC232/assets/130802143/e1840d9a-c2d3-493c-9088-32b3006ea986)![image](https://github.com/ntd002/DSC232/assets/130802143/03a31016-996b-4899-952d-774d49eb607a)
Figure 6: Top 20 artists whose tracks appear most frequently in the dataset.

![F03C3EB3-4AB7-4EFA-8042-BD8A37C1315B](https://github.com/ntd002/DSC232/assets/130802143/e8bbd267-ad71-4f41-bf7f-75a9f0bf8335)![image](https://github.com/ntd002/DSC232/assets/130802143/143b7720-5976-4dff-964b-535f0ba01909)
Figure 7: The stream count distribution is skewed to the right, and is a unimodal distribution with one distinct peak

### 4.2 Preprocessing

![BD1C7A27-3817-49FD-BB53-0CBF2D49A000](https://github.com/ntd002/DSC232/assets/130802143/5f831ed6-b55b-4666-92dd-bb4b525cd18f)![image](https://github.com/ntd002/DSC232/assets/130802143/e7311645-ec4c-42be-9b2d-cf51ab479421)
Figure 8: Normalization of the “af_acousticness” attribute in all records of the dataset.

### 4.3 Model 1
Random forest classifier for prediction of profanity has an accuracy of 77.4%.\
Random forest classifier for prediction of popularity increase has an accuracy of 61.5%.\
Random forest classifier for prediction of popularity increase has an accuracy of 55.8%.
### 4.4 Model 2

![176DBC60-2A3C-444A-9E9C-D9BD3D149EB6](https://github.com/ntd002/DSC232/assets/130802143/ece9fd26-1a13-4b98-8805-75ae680dccb2)![image](https://github.com/ntd002/DSC232/assets/130802143/d74e92c3-5dee-4400-97ab-123cc090b347)
Figure 9: 2-D Cluster analysis of energy and danceability attributes using 6 clusters.


Silhouette Score: 0.5492704788609065\
Silhouette Score: 0.5173897338891734\
Silhouette Score: 0.5029666184535027\
Silhouette Score: 0.46515254881357165\
Silhouette Score: 0.4442161457724867\
Silhouette Score: 0.4735004919145314\
Silhouette Score: 0.4755510964656044\
Silhouette Score: 0.45684214759467057


![70F2A628-6AE0-417D-8EB3-F932A63B6EDB](https://github.com/ntd002/DSC232/assets/130802143/a16a06e5-ce7f-45c3-b3cb-0b5db2447eed)![image](https://github.com/ntd002/DSC232/assets/130802143/f86950a7-5b13-48c9-b93b-3dc9dd382279)
Figure 10: 2-D Cluster analysis of popularity and danceability attributes using 4 clusters.

Silhouette Score: 0.8785532878495226\
Silhouette Score: 0.3273972588970275\
Silhouette Score: 0.028365477837013767\
Silhouette Score: -0.01873459539871663\
Silhouette Score: -0.020683535499144846\
Silhouette Score: -0.03338390033915237\
Silhouette Score: -0.06254580484007226\
Silhouette Score: -0.20195852169121722


![C2B82C8F-F72C-4057-B41D-B99AB87096AB](https://github.com/ntd002/DSC232/assets/130802143/be0a6e17-6112-4d35-8b09-3e1956465afe)![image](https://github.com/ntd002/DSC232/assets/130802143/2b67e02c-cbf5-4d6a-b1d0-318d78a0309a)
Figure 11: 2-D cluster analysis of popularity and valence attributes using 4 clusters.

Silhouette Score: 0.8777958005670929\
Silhouette Score: 0.25316260737768\
Silhouette Score: 0.008758324455058466\
Silhouette Score: -0.025610898137982625\
Silhouette Score: -0.03723946929681865\
Silhouette Score: -0.10253902231710126\
Silhouette Score: -0.09296600779895305\
Silhouette Score: -0.10702128533420957

### 4.5 Model 3
Our first linear regression model was used to predict stream count using rank and popularity.

Root Mean Squared Error (RMSE) on test data: 206507.528\
R-squared (R2) on test data: 0.019

The next linear regression model implemented was used to predict rank using popularity and stream count.

Root Mean Squared Error (RMSE) on test data: 57.031\
R-squared (R2) on test data: 0.017

In our final linear regression experiment, we attempted to predict popularity by adding several more features to see if this can improve the R2 score of our model.

Root Mean Squared Error (RMSE) on test data: 30.404\
R-squared (R2) on test data: 0.003


### 4.6 Model 4: Final Model

![2536DF4B-BD13-48EA-AC8E-F10D7C47250E](https://github.com/ntd002/DSC232/assets/130802143/2d2ddc02-9059-4a2b-afd9-6854b247fe36)![image](https://github.com/ntd002/DSC232/assets/130802143/83326947-98f3-4536-9fe3-2ae66ee71718)
Figure 12: Multidimensional cluster analysis shown in a 2-D slicing of danceability and speechiness attributes.

![877AAFB7-76C5-48C4-ABFA-204DA82719C6](https://github.com/ntd002/DSC232/assets/130802143/2b8ba691-5d9b-45e5-84eb-c375fcca3f7a)![image](https://github.com/ntd002/DSC232/assets/130802143/ef809f63-121a-44de-8ddf-788537bd7e31)
Figure 13: Multidimensional cluster analysis shown in a 2-D slicing of tempo and liveliness attributes.

![42FC962A-8BAA-49F4-A4D7-5583B7035669](https://github.com/ntd002/DSC232/assets/130802143/f3532cf3-9b89-4b26-9a95-5d2e31ebccea)![image](https://github.com/ntd002/DSC232/assets/130802143/698a0ed3-0c01-4275-aded-ea01521fa317)
Figure 14: Multidimensional cluster analysis shown in a 2-D slicing of valence and danceability attributes.

![A8188C01-1000-46F9-A661-9CE740EB6578](https://github.com/ntd002/DSC232/assets/130802143/00c717f8-8038-48dd-8826-998c6866fb30)![image](https://github.com/ntd002/DSC232/assets/130802143/6b7b979f-0596-4a6b-b172-58ed1cc5fbc5)
Figure 15: Multidimensional cluster analysis shown in a 2-D slicing of tempo and valence attributes.

![9E7CC065-A14A-423E-8E8B-A03A1BB29067](https://github.com/ntd002/DSC232/assets/130802143/467f941e-f87b-4581-b2da-8f38d5c1f8ed)![image](https://github.com/ntd002/DSC232/assets/130802143/eae8f28f-9e58-4e9d-9a9b-a8ea0b40750a)
Figure 16: Determining a region-specific “recommended” track using the trained multidimensional cluster model. First iteration is shown.

## 5. Discussion

### 5.1 Data Exploration
In our initial data exploration, we used the pyspark.sql.DataFrames.printSchema() syntax to return each individual column as an output as well as its corresponding data type. Additionally, we used the  pyspark.sql.DataFrame.groupBy syntax to return the top 20 regions and top 20 artists that were referenced in Spotify music popularity lists. By returning the schema of the dataframe, we were able to better understand the context of each column in the dataset. Additionally, it was interesting to see trends in the dataset such as which regions and artists are most likely to be referenced in the Spotify music popularity lists. This led us to realizing we might be better suited for interpretation at a higher level (regional, music type) rather than individual preferences. 

### 5.2 Preprocessing
The columns of “contains_cussing”, “popularity_increased”, “new_entry”, “same_position” and “popularity_decreased” were created to be implemented in Random Forest Classification models. Specifically, we were interested in seeing how accurately a Random Forest Classification model could predict whether a song contains profanity as well as how accurately the model could predict a song’s popularity.  
In retrospect, it would have been interesting to incorporate the release_date column into our analysis. This would have been a good opportunity to incorporate some time series analysis methods and extrapolate any relationships between Spotify audio metrics variables over the course of months, days or years. 

### 5.3 Models 1, 2, & 3
Our Random Forest Classification and K-Means Clustering models fit in the ideal range for model complexity, as they are neither underfit or overfit. There is a healthy difference between the test error and training error, and the test error is close to minimized. However, all of our Linear Regression models performed poorly and are severely underfit as demonstrated by the very low correlation values and high RMS error.

From our first few attempts, the Random Forest Classification models appear to yield the most promising results and can serve as a reliable tool to predict a new song’s attributes.

Interestingly, while we may assume that stream count in our data can be predicted using rank and popularity, our linear regression model returns a large RMSE and very poor R2 score, indicating a model that does not fit the data well. Reviewing a few samples by hand, it appears that oftentimes stream count does seem to be severely disjointed from rank and popularity. This would be an area to explore in more detail in the future.

While our RMSE dropped significantly when predicting rank using popularity and stream count, we still return a very poor R2 model. This indicates that perhaps our choice of features is not best for building a well-fitting linear regression model.

Our RMSE error dropped further, however our R2 score dropped as well. It appears that while we have success with our random forest and k-means clustering experiments, our linear regression analysis has shown that further feature engineering, principal component analysis, and normalization/scaling may be needed to achieve a good linear regression with this dataset.




### 5.4 Model 4: Final Model

While the multidimensional cluster model is difficult to visualize in 2 dimensions, the low silhouette scores prove the model accuracy is not ideal. More work can be done in the future to refine the combination and number of attributes/parameters we would like to use in our model to optimize the clustering. However, it is clear that the multidimensional clustering approach satisfies our project goal of creating a track recommendation systems for users based on different audio metrics, as shown in Figure 16.









## 6. Conclusion

Reflecting on our project, there are several key insights and future directions that stand out. Firstly, our choice of the Spotify Audio dataset proved to be both rich and challenging. While we were able to leverage this data to develop meaningful models, there were several limitations and areas for improvement that we encountered.

One of the main challenges was the variability and complexity of the data, which impacted the performance of our linear regression models. Despite our efforts to normalize and preprocess the data, the models exhibited poor fit, indicating that additional feature engineering and perhaps more sophisticated modeling techniques could be beneficial. For future iterations, exploring advanced methods such as neural networks or ensemble models might provide better predictive performance and capture the intricate patterns within the data.

Our Random Forest and K-Means Clustering models showed more promise, particularly in predicting song attributes and grouping tracks based on audio features. These models highlighted the potential for using machine learning to enhance recommender systems on platforms like Spotify. However, the clustering model’s low silhouette scores suggest that further refinement is needed. Future work could involve experimenting with different combinations of features, optimizing the number of clusters, and incorporating user interaction data to improve the accuracy and relevance of recommendations.

In hindsight, there are several aspects we could have approached differently. More extensive data exploration and feature selection in the early stages might have helped in identifying the most impactful variables for our models. Additionally, incorporating external datasets, such as user demographic information or social media trends, could provide a more holistic view and improve the robustness of our predictions.

Another important direction for future research is real-time model updating and adaptive learning. As user preferences and trends in music are constantly evolving, integrating a feedback loop where the model updates based on new data and user interactions can significantly enhance the personalization and effectiveness of the recommender system.

Overall, this project has been a valuable learning experience, demonstrating the complexities and opportunities in applying big data analytics to real-world problems. While we have made significant progress in understanding and predicting Spotify trends, there is ample room for further exploration and improvement. Our work lays a foundation for future efforts to develop more sophisticated and accurate personalization systems that can enhance user experience and drive economic value for streaming platforms. Our track recommendation model will undoubtedly enable new breakout artists’ songs to reach previously unattainable audiences. With the potential of a growing fanbase, more artists may consider using Spotify as a platform which would increase revenue for both artists and Spotify. Amidst this, the users now have a wider variety of artists to listen to and enjoy.





## 7. Statement of Collaboration
### Name: Alex Hayslip
- Title: 
- Contribution: Wrote code for data exploration, preprocessing and modeling in a local environment. 

### Name: Chris Scholz
- Title: 
- Contribution: Porting and centralizing locally-developed prototype code into single notebook in SDSC, sourcing and managing dataset within SDSC.

### Name: Kian Mohseni
- Title: Multi
- Contribution: Chose the dataset, wrote and edited Abstract, helped create and format Github repositories and branches, drafted README.md files for Data Exploration & Preprocessing branches, code review & model suggestions, writing final report.

### Name: Nathaniel Do
- Title: Debugger
- Contribution: Coding/debugging, feedback, preprocessing problem solving regarding the dataset.

### Name: Jesse Parent
- Title: 
- Contribution: Documentation, code review, writing/editing.



## References
- Björklund, G., Bohlin, M., Olander, E., Jansson, J., Walter, C.E., Au-Yong-Oliveira, M. (2022). An Exploratory Study on the Spotify Recommender System. In: Rocha, A., Adeli, H., Dzemyda, G., Moreira, F. (eds) Information Systems and Technologies. WorldCIST 2022. Lecture Notes in Networks and Systems, vol 469. Springer, Cham. https://doi.org/10.1007/978-3-031-04819-7_36
- Mulligan, M. (2022, December 7). Music subscriber market shares 2022. Midia Research. Retrieved June 4, 2024, from https://www.midiaresearch.com/blog/music-subscriber-market-shares-2022
- Schrage, M. (2017, August 1). Great Digital Companies Build Great Recommendation Engines. Harvard Business Review. Retrieved June 4, 2024, from https://hbr.org/2017/08/great-digital-companies-build-great-recommendation-engines
- Iqbal, M. (2024, May 7). Spotify Revenue and Usage Statistics. Business of Apps. Retrieved June 4, 2024, from https://www.businessofapps.com/data/spotify-statistics/







