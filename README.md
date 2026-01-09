# DSA-210-PROJECT

# Introduction 
The aim of this project is to investigate whether the amount of time a player spends on a game (playtime) has a statistically significant impact on their likelihood to recommend the game on Steam. The project analyzes a dataset of over 200,000 user reviews to assess if "Hours Played" is a reliable predictor of user satisfaction. By comparing the playtime distributions of positive and negative reviews, this study aims to reveal whether deeper engagement correlates with positive sentiment.

# Hypothesis
Players who recommend a game have significantly higher average playtime compared to players who do not recommend the game.

# Motivation  
I wanted to explore the relationship between time investment and player satisfaction. Does playing a game for hundreds of hours guarantee a positive review? Conversely, do negative reviews come mostly from players who bounced off quickly? Understanding this relationship can provide insights for game developers regarding player retention and satisfaction.

# Data Source 
The dataset used in this project is the **Steam Game Reviews** dataset, sourced from Kaggle. It contains individual user reviews for various games on the Steam platform.

Key features used for each review include:

#### •Review Text (Content of the review)

#### •Hours Played (Numeric value of hours at time of review)

#### •Recommendation (Binary: "Recommended" or "Not Recommended")

#### •Game Name

#### •Date

The raw dataset contained approximately 231,000 entries. Since the data is from a public Kaggle dataset, there are no ethical or privacy concerns associated with this analysis.

# Project Plan 
#### 1. Data Collection: Download and load the Steam Game Reviews dataset from Kaggle.

#### 2. Data Cleaning: Filter relevant columns (`hours_played`, `recommendation`), handle missing values, and convert the recommendation column into a binary format (1 = Recommended, 0 = Not Recommended).

#### 3. Exploratory Data Analysis (EDA): Use histograms and boxplots to observe the distribution of playtime and its relationship with recommendation status.

#### 4. Statistical Testing: Apply independent samples t-tests to determine whether there is a significant difference in playtime between recommending and non-recommending players.

#### 5. Machine Learning Modeling: Build and evaluate classification models (Logistic Regression, Random Forest) to predict recommendations based solely on playtime.

#### 6. Conclusion and Interpretation: Interpret the results to validate the hypothesis and assess the predictive power of playtime.

# Data Analysis

## 1. Collecting Data
The dataset focuses on user reviews with the following key metrics:

#### •Hours Played
#### •Recommendation Status (Converted to Binary: 1 = Recommended, 0 = Not Recommended)

The data was processed using Pandas in a Jupyter Notebook environment.

## 2. Exploratory Data Analysis (EDA)
Using pandas, matplotlib, and seaborn libraries, I conducted several exploratory data analyses to understand how playtime relates to recommendations. I first created a histogram to visualize the overall distribution of hours played. Next, I used a boxplot to compare the distribution of playtime between recommended and not recommended reviews. I also checked the class balance using a count plot.

### 2.1 Histogram
The histogram displays the distribution of hours played. The data is heavily right-skewed, meaning most players have relatively low playtime, while a few have played for thousands of hours.

### 2.2 Boxplot
The boxplot compares the distribution of "Hours Played" for:
*   **0 (Not Recommended)**
*   **1 (Recommended)**

Visual inspection suggests a difference in the spread and median playtime, with recommended reviews generally showing a wider range of high playtime values.

### 2.3 Correlation Analysis
I conducted a Pearson correlation analysis to test the strength of the linear relationship between playtime and recommendation.

##### •Pearson Correlation Coefficient: -0.012
→ This indicates a negligible (almost zero) linear relationship between hours played and the binary recommendation status.

##### •P-Value: < 0.05
→ While statistically significant due to the large sample size, the effect size is practically non-existent.

## 3. Hypothesis Testing
#### Null hypothesis (H₀): The average playtime is the same for recommending vs. non-recommending reviews.

#### Alternative hypothesis (H₁): Reviews that recommend the game have a higher average playtime.

I conducted an independent samples t-test. The results are:

#### •T-statistic: -5.13

#### •P-value: 2.9e-07

Since the p-value is well below the significance threshold of 0.05, I reject the null hypothesis.
This provides statistical evidence that there is a significant difference in the average playtime of the two groups, despite the weak correlation.

## 4. Visualization Summary
The visualizations highlighted that while there is a statistical difference, the distributions of playtime for positive and negative reviews overlap significantly. High playtime does not exclusively belong to positive reviews, and low playtime does not exclusively belong to negative ones.

## 5. Machine Learning Prediction
To predict recommendations based on playtime, I trained and evaluated two classification models: Logistic Regression and Random Forest.

### 5.1 Logistic Regression
##### •Accuracy: ~79%
##### •F1-Score: ~0.88
##### •ROC-AUC: ~0.55

The model achieved high accuracy only because the dataset is imbalanced (79% of reviews are positive). The ROC-AUC score of 0.55 indicates the model is barely better than random guessing.

### 5.2 Random Forest Classifier
##### •Accuracy: ~79%
##### •F1-Score: ~0.88
##### •ROC-AUC: ~0.60

The Random Forest performed slightly better than Logistic Regression in terms of ROC-AUC, but still failed to find a strong predictive signal in playtime alone.

### Model Comparison
Both models struggled to predict user sentiment based solely on playtime. This confirms that playtime is not a sufficient standalone feature for recommendation prediction.

## 6. Limitations and Future Work

### 6.1 Limitations
##### •Class Imbalance: The dataset is heavily skewed towards positive recommendations (~79%), making it difficult for models to identify negative reviews.

##### •Single Feature: Relying only on "Hours Played" ignores the context of the review, the game's genre, and price.

##### •Skewed Data: Playtime data has extreme outliers which can affect model performance.

### 6.2 Future Work
Future work should focus on **Natural Language Processing (NLP)** to analyze the actual text of the reviews. Sentiment analysis of the review content would likely yield much higher predictive accuracy. Additionally, incorporating more features like game genre, developer, and price would create a more robust model.

## 7. Findings
This project aimed to determine whether playtime is a predictor of positive reviews. Key findings include:

#### •There is a statistically significant difference in average playtime between positive and negative reviews (p < 0.05).

#### •However, the correlation is extremely weak (-0.012).

#### •Machine Learning models (Logistic Regression, Random Forest) failed to effectively predict recommendations based on playtime alone (ROC-AUC ~0.55 - 0.60).

#### •The vast majority of reviews on Steam are positive, creating a class imbalance challenge.

## 8. Conclusion 
The analysis supports the hypothesis that there is a *difference* in playtime between the groups, but refutes the idea that playtime is a *strong predictor* of satisfaction. 

While satisfied players may play longer on average, playtime alone cannot distinguish a positive review from a negative one with high confidence. A player might play for 100 hours and still leave a negative review due to a bad ending or a specific bug. Therefore, engagement metrics should be combined with sentiment analysis for a true understanding of player satisfaction.
