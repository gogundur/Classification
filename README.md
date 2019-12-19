 # Term Deposit Opening Decision
 ### AGENDA
- DataSet 
    - DataSet Information
    - Attribute Information
- Descriptive Analysis
    - Visualizing
    - Correlations
- Data Manipulation
    - Null-Missing Value Analysis
    - Encoding Categorical Variables
    - Data Normalization
- Predictive Analysis
    - Sampling
    - Classification Models and Results
- Summary
### Dataset Information

- The data is related with direct marketing campaigns of a Portuguese banking institution. The marketing campaigns were based on phone calls. Data is collacted from http://archive.ics.uci.edu/ml/datasets

- DataSet Often, more than one contact to the same client was required, in order to access if the product (bank term deposit) would be ('yes') or not ('no') subscribed.

- The classification goal is to predict if the client will subscribe (yes/no) a term deposit (variable y).

- The dataset named bank-additional-full.csv have 41188 rows and 20 inputs/columns, ordered by date from May 2008 to November 2010
### Attribute Information

    1 - Age (numeric)
    2 - Job : type of job (categorical)
    3 -Marital : marital status (categorical)
    4 - Education (categorical)
    5 - Default: has credit in default? (categorical)
    6 - Housing: has housing loan? (categorical)
    7 - Loan: has personal loan? (categorical)

#### related with the last contact of the current campaign:
    8 - Contact: contact communication type (categorical)
    9 - Month: last contact month of year (categorical)
    10 - Day_of_week: last contact day of the week (categorical)
    11 - Duration: last contact duration, in seconds (numeric)

#### other attributes:
    12 - Campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
    13 - Pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)
    14 - Previous: number of contacts performed before this campaign and for this client (numeric)
    15 - Poutcome: outcome of the previous marketing campaign (categorical)

#### social and economic context attributes
    16 - Emp.var.rate: employment variation rate - quarterly indicator (numeric)
    17 - Cons.price.idx: consumer price index - monthly indicator (numeric) 
    18 - Cons.conf.idx: consumer confidence index - monthly indicator (numeric) 
    19 - Euribor3m: euribor 3 month rate - daily indicator (numeric)
    20 - Nr.employed: number of employees - quarterly indicator (numeric)
    
### Descriptive Analysis

- We have two types of variables in our data set. These are Continuous Variables and Categorical Variables. 

#### Continuous Variables

- 'age‘ , 'duration', 'campaign', ‘pdays ‘, 'previous', 'emp.var.rate‘
'cons.price.idx', 'cons.conf.idx', 'euribor3m', 'nr.employed'

#### Categorical Variables

- 'job', 'marital', 'education', 'default', 'housing', 'loan’
'contact', 'month', 'day_of_week', 'poutcome', 'y'

### Visualizing – Continuous Variables
![](https://github.com/gogundur/Classification/blob/master/images/continous%20variables%20v1.png)
![](https://github.com/gogundur/Classification/blob/master/images/continous%20variables%20v2.png)

### Visualizing – Categorical Variables
![](https://github.com/gogundur/Classification/blob/master/images/categorical%20variables%20v1.png)
![](https://github.com/gogundur/Classification/blob/master/images/categorical%20variables%20v2.png)

### Correlations
![](https://github.com/gogundur/Classification/blob/master/images/correlations.png)

### Data Manipulation

- We found a high correlation between 4 columns based on the Heat Map  Method. These columns are cons.price.idx, euribor3m, nr.employed,emp.var.rate. Therefore we applied the factor analysis method and created a new column called X_factor. After this process we dropped these columns.

- Duration column/attribute highly affects the output target, we also dropped the Duration column. Because, the duration is not known before a call is performed.
 
- We have numeric attribute named pdays means that number of days that passed by after the client was last contacted from a previous campaign (There are 999 and other numeric values inside of this column. 999 means client was not previously contacted. We converted the 'pdays’ column numeric to categorical. If the value is equal to 999, we put the '0' instead of '999', otherwise we put 1. We dropped the regular 'pdays' column and set column name as 'pdays_cat’

#### One-Hot Encoding

We applied One Hot Encoding method to categorical data with using get dummies function. One hot encoding is a process by which categorical variables are converted into matrix form with 1 and 0 values.

#### Data Normalization

We normalized our numerical data as data preparation. The goal of normalization is to change the values of numeric columns in the data set to use a common scale, without distorting differences in the ranges of values or losing information. We used MinMaxScaler function.

#### Unknown Values

There isn’t Null values but we have unknown values. We kept unknown values . Because, these information is not known during a call is performed.

#### Test-Train Data Split

First step is spliting data into two and selected randomly %80 of data as Training set and %20 of data as Test Set on Python

#### Upsampling

Second step is upsampling to handle unbalanced data. We realized that we have mostly ‘no’ outcome on our dataset.
In upsampling, for every observation in the majority class, we randomly select an observation from the minority class with replacement. The end result is the same number of observations from the minority and majority classes.

## Logistic Regression
- We applied Logistic Regression algorithm which is the most commonly used algorithm for solving all classification problems.

![](https://github.com/gogundur/Classification/blob/master/images/logistic%20regression.png)

## K Nearest Neighbors
- As the second algorithm, we used K Nearest neighbors which is widely used in classification problems because of Ease to interpret output, Calculation time, Predictive Power
![](https://github.com/gogundur/Classification/blob/master/images/knearest%20neighbors.png)

## Random Forest
- As We applied the Random Forest as the third algorithm. RF are among the most popular ML methods because of their relatively good accuracy, robustness and ease of use.

![](https://github.com/gogundur/Classification/blob/master/images/random%20forest.png)

- To get the feature importance scores, we used feature_importances_ function of RandomForestClassifier library. The most important feature of our dataset is X_factor.

![](https://github.com/gogundur/Classification/blob/master/images/random%20forest%20feature.png)

## Summary
    In conclusion, Logistic Regression algorithm has better performance than other algorithms. 

    Minimum MSE ( Predict target variable with minimal error )
    Max Cohen Kappa Score (Controlling accuracy of  the model and compares an Observed Accuracy with an Expected Accuracy (random chance))
    Max Matthew Score (quantifying the quality of predictions)
    Max Accuracy (high accuracy predict the labeled values)
    Max Precision (high accuracy of positive predictions)
    Max Recall (high accuracy predict the target value)
    
![](https://github.com/gogundur/Classification/blob/master/images/summary.png)

