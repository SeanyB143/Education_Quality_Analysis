# World-Education-Quality-Analysis
### Authored by : Sean Bjork

![](./visuals/ed_qual_2012.png)

## Motivating Questions

- Which countries have the best overall education quality?
- Which factors of education best predict overall quality?

## Data

 

## Repository Structure
- Jupyter Notebooks:
  - (./code/1_scraping.ipynb)
  - (./code/2_cleaning.ipynb)
  - (./code/3_NLP_EDA.ipynb)
  - (./code/4_modeling_cvec.ipynb)
  - (./code/5_modeling_tfidf.ipynb)
- Datasets:
  - (./data/data.csv)
  - (./data/clean_data.csv)
  - (./data/cvec_df.csv)
  - (./data/tfidf_df.csv)
- Presentation:
  - (./slides/AskWomen_AskMen_Classification.pdf)
- Pictures:
  - (./pictures/overlap_words.png)

## Executive Summary
Our data was collected from multiple requests to our desired Reddit APIs. Of the keys provided in these dictionaries, we were most interested by "title", which contained the question for each post and contained zero missing values. Cleaning our data entailed removing undesired special characters (mostly "#" and "\") and replacing the commonly used abbreviation "SO" with "sigoth", short for "significant other". For natural language processing, we employed both the CountVectorizer and TFIDF, creating data frames labeled "cvec_df.csv" and "tfidf_df.csv". We added "target" columns to these data frames to conclude our preprocessing.

For the modeling of our data, we used both LogisticRegression and Multinomial Naive Bayes with both vectorized data frames. Utilizing GridSearchCV, we found the best hyperparameters for each model. For LogisticRegression, the best "penalty" (regularizer) was found to be Lasso. However, the best accuracy score from this model (.664) was less than the best found with Naive Bayes. It is interesting to note that the Naive Bayes calculations occured much more quickly, as GridSearching hundreds of alpha-values took mere seconds.

## Findings/Conclusions
In this study, we found lists of words which occur frequently in both AskWomen and AskMen, as well as words which occur in one of the subreddits or the other. The words in these latter two lists effectively serve as the best-predicting features for our models. Our accuracy score (.664) is significantly greater than the naive prediction accuracy (.539).

## Recommendations/Future Steps
For further research, we encourage the collection of more data and vectorizing within the gridsearch to improve hyperparameter tuning. Also, feature engineering which included character and word counts, as well as incorporation of the 'text' feature from posts that included it, may improve modeling performance.


## References
Data:
urls
