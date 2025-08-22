---
layout: post
author: Augustine Tong
title: "Applied Data Science Project Documentation"
categories: ITD214
---
## Project Background

The dataset that we are utilising is the IMDB TMDB Movie Metadata Big Dataset, which will be made available during this project.

My team's project business goal is to maximise the commercial and critical success of upcoming film productions by leveraging historical movie data by increasing revenue by 5%. Objective 1, which is conducted by our group leader, Kelvin, is to predict the box office revenue. Objective 2, which is my main objective, is to predict user rating or critical reception, which can be gleaned from the vote average. Objective 3 is pursued by Shir Min, who is predicting sentiments for new movies. Objective 4, which is overseen by Roger, is to predict commercial success class or blockbuster classification.

## Work Accomplished
The work that I have done to accomplish the outcome involves the usage of the highly popular programming language, Python, to achieve my objective and hence, our business goal. Python, being highly versatile, enables the usage of libraries like numpy, pandas, and scikit-learn to provide indispensable assistance when it comes to analysing data, as well as programming. To outline the amount of work I have accomplished during the duration of this project, as well as applying what I have learnt during the duration of this course, I contributed to the achievement of my objective via Data Preparation, which is the process of transforming raw data into a clean, consistent and usable format for analysis and other downstream tasks like machine learning. Following that, I conducted Modelling, which is the process of creating a visual representation of how data is structured and related within a system.  Following that, evaluation, as well as recommendations and analysis will be provided, and the issue of AI Ethics will also be explored. The subsequent sections will go through all of these in detail.

### Data Preparation
When it came to preparing the data, I noticed that there were several variables that could be considered unique identifiers rather than features with meaningful information. Unique identifiers are highly important in the real world, especially when it comes to retrieving data. However, when it comes to analysing data, unique identifiers are usually removed before modelling as there are privacy issues involved, and especially to prevent overfitting of data. They usually have values that cannot be found in the rest of the dataset. These variables that I determined were unique identifiers were id, title, backdrop_path, homepage, imdb_id, original_title, poster_path and poster_link. I removed these variables accordingly.

Next, I removed variables that are important for text analytics and its applications such as sentiment analysis and topic modelling, as I am not the group member responsible for pursuing the objective related to text analytics. These variables were overview and tagline.

Following that, I removed certain variables that could be considered to be highly correlated, such as release_date (as release_year is already available), AverageRating, IMDB_Rating, meta_score (as they are highly similar to my target variable, vote_average), Star1, Star2, Star3, Star4 (as cast_list is already sufficient), Director, Certificate, Writer, Director_of_Photography, Producer, Music_Composer, production_countries (as they may be highly correlated with production_companies), keywords and all_combined_keywords (as the dataset already has genres_list), and finally, spoken_languages (as original_language is sufficient).

I also removed the status variable as most of the movies in the dataset have already been released.

Missing and wrong values were also taken care of as follows: 1) "runtime" values like "0" and "28" were replaced with the median
2) "release_year" null values and dates after 2025 were replaced with the median
3) Rows where values of "production_companies" are null were removed

Also, categorical variables such as original_language, production_companies, genres_list and cast_list were converted to numerical variables for easier modelling within the Python framework.

The following image was the final Correlation Matrix that I had obtained from my list of selected variables.

<img width="1684" height="776" alt="image" src="https://github.com/user-attachments/assets/edc08251-4015-44ef-91b7-6d09f395ddb5" />
Figure 1: Correlation Matrix

As seen from the matrix, most of the variables were not highly correlated (>0.8) with each other. Hence. I decided to retain all of these variables listed on the matrix.

### Modelling
When it came to modelling, I decided to use 1 White Box model and 2 Black Box Models that are reliable in handling tasks like these. The White Box model that I employed was the Lasso Regression, while the Black Box models that I employed were the Random Forest and the Support Vector Machine.

Lasso Regression is a type of linear regression model that performs both regularisation and variable selection to improve prediction accuracy and model interpretability.

<img width="1536" height="964" alt="image" src="https://github.com/user-attachments/assets/245765a8-e863-4ec3-9d4b-4c5b6619c5d2" />
Figure 2: Lasso Regression
Source: https://dataaspirant.com/lasso-regression/

Random Forest is a powerful machine learning algorithm that uses an ensemble of decision trees to make a decision, and is usually sufficient for modelling.

<img width="1772" height="1181" alt="image" src="https://github.com/user-attachments/assets/6e1df4b4-f0e1-4a49-8980-688504c823d4" />
Figure 3: Random Forest
Source: https://dida.do/what-is-random-forest

Support Vector Machine (SVM) is a supervised machine learning algorithm used for classification and regression tasks. When the number of dimensions is high, especially in this case, SVM can be highly useful in finding an optimal hyperplane that best separates data points into different classes.

<img width="1200" height="675" alt="image" src="https://github.com/user-attachments/assets/01158ac0-f81c-43f5-b0ee-60fd925f8d05" />
Figure 4: Support Vector Machine
Source: https://spotintelligence.com/2024/05/06/support-vector-machines-svm/

The next section, "Evaluation", will detail the results that I have obtained from running the models on my dataset.

### Evaluation
When it comes to evaluating the models that I chose, Python provided me with the following results, as pertains to Root Mean Squared Error (RMSE), Mean Absolute Error (MAE), as well as Coefficient of Determination (R-Squared).

For RMSE, large errors are penalised more than small ones because of the squaring, and should be used if big mistakes are very costly. In general, the lower the RMSE, the better.

<img width="322" height="97" alt="image" src="https://github.com/user-attachments/assets/3ecc1905-181c-4f59-8030-196e8ccb83f0" />

For MAE, the average absolute difference between predicted and actual values is calculated, and should be used when we want a robust, easy-to-interpret-metric. Also, it is less sensitive to outliers compared to RMSE. In general, the lower the MAE, the better.

<img width="277" height="84" alt="image" src="https://github.com/user-attachments/assets/cc608b0e-e62b-407d-bd04-7151604fa0cb" />

For R-Squared, the proportion of variance in the target explained by the model is calculated, and is known as the overall "goodness of fit". In general, an R-Squared value of 1 indicates a perfect prediction or a perfect fit to the model, while an R-Squared value of 0 indicates that the model explains none of the variability in the dependent variable. An R-Squared value of -1 is the opposite of an R-Squared value of 1 and is generally impossible. 

<img width="182" height="76" alt="image" src="https://github.com/user-attachments/assets/6e031082-ab46-414d-bff7-473317e7efd0" />

The following table are the results of my Evaluation:

<img width="928" height="144" alt="image" src="https://github.com/user-attachments/assets/6035331b-9a9f-4047-a3b4-826dcfdeb55e" />
Figure 5: Comparison of Models

As can be seen from the table, the Random Forest is the clear Champion Model as it has the lowest RMSE and MAE, as well as the highest R-Squared value among the 3 models.

When it comes to ranking the importances of the features within the Random Forest, it is clear that vote_count highly influences my target variable of vote_average.

<img width="790" height="620" alt="image" src="https://github.com/user-attachments/assets/16b90e10-965d-4312-b974-2e74a149f6cd" />
Figure 6: Feature Importances of Random Forest

## Recommendation and Analysis
It is clear from the Champion Model (Random Forest) that most of the the variables that I had selected for the purpose of modelling are relevant (0.89).

Going through all of my selected variables, I would say that vote_count has to be highly important, as more votes provide a more accurate vote average/movie score.

Revenue is a little bit different, as it is possible for low-rated films to have high revenue and high-rated films to have low revenue. However, most of the time, a high revenue indicates a higher movie score.

A longer runtime is usually indicative of a movie with a lot content, and usually indicates a higher movie score. However, the caveat is that certain movies with less runtime, such as animated films suitable for children, can be extremely highly rated.

Adult-rated movies are typically watched less than movies suitable for all audiences. Therefore, vote count, and hence vote average/movie score, may be affected.

A higher budget usually indicates a greater movie score, as it means that more effort has been put into making the movie. However, this is not always the case as there are several movies that have high budgets but are poorly-rated, while there are those that have low budgets but are highly-rated.

Popularity should be a significant factor in movie ratings. Usually, movies of higher popularity have higher movie scores.

The release year can be a factor in movie scores. For example, nostalgia can lead to older movies having higher scores, while brand new blockbusters can also contribute to higher scores due to anticipation.

Usually, a positive overview sentiment would contribute to a higher movie rating. This should be self-explanatory.

A movie that is made in a highly-spoken language such as English or Chinese would contribute to more vote counts, and hence, contribute more to the vote average.

These days, major production companies such as Universal Studios and Disney have the lion's share of good movies. This is not always the case though, as independent films, while not as successful at the box office, can be seen as works of art and can be highly rated by viewers.

Genre can be a significant factor in movie ratings. Movies of popular genres like romance, comedy, action and fantasy tend to do well among viewers.

Cast list can be another significant factor in movie ratings. Usually, popular movie stars tend to produce movies that are more highly rated due to their clout, resulting from good past performances. However, up-and-coming movie stars that have not been seen by most viewers have to be taken into consideration.

All in all, a movie that I would suggest to improve critical reception would have to be one that has many vote counts, a higher revenue, longer runtime, suitable for all ages, higher budget, can achieve higher popularity, be a blockbuster akin to a classic (maybe a long-awaited sequel?), a positive overview sentiment, be of a highly-spoken langauge, be made by famous production companies, be of a popular genre, as well as starring popular cast members.

## AI Ethics
Privacy and fairness issues can stem from using the data of so many movies made by large production companies, and even by smaller production companies. It is possible that such production companies, despite most of their information being voluntarily public, do not want to be subject to algorithms related to AI and Data Analytics. It could trivialise their data as being "just numbers" that determine which movie is going to bad or good, which movie is going to be poorly or highly rated, which movie is or is not going to have greater revenue. As a result, data can be misused and cause biasness. Production companies may only choose to hire more famous cast members, directors, producers etc., and may cause less famous individuals to lose jobs and opportunities.

As I have deduced from our dataset as a whole, there are several errors and incomplete data that cannot be reconciled by imputing or removal of entire variables. These errors were most likely caused by humans. When fed into AI or Machine Learning algorithms, it is possible that there may be highly erroneous results that impact the accuracy of projects that attempt to determine the success of films. This particular dataset is also highly concerning as it is a popular dataset used by several data analysts. As they say, "Garbage in, garbage out", and AI being trained on such inaccurate data may be detrimental to the movie industry.

Accountability may also be an issue, as AI engineers and data analysts who use the dataset may be anonymous, and movie production companies may not want their data to be misused for potentially nefarious means, despite their data being public. Inaccurate data can be twisted to form inaccurate views of the movie industry, which could be detrimental to the industry as a whole.

Transparency might be an issue, as the presence, or lack of presence of data seen in the dataset could indicate that there are several production companies that do not want their data to be made too public, even though most of it should be public information. Perhaps this is a misinterpretation of mine. However, if true, it could impact AI development, as AI requires huge amounts of data to train on, and a lack of data can lead to inefficient AI.

## Source Codes and Datasets
Upload your model files and dataset into a GitHub repo and add the link here. 
https://github.com/augustinetong1212-byte/itd214_proj
https://drive.google.com/file/d/1sP2ZqElD-JEZI7GmhuOLWH8rmYz0iN5k/view?usp=drive_link
