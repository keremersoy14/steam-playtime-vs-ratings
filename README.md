# Steam Playtime vs Player Ratings  
**Kerem Ersoy – 31225**  
**DSA210 Project**

## Overview
This project analyzes the relationship between how long players spend playing a game on Steam and whether they recommend the game. The focus is on understanding whether playtime alone provides meaningful insight into player ratings.

## Dataset
The dataset is sourced from Kaggle and contains individual Steam user reviews. Each entry includes hours played, recommendation status, and basic review metadata.

## Approach
- Data cleaning and preprocessing  
- Exploratory data analysis with simple visualizations  
- Correlation analysis between playtime and recommendation  
- Application of basic machine learning models  

Playtime values are log-transformed to handle skewed distributions.

## Machine Learning
Two classification models are used:
- Logistic Regression (baseline)
- Random Forest Classifier

Models are evaluated using Accuracy, F1-score, and ROC-AUC.

## Tools
Python, Pandas, NumPy, Matplotlib, Scikit-learn, Jupyter Notebook

## Notes
All analysis, visualizations, and model results are provided in the Jupyter Notebook.
