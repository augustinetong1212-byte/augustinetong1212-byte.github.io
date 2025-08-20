---
layout: post
author: Augustine Tong
title: "Applied Data Science Project Documentation"
categories: ITD214
---
## Project Background
Provide an overview of your team's project business goals and objectives and state the objective that you are working on. 

The dataset that we are utilising is the IMDB TMDB Movie Metadata Big Dataset, which will be made available during this project.

My team's project business goal is to maximise the commercial and critical success of upcoming film productions by leveraging historical movie data by increasing revenue by 5%. Objective 1, which is conducted by our group leader, Kelvin, is to predict the box office revenue. Objective 2, which is my main objective, is to predict user rating or critical reception, which can be gleaned from the vote average. Objective 3 is pursued by Shir Min, who is predicting sentiments for new movies. Objective 4, which is overseen by Roger, is to predict commercial success class or blockbuster classification.

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## Work Accomplished
Document your work done to accomplish the outcome

The work that I have done to accomplish the outcome involves the usage of the highly popular programming language, Python, to achieve my objective and hence, our business goal. Python, being highly versatile, enables the usage of libraries like numpy, pandas, and scikit-learn to provide indispensable assistance when it comes to analysing data, as well as programming. To outline the amount of work I have accomplished during the duration of this project, as well as applying what I have learnt during the duration of this course, I contributed to the achievement of my objective via Data Preparation, which is the process of transforming raw data into a clean, consistent and usable format for analysis and other downstream tasks like machine learning. Following that, I conducted Modelling, which is the process of creating a visual representation of hwo datat is structured and related within a system.  Following that, evaluation, as well as recommendations and analysis will be provided, and the issue of AI Ethics will also be explored.The subsequent sections will go through all of these in detail.

### Data Preparation
When it came to preparing the data, I noticed that there were several variables that could be considered unique identifiers rather than features with meaningful information. Unique identifiers are highly important in the real world, especially when it comes to retrieving data. However, when it comes to analysing data, unique identifiers are usually removed before modelling as there are privacy issues involved, and especially to prevent overfitting of data. They usually have values that cannot be found in the rest of the dataset. These variables that I determined were unique identifiers were id, title, backdrop_path, homepage, imdb_id, original_title, poster_path and poster_link. I removed these variables accordingly.

Next, I removed variables that are important for text analytics and its applications such as sentiment analysis and topic modelling, as I am not the group member responsible for pursuing the objective related to text analytics. These variables were overview and tagline.

Following that, I removed certain variables that could be considered to be highly correlated, such as release_date (as release_year is already available), AverageRating, IMDB_Rating, meta_score (as they are highly similar to my target variable, vote_average), Star1, Star2, Star3, Star4 (as cast_list is already sufficient), Director, Certificate, Writer, Director_of_Photography, Producer, Music_Composer, production_countries (as they may be highly correlated with production_companies), keywords and all_combined_keywords (as the dataset already has genres_list), and finally, spoken_languages (as original_language is sufficient).

I also removed the status variable as most of the movies in the dataset have already been released.

Missing and wrong values were also taken care of as follows:
-"runtime" values like "0" and "28" were replaced with the median
-"release_year" null values and dates after 2025 were replaced with the median
-Rows where values of "production_companies" are null were removed

Also, categorical variables such as original_language, production_companies, genres_list and cast_list were converted to numerical variables for easier modelling within the Python framework.

The following image was the final Correlation Matrix that I had obtained from my list of selected variables.

<img width="1684" height="776" alt="image" src="https://github.com/user-attachments/assets/edc08251-4015-44ef-91b7-6d09f395ddb5" />

As seen from the matrix, most of the variables were not highly correlated (>0.8) with each other. Hence. I decided to retain all of these variables listed on the matrix.

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

### Modelling
When it came to modelling, I decided to use 1 White Box model and 2 Black Box Models that are reliable in handling tasks like these. The White Box model that I employed was the Lasso Regression, while the Black Box models that I employed were the Random Forest and the Support Vector Machine.

Lasso Regression is a type of linear regression model that performs both regularisation and variable selection to improve prediction accuracy and model interpretability.

Random Forest is a powerful machine learning algorithm that uses an ensemble of decision trees to make a decision, and is usually sufficient for modelling.

<img width="1772" height="1181" alt="image" src="https://github.com/user-attachments/assets/6e1df4b4-f0e1-4a49-8980-688504c823d4" />

Support Vector Machine (SVM) is a supervised machine learning algorithm used for classification and regression tasks. When the number of dimensions is high, especially in this case, SVM can be highly useful in finding an optimal hyperplane that best separates data points into different classes.

<img width="1200" height="675" alt="image" src="https://github.com/user-attachments/assets/01158ac0-f81c-43f5-b0ee-60fd925f8d05" />

The next section, "Evaluation", will detail the results that I have obtained from running the models on my dataset.

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

### Evaluation
When it comes to evaluating the models that I chose, Python provided me with the following results, as pertains to Root Mean Squared Error (RMSE), Mean Absolute Error (MAE), as well as Coefficient of Determination (R-Squared).

For RMSE, large errors are penalised more than small ones because of the squaring, and should be used if big mistakes are very costly. In general, the lower the RMSE, the better.

<img width="322" height="97" alt="image" src="https://github.com/user-attachments/assets/3ecc1905-181c-4f59-8030-196e8ccb83f0" />

FOR MAE, the average absolute difference between predicted and actual values is calculated, and should be used when we want a robust, easy-to-interpret-metric. Also, it is less sensitive to outliers compared to RMSE. In general, the lower the MAE, the better.

<img width="277" height="84" alt="image" src="https://github.com/user-attachments/assets/cc608b0e-e62b-407d-bd04-7151604fa0cb" />

For R-Squared, the proportion of variance in the target explained by the model is calculated, and is known as the overall "goodness of fit". In general, an R-Squared value of 1 indicates a perfect prediction or a perfect fit to the model, while an R-Squared value of 0 indicates that the model explains none of the variability in the dependent variable. An R-Squared value of -1 is the opposite of an R-Squared value of 1 and is generally impossible. 

<img width="182" height="76" alt="image" src="https://github.com/user-attachments/assets/6e031082-ab46-414d-bff7-473317e7efd0" />

The following table are the results of my Evaluation:

<img width="928" height="144" alt="image" src="https://github.com/user-attachments/assets/6035331b-9a9f-4047-a3b4-826dcfdeb55e" />

As can be seen from the table, the Random Forest is the clear Champion Model as it has the lowest RMSE and MAE, as well as the highest R-Squared value among the 3 models.

When it comes to ranking the importances of the features within the Random Forest, it is clear that vote_count highly influences my target variable of vote_average.

<img width="790" height="620" alt="image" src="https://github.com/user-attachments/assets/16b90e10-965d-4312-b974-2e74a149f6cd" />



Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## Recommendation and Analysis
Explain the analysis and recommendations

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## AI Ethics
Discuss the potential data science ethics issues (privacy, fairness, accuracy, accountability, transparency) in your project. 

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## Source Codes and Datasets
Upload your model files and dataset into a GitHub repo and add the link here. 
