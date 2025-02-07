# World-Education-Quality-Analysis
### Authored by : Sean Bjork

- *World Heat Map of Education Quality in 2012*
![](./visuals/ed_qual_2012.png)

## Motivating Questions
- Which countries have the best overall education quality?
- Which factors of education best predict overall quality?
  - Why do countries such as the US spend "top dollar" for an education system that isn't also top quality?

## Data
- UNESCO UIS: Education Statistics
  - United Nations Educational, Scientific and Cultural Organization Institute for Statistics
    - http://data.uis.unesco.org/#
- PISA IDE Score Reports in Math, Reading, & Science
  - Program for International Student Assessment International Database Explorer
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
Based on several readings about measuring education quality, namely the feature selection therefor, we followed recommendations made by Max Roser in his article posted on Our World in Data. In this article, there is particular emphasis on school climate and learning outcomes as the best factors for calculating education quality. Based on other readings, as well as our own fascination and intuition, school resources is also included as a feature category for our measure of international education. Due to the limits of the PISA Assessment, the scope of our analysis is limited to 68 countries over the span of 2000 to 2015.

Once these three feature categories were established, the specific features for each were meticulously selected. Factors associated with school climate were extracted from UNESCO's Institute for Statistics (UIS) and include enrollment rates (gross and net, intake ratios, drop-out rates, graduation rates, and school life expectancy to name a few - full feature list included in UIS_cleaning notebook. Factors associated with learning outcomes include PISA's math, reading, and science assessment for 15-year-olds, as well as literacy rates from the World Bank data set (percentages of total youth and total adult). Lastly, the factors associated with school resources were selected from solely the World Bank data set and include government expenditure on education as a percentage of total GDP, total government expenditure, total government expenditure on public institutions, and on a per capita basis.

Our methodology for calculating a comparative education quality index started with calculating individual indexes for each of our three feature categories: school climate, learning outcomes, and school resources. This was done by first employing a minimum-maximum scaler to all features with the minimum set to .9 and the maximum set to 1.1. Missing values were inputed as 1, so to not explicitly effect our indexes when data points were missing (more about this in limitations section). The total products of all our scaled features, therefore, served as our three indexes. After again scaling these values to account for differing numbers of features in each, we multiplied the three indexes to calculate our overall education quality index. Again, this was done for all 68 countries over our fifteen year span.

The top countries for each of our four indexes were calculated, as well as the most highly correlated features with each. We generated heat maps of this information: the index correlations with Seaborn and overall education quality with Tableau. Lastly, we calculated the average education quality worldwide to determine long-term trends.

## Findings
- *Top Countries for School Climate Index*
  - ![](./visuals/top_climate.png)
- *Top Countries for Learning Outcomes Index*
  - ![](./visuals/top_learning.png)
- *Top Countries for School Resources Index*
  - ![](./visuals/top_resources.png)
- *Top Countries for Education Quality Index*
  - ![](./visuals/top_ed_qual.png)


- *Most Correlated Features with School Climate Index*
![](./visuals/climate_correlations.png)
- *Most Correlated Features with Learning Outcomes Index*
![](./visuals/learning_correlations.png)
- *Most Correlated Features with School Resources Index*
![](./visuals/resources_correlations.png)
- *Most Correlated Features with Education Quality Index*
![](./visuals/ed_qual_correlations.png)

- *World Heat Map of Education Quality in 2000*
![](./visuals/ed_qual_2000.png)
- *World Heat Map of Education Quality in 2003*
![](./visuals/ed_qual_2003.png)
- *World Heat Map of Education Quality in 2006*
![](./visuals/ed_qual_2006.png)
- *World Heat Map of Education Quality in 2009*
![](./visuals/ed_qual_2009.png)
- *World Heat Map of Education Quality in 2012*
![](./visuals/ed_qual_2012.png)
- *World Heat Map of Education Quality in 2015*
![](./visuals/ed_qual_2015.png)

- *Yearly Worldwide Average Education Quality Index*
  - ![](./visuals/yearly_ed_qual.png)

## Conclusions / Limitations
As clearly shown in the world heat maps of education quality, as well as the list of top countries by education quality, the best education systems by overall quality exist in Europe countries, namely Finland, Belgium, Denmark, Spain, and Ireland. This finding is consistent with other measures of education quality, such as the list calculated by the INDEPENDENT report titled "The Best School Systems in the World" by Oscar William-Grut, which also ranked Finland as number one. As for which features best predict education quality, our learning index is most highly correlated, followed by our enrollment features. This is to say that our research suggests learning outcomes (scores in Math, Reading, Science, and Literacy) and school climate factors relating to gross enrollment rates best predict which educational systems have the best overall quality.

There were many interest findings from our analysis. For one, Singapore was found to have the highest learning outcomes index. Singapore is known for developing the "Singapore Math" method, which focuses on fewer topics than the US education system, but delves into greater depth with each topic. Also, we found that Moldova had the greatest school resource index of all included countries. From a paper titled "Improving the Efficiency and Equity of Public Education Spending: The Case of Moldova", we learned that Moldova suffers from an extremely high emigration rate due to political conflict. This has lead to an unnaturally low student population, causing an unnaturally high teach-to-student ratio. Therefore, government expenditure on education per capita is unnaturally high, since teacher wages account for the majority of total education costs.

Our study was limited by a few factors, both avoidable and unavoidable. Our data was missing several values, for which we imputed the value of 1. Since our indexes were calculated with multiplication, this value did not change the resulting index. However, had the value not been missing, it likely would not have been one. Therefore, imputing 1 for null values effectively brings countries will many null values closer to the median value for every index. This could have been avoided by a more thorough data collection. The unavoidable limitation of our study is that measuring education quality may not be measured separate from the greater cultural system in which it exists. As mentioned in an article in University World News titled "Can we measure education quality in global rankings?", to measure educational system qualities against one another is to assume that the impute and output of those systems, that is the students, are comparable populations. However, the factors affecting overall student success even before they enter their respective education system, such as their early childhood upbringing, can not be measured, though they undoubtedly have a significant impact on the effectiveness of their education.

## References
- The 11 Best School Systems in the World (November 2016)
  - INDEPENDENT Report by Oscar Willams-Grut
  - https://www.independent.co.uk/news/education/11-best-school-systems-in-the-world-a7425391.html
- Measuring education: What data is available? (February 2018)
  - Our World in Data Report by Max Roser
    - https://ourworldindata.org/measuring-education-what-data-is-available
- Improving the Efficiency and Equity of Public Education Spending: The Case of Moldova (February 2019)
  - IMF Working Paper by Hui Jin, La-Bhus Fah Jirasavetakul, and Baoping Shang
    - https://www.imf.org/~/media/Files/Publications/WP/2019/WPIEA2019042.ashx
- Can we measure education quality in global rankings? (August 2018)
  - University World News: The Global Window on Higher Education Report by Philip G Altbach and Ellen Hazelkorn
    - https://www.universityworldnews.com/post.php?story=20180814184535721
- Data Resources:
  - UNESCO UIS (February 2019)
    - http://data.uis.unesco.org/#
  - PISA (February 2017)
    - https://pisadataexplorer.oecd.org/ide/idepisa/
  - World Bank (June 2017)
    - https://datacatalog.worldbank.org/dataset/education-statistics
    
