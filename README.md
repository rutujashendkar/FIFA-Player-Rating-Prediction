
<p align="center">
  <img width="800" height="200" src="https://user-images.githubusercontent.com/92499217/167567881-8283befb-9d29-48dc-885f-ec595319787a.png">
</p>

# Introduction

In FIFA, each player has an overall rating which is calculated based on several statistics such as age, skills in passing, shooting, preferred foot, body type, potential, stamina, sprint speed etc. This repository focuses on player data obtained from FIFA 19 to determine the significant features which help in predicting the overall rank of the player by using linear regression via Statistical Method as well as Machine Learning Method. 
Dataset
The dataset used has been sourced from Kaggle. It has 18207 rows and 89 columns having numerical as well as categorical columns.
The data has all the possible matrices a player can have and some of them are given as a ranking compared to other players. All the players have received the ratings based on their performances in the previous games. The data has ratings of each player for each position. Let's suppose a forward player will obviously have a bad rating in defending. 
Upon doing the descriptive analysis, it was found that the mean age of the players was found to approximately 25 years with a standard deviation of 4.6 years. A mean acceleration of 64.61 and SprintSpeed of 64.72 was observed among the players. On comparing 75% of values for several features to their respective max feature, it is obvious that there are many outliers.

# Project Lifecycle

![Fifa project cycle](https://user-images.githubusercontent.com/92499217/167568835-623475a0-6ef1-402b-8105-d0f6aebc8c53.PNG)


# Data Cleaning and Pre-processing
In data cleaning, the columns that were of no use like Jersey No., Loaned from, ID were dropped. Secondly, the NULL values were treated for categorical and continuous columns. For categorical features, Simple Imputer was used with strategy as ‘most frequent’ and for numerical columns, median was used to replace the null values. A new column was created named ‘Experience’. This was done by subtracting two values - joined year & 2019. Datatype conversion was also done on a few columns.

# Assumption Testing  

- Assumption-1 Normality Test 
 To check the normality of the residuals, the Jarque Bera test was used . The data should follow normal distribution due to various statistical reasons. The result of the test was – (statistic=693.0073725550892, p value=0.0). As the p value is lower than the significance level it shows that the residuals does not follow normal distribution.

- Assumption-2 Multi collinearity
The features in the dataset should not be correlated that causes confusion in the study because the variables are too closely related. To check multicollinearity, Variance Inflation factor was used. Most of the VIF values are below 10 which shows that features are not collinear.

- Assumption-3 Constant variance of residuals
Variance means error. If the model we have built has high variance among the values, the accuracy will be low . When there is heteroscedastic, it results in inefficient point estimates and biased estimates of standard errors, and may result in overestimating the goodness of fit  as measured by the Pearson coefficient .
To check this goldfeld-quandt test was performed and the result is (1.0098270212536673, 0.32089458843022417, 'increasing'). P value is higher than the significance level which proves that there is constant variance of residuals.

- Assumption-4 Autocorrelation
Autocorrelation is the measure of the degree of similarity between a given time series and the lagged version of that time series over successive time periods.  For a good model there should be no autocorrelation.
Durbin-Watson value is 1.94(very close to 2) indicating no strong autocorrelation.

- Assumption-5 Linearity of the Relationship 
The basic idea of the Rainbow test is that even if the true relationship is non-linear, a good linear fit can be achieved on a subsample in the "middle" of the data. The null hypothesis is rejected whenever the overall fit is significantly worse than the fit for the subsample. 
When the rainbow test was performed on the dataset, the result obtained was (1.013798082344859, 0.2569460350867301) which shows that the P value is greater than the significance level which proves that the data follows a linear relationship.

# Models
The main objective of the model is to predict the overall rating of the player based on different skills, wages, experience, age, nationality, preferred foot type etc. A linear regression model was preferred for this dataset. Passing of the dataset in some of the assumptions test of linear regression also favours the use of linear regression technique in the model. Label encoding was preferred where categorical variables were having a large number of unique values, for the leftover categorical variable which have only two unique values, the get_dummy method was used.

Both, statistics model and machine learning model were developed for the analysis of target variables. In the analysis, a backward elimination approach was preferred to find the significant variable for the statistics model, However, for machine learning model, forward feature selection technique was used to filter the features. At the end, it was observed the R square value of the statistics model was 0.931 showing that the the model is good to go. For machine learning model, R square value for test data was 0.92943, which conveys that the model explained 92.94% of target variable variance. 

# Conclusion

- While plotting histogram of age we found a high number of players belonging to the age category of 20 to 28 and this trend decreased afterward. 
- Count of players with field positions like goalkeeper , centre back and striker is very high but very less for right attacking midfielder and right forward.
- The median shot power of the left preferred player is very high with no outlier on the minimum side. It indicates that if the player is using his left foot, he is more likely to have high shot power. However, the right foot player has more control over the ball.
- Potential of a player generally shows a decreasing trend with age after 30, it might be due to injuries or ageing factor.
- The famous clubs like 'Juventus', 'Real Madrid', 'Paris Saint-Germain', 'FC Barcelona', 'Legia Warszawa', 'Manchester United etc. show overall rating around 80 or above

After feature selection, it was found that Agility, dribbling skill, stamina, long shots, field position like LB, RB, LCM, CM and RCM etc are not significant for the overall rating of the player.

However, Age, Potential, Aggression, Interception, strength, wage, experience etc came out as significant variables. It was observed that the R square value of the model is 0.92943189, which explains good amount of variance present in the target variable. The difference in the R square value of test and train data was not significant, hence, the model does not require further optimization. There is a chance to make the model more efficient by removing variables that are showing a high variance influencing factor.

