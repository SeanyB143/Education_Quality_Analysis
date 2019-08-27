# World-Education-Quality-Analysis
### Authored by : Sean Bjork

![](./visuals/ed_qual_2012.png)
> Above shows education qualities in 2012

## Motivating Questions

- Which countries have the best overall education quality?
- Which factors of education best predict overall quality?
  - Why do countries such as the US spend "top dollar" for an education system that isn't also top quality?

## Data

- UNESCO UIS: Education Statistics
  - United Nations Educational, Scientific and Cultural Organization Institute for Statistics
    - http://data.uis.unesco.org/#
- PISA Score Reports in Math, Reading, & Science
  - Program for International Student Assessment
    - https://pisadataexplorer.oecd.org/ide/idepisa/
- The World Bank: IBRD & IDA Education Statistics
  - International Bank for Reconstruction and Development & International Development Association
    - https://datacatalog.worldbank.org/dataset/education-statistics

## Repository Structure
### Data:

- UIS
  - (./data/UIS/EDULIT_DS_23082019165936814.csv.csv) # First download
  - (./data/UIS/EDULIT_DS_25082019015237837.csv) # Second download 
  - (./data/UIS/uis.csv) # Cleaned data
- PISA
  - (./data/pisa/math_report-Table 1.csv) # Math scores
  - (./data/pisa/reading_report-Table 1.csv) # Reading scores
  - (./data/pisa/science_report-Table 1.csv) # Science scores
  - (./data/pisa/pisa.csv) # Cleaned data
- World Bank
  - (./data/world_bank/API_4_DS2_en_csv_v2_103930.csv) # Data download
  - (./data/world_bank/world_bank.csv) # Cleaned data
- Modeling
  - (./data/modeling/original_stats.csv) # Combined data
  - (./data/modeling/scaled_stats.csv) # Scaled data with indexes
  - (./data/modeling/tableau_df.csv) # Formatted for Tableau

### Notebooks:

- Cleaning:
  - (./notebooks/UIS_cleaning.ipynb)
  - (./notebooks/PISA_cleaning.ipynb)
  - (./notebooks/world_bank_cleaning.ipynb)
- Preprocessing & Feature Engineering
  - (./notebooks/preprocessing_engineering.ipynb)
- EDA & Modeling
  - (./notebooks/EDA_modeling.ipynb)

### Visuals
- Tables & Heat Maps:
  - (./visuals/ed_qual_2000.png)
  - (./visuals/ed_qual_2003.png)
  - (./visuals/ed_qual_2006.png)
  - (./visuals/ed_qual_2009.png)
  - (./visuals/ed_qual_2012.png)
  - (./visuals/ed_qual_2015.png)
  - (./visuals/ed_qual_correlations.png)
  - (./visuals/climate_correlations.png)
  - (./visuals/learning_correlations.png)
  - (./visuals/resources_correlations.png)
  - (./visuals/top_ed_qual.png)
  - (./visuals/top_climate.png)
  - (./visuals/top_learning.png)
  - (./visuals/top_resources.png)
  - (./visuals/yearly_ed_qual.png)
  - (./visuals/education_expenditure.jpg)

### Slide Deck
- Presentation:
  - (./slides/education_analysis_slides.pdf)

## Executive Summary
Our data was collected from multiple requests to our desired Reddit APIs. Of the keys provided in these dictionaries, we were most interested by "title", which contained the question for each post and contained zero missing values. Cleaning our data entailed removing undesired special characters (mostly "#" and "\") and replacing the commonly used abbreviation "SO" with "sigoth", short for "significant other". For natural language processing, we employed both the CountVectorizer and TFIDF, creating data frames labeled "cvec_df.csv" and "tfidf_df.csv". We added "target" columns to these data frames to conclude our preprocessing.

For the modeling of our data, we used both LogisticRegression and Multinomial Naive Bayes with both vectorized data frames. Utilizing GridSearchCV, we found the best hyperparameters for each model. For LogisticRegression, the best "penalty" (regularizer) was found to be Lasso. However, the best accuracy score from this model (.664) was less than the best found with Naive Bayes. It is interesting to note that the Naive Bayes calculations occured much more quickly, as GridSearching hundreds of alpha-values took mere seconds.

## Findings/Conclusions
In this study, we found lists of words which occur frequently in both AskWomen and AskMen, as well as words which occur in one of the subreddits or the other. The words in these latter two lists effectively serve as the best-predicting features for our models. Our accuracy score (.664) is significantly greater than the naive prediction accuracy (.539).

## Recommendations/Future Steps
For further research, we encourage the collection of more data and vectorizing within the gridsearch to improve hyperparameter tuning. Also, feature engineering which included character and word counts, as well as incorporation of the 'text' feature from posts that included it, may improve modeling performance.


## References

