# DSC232 Group Project
See also: [Project Abstract](https://github.com/ntd002/DSC232/blob/Milestone1/Spotify%20Audio%20Data%20Abstract.pdf)

## Milestone 2 Overview
Following the [data exploration step](https://github.com/ntd002/DSC232/tree/Milestone1), we will begin the initial minor preprocessing of our dataset to prepare it for training models in the following [Milestone 3](https://github.com/ntd002/DSC232/tree/Milestone3). This process will include checking for and dropping all instances with null values for any of the columns. Next, we'll continue this method by removing any duplicate instances from our data. The dataset will be examined to review the data types of each attribute, and a decision will be made for which columns should be converted from string to integer to facilitate the application of different models. Lastly, there will be careful review to ensure that indentations, delimiters, and other formatting charactersitics are considered when loading the dataset into a dataframe used for analysis. In conclusion, there will be many steps taken in the initial preprocessing stage to transform our data to adopt a more useful format for our future modelling applications.

We installed Plotly in our Jupyter Environment to create visuals of our data. Enter the following code into your Jupyter Terminal to perform this installation:

  !pip install plotly --upgrade
