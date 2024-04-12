# Macdonald_data
This data is MacDonald data that includes response regarding taste, health, cost and efficiency. Further, it also includes responders age, visit frequency and ratings. 

**Methodology**

The data were analyzed using python in spyder (https://www.spyder-ide.org/). 

The library and packages used were:  pandas (1.5.3), numpy (1.24.4), matplotlib (3.5.2), seaborn(0.13.2), scikit-learn(1.0.2), scipy (1.9.1), statsmodels (0.13.2) and pingouin (0.5.4).


**Data cleaning and validation**


The data cleaning and validation steps are summarized in figure 1. The data types of each column were explored. Most of the columns were object datatype except Age columns which was an int64 data type. The unique values in each column were studied. The unique values looked okay for yummy, convenient, spicy, fattening, greasy, fast, cheap, tasty, expensive, healthy, and disgusting columns (2 unique values: yes and no). The unique value for Like columns were ratings from -5 to 5; however, -5 and 5 were labelled as 'I hate it!-5' and 'I love it!+5' respectively. The values 'I hate it!-5' and 'I love it!+5'  were changed to -5 and 5 respectively. The unique value for gender looked okay (Male and Female). The unique values for visitfrequency were 'Every three months' 'Once a week' 'Once a month' 'Once a year', 'More than once a week' and 'Never'. These unique values were converted to values as visit frequency per year as shown in figure description. There were 22 number of duplicated rows. Since there was no unique identifier for any of these columns and the possible values range was low it was difficult to decide if these rows were true duplicates or were coincidentally duplicates. Hence, I decided to check for subsequent duplicate rows and remove only those rows. There were no missing values. The summary statistics did not show any extreme values for Age column. The data type for columns yummy", "convenient", "spicy", "fattening", "greasy", "fast", "cheap", "tasty", "expensive", "healthy", "disgusting" and "Gender" were converted to category data type. The Like and visitfrequency columns were converted to integer data type. Further, additional columns age_group and visits per year were created based on the Age and visitfrequency columns. Both columns are category data types. 

![data_cleaning_validation_summary](https://github.com/Laxmi-Dhungel/Macdonald_data/assets/154451345/2d25e81a-8a9b-4eac-ac1d-31f539dcc589)

Figure 1. The summary of data cleaning and validation steps. The data were checked for data types, unique values, duplicates and summary statistics. All columns except Age were object data type. The data types were converted to category data type for most of the columns except like and frequency. The duplicates values in subsequent rows were removed. The summary statistics did not show any extreme values for Age column. The unique values were okay for most of the columns. For columns Like and visitfrequency, the unique values were replaced. The like columns had values ranging from -5 to 5; however -5 and 5 were labelled as 'I hate it!-5' and 'I love it!+5' respectively. The values 'I hate it!-5' and 'I love it!+5'  were changed to -5 and 5 respectively.  The unique values for visitfrequency were 'Every three months' 'Once a week' 'Once a month' 'Once a year', 'More than once a week' and 'Never'. These values were converted to number of visits per year and replaced as follow: (Every three months: 4,  Once a week: 52, "Once a month": 12, "Once a year": 1, "More than once a week": 156, "Never": 0). For more than once a week, the visits were assumed to be 3 times a week on average. Additional columns age_group and visits_per_year were created using Age and visitfrequency columns. The ages were categorized as "16-20 y", "21-25 y", "26-30 y","31-35 y", "36-40 y", "41-45 y", "46-50 y", "51-55 y", "56-60 y", "61-65 y" and ">65 y" in age_group column. The visits_per_year column was a category datatype of visitfrequency column and the value 156 was replaced with >52. 


**Statistical Analysis**
The data for age based on visits per year was not normally distributed; hence Mann-whitneyU test (using pinguin) was used to determine the significant differences in the median age of respondent based on visits per year (https://pingouin-stats.org/build/html/generated/pingouin.pairwise_tests.html). The pairwise tukey_hsd test was used to determine the significant difference in like based on visit frequency, age-group and gender. The possible values for like column was narrow and ranged from -1 to 5; hence average was computed. The random forest regressor (feature_importances_) was used to determine the most feature determining like and visit frequency. 

**Results**


**Response regarding taste, health, cost, and efficiency of the restaurant**


The columns were categorized as features related to taste, cost and efficiency and health. The taste related features were “Yummy”, “Tasty”, “Spicy” and “Disgusting”. The cost and efficiency related features were “Cheap”, “Expensive”, “Fast” and “Convenient”. The health-related features were “Healthy”, “Fattening” and “Greasy”. The overall response analysis suggested that the responders are comparatively satisfied with features related to taste and cost and efficiency; however, they are not satisfied with features related to health. Higher percentages of respondents commented to positive taste related features as Yes (yummy: 55.23% and Tasty: 64.39%) and negative taste related features as No (Spicy: 90.63%, Disgusting: 75.69%) (Figure 2). Similarly higher percentages of respondents commented the restaurant to be cheaper, fast, and convenient (yes %: cheap (59.85%), expensive (35.81%), fast (90.01%), convenient (90.77%)). Higher percentages of respondent commented the food to be unhealthy, fattening, and greasy (yes %: healthy (19.9%), fattening (86.71%), greasy (52.62%)). 


![data_distribution_taste](https://github.com/Laxmi-Dhungel/Macdonald_data/assets/154451345/2cb0c368-92de-42c0-986f-12f45c540cf9)

Figure 2. Percentage distribution of response regarding food taste. A) Yummy,  B) Tasty, C) Spicy, D) Disgusting. Overall the respondent comments regarding taste of food looks comparatively satisfactory. Higher percentages of respondent commented Yes for positive taste related features (A, B) whereas higher percentages of respondent commented No for negative taste related features (C, D). 


![data_distribution_efficiency](https://github.com/Laxmi-Dhungel/Macdonald_data/assets/154451345/44437456-53d9-4780-8ab7-ac05de1ed065)

Figure 3. Percentage distribution of response regarding restaurant cost and effiency. A) Cheap, B) Expensive, C) Fast, D) Convenient. Overall, the rspondent commented the restaurant to be cheaper, fast and convenient. 


![data_distribution_health](https://github.com/Laxmi-Dhungel/Macdonald_data/assets/154451345/69317825-5750-4515-aa22-d97b16ba6d6d)

Figure 4. Percentage distribution of response regarding health. Overal, the respondent seemed unsatisfied with features related to health. Higher percentages of respondent commented food to be unhealthy, fattening and greasy.



**Response regarding taste, health, cost, and efficiency of the restaurant based on age-group**

Percentage distribution of response regarding food taste based on age-group showed that age-group below 45 years feel food as yummy but the result was reversed for age group above 45 years. Similarly, higher percentages of respondent commented food as Tasty; however the "yes" percentages was lower for older population compared to younger population. Most of the respondent commented food as not being spicy and disgusting. Higher percentage of respondent for all age-group except 41-45 years commented food as being cheap and not expensive. Most of the respondent on all age-group commented the restaurant as fast and convenient. For all age-group, higher percentages of respondent commented food as unhealthy and fattening. 


![food_taste](https://github.com/Laxmi-Dhungel/Macdonald_data/assets/154451345/63e0101e-2ff6-4120-afa8-8e469d9ea1a0)

Figure 5. Percentage distribution of response regarding food taste based on age-group. Below 45 years, higher percentages of respondent commented food as yummy but the result was reversed for age group above 45 years (A). Similarly, higher percentages of respondent commented food as Tasty; however the "yes" percentages was lower for older population compared to younger population (B).  Higher percentages of respondent for all age group commented "no" for food as spicy and disgusting (C and D).
 

![age_dist_cost](https://github.com/Laxmi-Dhungel/Macdonald_data/assets/154451345/a38b3e30-2fd7-4546-b6ca-27974845e87c)

Figure 6. Percentage distribution of response regarding food cost and efficiency based on age-group. Higher percentage of respondent for all age-group except 41-45 years commented food as being cheap (A). Similarly, higher percentage of respondent of all age-group except 41-45 years commented "no" for food being expensive (B). Most of the respondent on all age-group commented the restaurant as fast and convenient (C). 


![healthy](https://github.com/Laxmi-Dhungel/Macdonald_data/assets/154451345/8c3c55ed-8602-4e12-8047-7eef88a6a3b4)

Figure 7. Percentage distribution of response regarding health. FOr all age-group, higher percentages of respondent commented food as unhealthy and fattening (A and B). Younger age-group population commented food as greasy (<40) wheras older age-group population (except 46-50 years)  commented food as not greasy (C). 


**Who visited the restaurant most often?/ How often did they visit the restaurant?**

The median age for the respondent was significantly lower for the respondent who visited the restaurant more often. The median age of respondent who never visited the restaurant was 55 whereas the median age of the respondent who visited more than 52 times a year was 33 (Figure 5). The median age of respondent who visited few times or never (0, 1, 4 times as year) was significantly lower than the respondent who visited more frequently (12, 52 and > 52 times a year) (Mann-whitney test, sig (p<=0.05)). Most of the respondent visited restaurant 12 times a year (Figure 6). Similarly, most of the respondent in age group 16- 50 years and > 65 years visited the restaurant 12 times a year whereas most of the respondent in the age-group 51-65 years visited the restaurant 4 times a year (Figure 7). Highest number of visit frequency for both male and female was 12 times a year (Figure 7). 


![median_age_visits_per_year](https://github.com/Laxmi-Dhungel/Macdonald_data/assets/154451345/12575c65-d8f4-455c-b96f-c1f7aeddf1d2)

Figure 5. Median age of respondent based on their visit frequency per year. The age of respondent who visited more often (12, 52 and >52 times a year) was significantly different than the age of respondent who visited less often (0, 1 and 4 times a year) (Mann-whitney test, sig (p <=0.05)). The lesser visit frequency and higher visit frequency are separated by red dashed line. Further, within lesser visit frequency the median age of respondent who visited restaurant 4 times a year was significantly lower than who never visited the restaurant. Similarly, within the higher visit frequency the median age of respondent who visited 52 times a year is significantly lower than the respondent who visited the restaurant 12 times a year. 


![visits_per_year](https://github.com/Laxmi-Dhungel/Macdonald_data/assets/154451345/0446b066-77f7-4b75-b077-13cc3af43e5e)

Figure 6. The percentages of respondent based on their visit frequency per year. Most of the respondent visited the restaurant 12 times a year (30.17%) whereas the least percentages of the respondent visited the restaurant > 52 times a year (3.72%).


![relative_percentages_age_gender](https://github.com/Laxmi-Dhungel/Macdonald_data/assets/154451345/b43982c6-bc90-4bde-ba54-61dd4a91b3e0)

Figure 7. Relative percentages of number of visits based on A) age-group and B) gender. Most of the respondent in age-group 16-50 years (>30%) and > 65 years (28%) visited the restaurant 12 times a year. Most of the respondent in age-group 51-65 years (29%) visited the restaurant 4 times  ayear. Similary, for both gender the highest visit frequency was 12 times a year (>30%). The relative percentage of respondent was least (<5%) for visit frequency > 52 times a year for age group 16-20 and >31 years. For age-group 21-30 least percentages of respondent (<5%) never visited the restaurant. Similarly, for both gender the lowest visit frequency was >52 times a year (< 5%). 


**Does age, gender and visit frequency impact like/rating?**

The visit frequency and age had a significant impact on the like/rating. The average like/rating significantly increase with an increase in visit frequency (pairwise_tukeyhsd, sig (p-value<=0.05)). The average like/rating for respondent who visited >52 times a year was highest (3.8) whereas average like/rating for respondent who never visited the restaurant was lowest (-3.91). Similarly, younger age-group respondent (< 40 years) gave higher like/rating compared to respondent at age-group (>40 years). The age-group 21-25 years gave the highest rating (2.4) whereas age-group 61-65 years gave the lowest rating (-0.3). The lowest average like/rating given by age-group 61-65 years was significantly different than average like/rating given by age-group <40 years. Although, female gave higher like/rating (0.9) than male (0.6) the differences was not statistically significant (pairwise_tukeyhsd, sig (p-value<=0.05)). A vey high percentages of respondent (63%) who never visited the restaurant gave -5 for like/rating. Similarly, highest percentage of respondent (44%) who visted the restaurant >52 times a year gave 5 like/rating. This suggested that respondent who visited more are more likely to give higher like/rating. 

Highest percentage (>20%) of younger age group (16-25 years) gave rating 5 whereas highest percentage of respondent (>15%) in age group greater than 61 years gave rating -5. This suggest that younger generation like the restaurant more than older populations. The relative percentages shows decline in like/rating with age. For both male (14%) and female (17%), most of the respondent gave rating 3.    


![visit_freq_like](https://github.com/Laxmi-Dhungel/Macdonald_data/assets/154451345/5efd6fa2-7004-4a0a-a03b-bb6f8b2247bd)

Figure 8. A) The average like/rating based on visit frequency. The average like/rating significantly increased with an increase in visit frequency. The differences in average like/rating was statistically significant between all the visit frequency expcept between 52 and > 52 visits per year. B) The relative percentage of like/rating based on visit frequency. The higher percentages of respondent who visited the restaurant more frequently (44% of respondent who visited >52 times a year, 25% of respondent who visited 52 times a year) gave higher like/rating (5). Similarly, a very high percentages of respondent (63%) who never visited the restaurant gave -5 like/rating. The highest percentages of respondent (18%) who visited restaurant once a year also gave -5 like/rating. 


![like_age_gender](https://github.com/Laxmi-Dhungel/Macdonald_data/assets/154451345/2cf8564e-d74f-4676-aa99-9a7dfa9c8fd1)

Figure 8. A) Average like/rating based on age group. The age-group lesser than 40 gave higher like/rating than age-group greater than 40. The average like/rating was the highest for the age-group 21-25 years (2.4) whereas the average like/rating was the lowest for the age-group 61-65 years (-0.3). The average lowest rating given by age-group 61-65 years was significantly lower than average rating given by age-group < 40 years (separated by red dash line). The highest average rating given by age-group 21-25 years was significanlty higher than average like/rating given by all the other age group except age-group 16-30 (ns) (pairwise_tukeyhsd, sig (p-value<=0.05)). B) Average like rating based on gender. Although female gave higher average rating than male, the difference was not statistically significant. 


![age_gender_like_rel_percentages](https://github.com/Laxmi-Dhungel/Macdonald_data/assets/154451345/a511ad24-bf8f-4385-a4b2-92dcbcdc7a84)

Figure 9. A) Relative percentage of like/rating based on age-group. The highest percentages (>20%) of younger age-group (16-25 years) gave higer rating (5) whereas highest percentages (>15%) of older age-group (>61 years) gave lower rating (-5). With an increase in age-group the like/rating given by the highest percentage of respondent was decreased. B) Relative percentage of like/rating based on gender. The highest percentage of both male (14%) and female (17%) gave like/rating 3. 


**Important predictors (food related) for like and visit frequency**


The important predictors (food related) for like and visit frequency was determined using random forest. The results showed that "yummy" is the most important predictor for both like and visit frequency. Taste related features were the top most determinant of both like and visit frequency (3 out of top 4). The "convenient" was the second most important predictor of visit frequency but the fourth most important predictor of like/Rating. Although health related predictor "greasy" was 5th most important predictor for both like and visit frequency, another health related feature "healthy" was 6th most important feature for like whereas it was 9th most important feature for visit frequency. The cost related feature "cheap" and "expensive" ranked as 7th and 8th most important feature respectively for like whereas 8th and 6th most important feature respectively for visit frquency.  


![Like](https://github.com/Laxmi-Dhungel/Macdonald_data/assets/154451345/f9eada23-adc2-4ce1-8399-a7f4946f3383)

Figure 10. Most important determinant of like/rating. The taste related features were the most important determinant of like (3 out of top 4). The "yummy" was the top most determinant of Like. The "convenient" was the fourth most important determinant followed by health related features "greasy" and "healthy". The most important feature was determined using random forest.



![visit_frequency](https://github.com/Laxmi-Dhungel/Macdonald_data/assets/154451345/7a286e27-6192-4590-8faf-2967f4df2b4f)

Figure 11. Most important determinant of visit frequency. The tase related features were the most important determiant of visit frequency (top 3 out of 4). The "yummy" ranked the top most determinant. The "convenient" was the second most important determinant. ALthough "greasy" ranked as 5th most important determinant, another health related feature "healthy" ranked as 9th most important feature. The most important feature was determined using random forest. 


**Conclusion**
The results showed that most of the respondent have positive response regarding features related to taste, cost and efficiency; however, the response regarding health related features were negative. Most of the respondent visited the restaurant 12 times a year (once a month). Younger generation visited the restaurant more often suggesting higher popularity among them. The respondent who visited more oftern gave higher like/rating. Further, younger generation gave higher like/rating to the restaurant. The like/rating was not different based on gender. The taste related features were the most important predictors of like and visit frequency.  The "yummy" was the most important predictor of both like and visit frequency. The food being "yummy" could be one of the main reasons for popularity among younger population as higher percentages of younger age-group commented food as yummy whereas the results was reversed in older age-group. The convenience ranked second most important feature to predict visit frequency. 

Hence, based in these results it can be suggested that older population are not satisfied with food taste (no yummy), which may be one of the reasons behind less visit frequency and like/rating. The restaurant may need to study the taste preferences of older population and include those as food options to attract the customers of all age-groups. Further, the response regarding health related features were negative. Although health was not one of the most important predictor of like and visit frequency, it has potential to be important predictors in future as people are becoming aware of their health, fitness and diet. Restaurant can include food that are both yummy and healthy and study its impact on like, visit frequency and ability to attract wide range of customers.  
