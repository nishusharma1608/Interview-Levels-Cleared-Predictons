# Job-interview-data
### ABOUT THE DATA
The dataset consists of curated features that provides a mapping of attributes of Jobs a.k.a requisitions and candidates. 
It is divided into 60:20:20 :: training:validation:testing sets.

### CLASSIFICATION TASK
Use features in the dataset to predict "Requisition_levels_cleared_category" (representing the interview level cleared by a candidate, the more the higher, and it can go up till the maximum levels in a job i.e. "requisition_levels") using Machine Learning / Deep Learning

### EXPLORATORY DATA ANALYSIS
To know the data more, EDA was performed and the following things were determined : 
- Shape of the training,testing and validation sets
- Number of missing values for each column
- Number of unique values for each column
- Datatypes of all features
- Number of Negative values for each feature
- Correlation matrix 

### DATA CLEANING AND PREPROCESSING
The following tasks were performed :
- Removal of 1st column named 'Unnamed : 0' which contains only numbers from 0 to 231916 (length of the dataset)
- Imputing missing values by '-1' 
- Removal of columns 'CandidateCity' and 'RequisitionCity' as it contained some noise in the form of textual data. Moreover, the information in columns 'CandidateCity' and 'RequisitionCity' is already captured in columns 'CandidateCityID' and 'RequisitionCityID' respectively

### DATA VISUALIZATION
Histograms for all features were plotted to gain info about any unusual distribution

### DATA SCALING
All the features had values which had disparate ranges. To bring them down to the same level, all features were scaled using a StandardScaler so that no features outweighs other features.
All features, after scaling, will be treated equally by all suverpised learning algorithms.

### OBSERVATIONS
- Features ('requisition_levels', 'OrganizationID') and ('Requisition_minexp', 'Requisition_maxexp') were found to have correlation greater than 0.8. None of the features (which were correlated) was removed as all features seem to capture important information and stand utmost importance in the data
- No features were highly correlated with the target variable 'Requisition_levels_cleared_category'
- 'Cand_exp' , whcich signifies the experience a candidate has, contains negative values, which is disturbing
- The features 'Matching Designation' and 'Cand_exp' are more correlated (as compared to other features) with our target variable 'Requisition_levels_cleared_category'
- The crosstable between 'Matching_Designation' and our target variable clearly shows that all the candidates with matching designations cleared atleast round 1 and reached to round 2. This means, assured clearance for round 1 of any interview if Matching_Designation = 1 !!

### ALGORITHMS APPLIED
### 1. Multinomial Logistic Regression
#### Why?
First, logistic regression does not require a linear relationship between the dependent and independent variables.  
Second, the error terms (residuals) do not need to be normally distributed.  
Third,  logistic regression requires the observations to be independent of each other.  
Fourth, the dependent variable in logistic regression is not measured on an interval or ratio scale.
Finally, logistic regression typically requires a large sample size.

Logistic Regression is hence the best choice for our data.

'max_iter' parameter was tuned as a warning was received that newton-cg (the solver) failed to converge

### 2. Naive Bayes
First, independent features
Second, it is easy and fast to predict class of test data set. 
Third, it also performs well in multi class prediction.

MultinomialNB wasn't used as it didn't allow negative values
BernoulliNB was ruled out as it is used only for boolean/binary data
GaussianNB was finally selected

### 3. Support Vector Machine
t works really well with clear margin of separation
It is effective in high dimensional spaces.
It uses a subset of training points in the decision function (called support vectors), so it is also memory efficient.

### 4. Decision Trees
Decision trees are used just to check whether the accuracy provided by other models matches with the one produced by it or not
Decision trees are prone to overfitting, hence this model shouldn't be selected.

### 5. Neural Networks
Neural network didn't perform well as it requires HUGE amount of data for training. Accuracy is not that impressive, as even the number of epochs is less.
Accuracy will increase if we increase number of epochs, only on the cost of losing a lot of time as well as computation power.




 
