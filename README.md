This model uses the Kaggle Titanic Dataset to predict a person on the Titanic ship would survive the crash.


<h1>Titanic Survival Prediction Model</h1>

<h2>Motivation</h2>
Titanic Dataset has largely been used to host Kaggle Data Science Competitions. This was my first attempt at one such competition. I have developed a Machine Learning Model that predicts whether a person on board the ship would survive or not based on different columns from the data set like Age, Sex, Accompany Family Members, Class, Fare, ParCh, etc. This model helps identifies, which factors among these affected the most for a person's survival and if Class or ticket-prices had any correlation with survival rates.

<h2>Data</h2>

The dataset used is directly downloaded from the Kaggle Competition Website (https://www.kaggle.com/competitions/titanic/data?select=train.csv). There are two different datasets train.csv and test.csv. For the competition, I will build the entire project on the train.csv file and the test.csv file will be used to create final predictions for competition submission.



<h2>Data Processing</h2>

Before any data analysis could be done, I needed to clean and organize our datasets for examination.
* From using the .info method, I see that almost all columns have no missing values, however, Age, Cabin and Embarked have some missing values as they are not equal to 712 rows.
* I am first dropping the Cabin column as there are not enough values and many rows have missing data, which would make it difficult to make proper sense of it.

<h2>Extrapolatory Data Analysis and Visualization</h2>

<h3>Pairplots</h3>

<br/>![Pairplot 1](https://github.com/goel-mehul/Titanic-Survival-Prediction-Model/blob/main/Images/Pairplot1.png "Pairplot 1")
<h4 align="center">Figure 1: Pairplot 1</h4>

<br/>![Pairplot 2](https://github.com/goel-mehul/Titanic-Survival-Prediction-Model/blob/main/Images/Pairplot2.png "Pairplot 2")
<h4 align="center">Figure 2: Pairplot 2</h4>


From the graphical analysis, I see very small amount of correlation to exist, which is hard to notice and ensure that it is statistically significant. However from the second pairplot it seems people who had higher fares, were in class 1, are more likely to have survived titanic crash.

<h3>HeatMap</h3>

<br/>![HeatMap](https://github.com/goel-mehul/Titanic-Survival-Prediction-Model/blob/main/Images/Heatmap.png "HeatMap")
<h4 align="center">Figure 3: HeatMap</h4>

From the heatmap, it becomes clear that there does not exist high correlations between different columns. Only Fare and Survived, and Parch and SibSp have some correlation. There is also negative correlation between Pclass and Survived which implies people in Class 1 had more chances of surviving compared to people in Class 3.


<h3>OLS Regression</h3>

From numerical exploratory analysis, we see that Survived has a correlation with

1) Survived with Pclass have a R square value of 0.127 and prob(f-stat) of almost 0. This means there exists small positive correlation.

2) Survived with Age have a R square value of 0 and prob(f-stat) of almost 0.105 This means there exists no correlation and it is not statistically significant.

3) Survived with SibSp have a R square value of 0 and prob(f-stat) of almost 0.593. This means there exists no correlation and it is not statistically significant.

4) Survived with ParCh have a R square value of 0.013 and prob(f-stat) of almost 0. This means there exists very small positive correlation.

5) Survived with Fare have a R square value of 0.073 and prob(f-stat) of almost 0. This means there exists very small positive correlation.



<h2>Prediction Model</h2>

<h3>Splitting Data</h3>
For the project, I did an 80-20 split of the train.csv data file.


<h3>Data Pipeline</h3>
For creating the pipeline, I used the OneHotEncoder and the OrdinalEncoder to transform both categorical and ordinal variables.
I then went on to work on building six different models and compare their accuracy scores

<h3>Naive Bayes Model</h3>

<br/>![Naive Bayes](https://github.com/goel-mehul/Titanic-Survival-Prediction-Model/blob/main/Images/Naive%20Bayes%20Output.png "Naive Bayes")
<h4 align="center">Figure 4: Naive Bayes Model Output</h4>

<h3>Logistic Regression Model</h3>

<br/>![Logistic Regression](https://github.com/goel-mehul/Titanic-Survival-Prediction-Model/blob/main/Images/Logistic%20Regression%20Output.png "Logistic Regression")
<h4 align="center">Figure 5: Logistic Regression Model Output</h4>

<h3>Support Vector Machines Model</h3>

<br/>![Support Vector Machines](https://github.com/goel-mehul/Titanic-Survival-Prediction-Model/blob/main/Images/Support%20Vector%20Machines%20Output.png "Support Vector Machines")
<h4 align="center">Figure 3: Support Vector Machines Model Output</h4>

<h3>Decision Tree Classifier Model</h3>

<br/>![Decision Tree Classifier](https://github.com/goel-mehul/Titanic-Survival-Prediction-Model/blob/main/Images/Decision%20Tree%20Output.png "Decision Tree Classifier")
<h4 align="center">Figure 7: Decision Tree Classifier Model Output</h4>

<h3>RandomForrest Classifier Model</h3>

<br/>![RandomForrest Classifier](https://github.com/goel-mehul/Titanic-Survival-Prediction-Model/blob/main/Images/RandomForrest%20Output.png "RandomForrest Classifier")
<h4 align="center">Figure 8: RandomForrest Classifier Model Output</h4>

<h3>AdaBoost Classifier Model</h3>

<br/>![AdaBoost Classifier](https://github.com/goel-mehul/Titanic-Survival-Prediction-Model/blob/main/Images/AdaBoost%20Classifier%20Output.png "AdaBoost Classifier")
<h4 align="center">Figure 9: AdaBoost Classifier Model Output</h4>

<h3>Voting Classifier Model</h3>

<br/>![Voting Classifier](https://github.com/goel-mehul/Titanic-Survival-Prediction-Model/blob/main/Images/VotingClassifier%20Output.png "Voting Classifier")
<h4 align="center">Figure 10: Voting Classifier Model Output</h4>

I used a voting classifier, however it gave a lower accuracy rating compared to the RandomForrest Classifier, which had an accuracy of 81.56. Thus, I decided to move ahead with that model.


<h2>Getting Predictions For Testing Data</h2>

I then followed the same data cleaning and data preparation steps as done earlier. This way the testing dataset was almost similar to the training dataset, and there was high chance of getting a high accuracy score.

<br/>![Predictions](https://github.com/goel-mehul/Titanic-Survival-Prediction-Model/blob/main/Images/Final%20Prediction%20Array.png "Predictions")
<h4 align="center">Figure 11: Prediction Array</h4>

Using the instructions given for generating predictions by Kaggle, I generated the submissions.csv and submitted it on Kaggle to get my accuracy score.
I received an accuracy score of 77.990%. My initial target was to beat the 75% threshold, which I was able to successfully do. 

<br/>![Submission Score](https://github.com/goel-mehul/Titanic-Survival-Prediction-Model/blob/main/Images/Submission%20Score.png "Submission Score")
<h4 align="center">Figure 12: Prediction Array Submission Score</h4>
