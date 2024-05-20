# DSC232

Preprocessing of the original dataset included creating 4 new binary columns stating whether or not a song is explicit (contains cussing), its popularity increased, decreased, or remained the same. There were also a handful of attributes whose distributions did not demonstrate a normal gaussian distribution, and were therefore normalized to be used in our machine learning models.

The first few models tested were Random Forest Classifiers to determine if variables like profanity and popularity change of a song can be predicted using other attributes. The next category of models ran were K-Means Clusters on samples of the full dataset, where attributes like energy, danceability, popularity, and valence were used to group songs together. Finally, multiple Linear Regression models were used to predict stream count using rank and popularity, predict rank using popularity and stream count, and predicting popularity using several other features.

Our Random Forest Classification and K-Means Clustering models fit in the ideal range for model complexity, as they are neither underfit or overfit. There is a healthy difference between the test error and training error, and the test error is close to minimized. However, all of our Linear Regression models performed poorly and are severely underfit as demonstrated by the very low correlation values and high RMS error.

From our first few attempts, the Random Forest Classification models appear to yield the most promising results and can serve as a reliable tool to predict a new song’s attributes. We will look to further refine these models by attempting to tune the parameters and combinations of inputs used.
