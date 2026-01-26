# Miniproject-IronKaggle

This project consists of a prediction of Sales-data. We got a dataframe called `training.csv`.

It's info is below

<class 'pandas.core.frame.DataFrame'>
RangeIndex: 640840 entries, 0 to 640839
Data columns (total 10 columns):
     Column               Non-Null Count   Dtype 
---  ------               --------------   ----- 
 0   Unnamed: 0           640840 non-null  int64 
 1   store_ID             640840 non-null  int64 
 2   day_of_week          640840 non-null  int64 
 3   date                 640840 non-null  object
 4   nb_customers_on_day  640840 non-null  int64 
 5   open                 640840 non-null  int64 
 6   promotion            640840 non-null  int64 
 7   state_holiday        640840 non-null  object
 8   school_holiday       640840 non-null  int64 
 9   sales                640840 non-null  int64 
dtypes: int64(8), object(2)
memory usage: 48.9+ MB

We prepared the data and trained im multiple models using basically this baselines:

The information above show us that the dataset is composed of 640840 rows with 10 features.
8 of those features are integers:
-    `Unnamed: 0`: `ID variable`:`Should be left out of training`, 
-    `store_ID`: `Store identifier, should be left out of training just to keep bias`,
-    `day_of_week`: `Categorical data, 1-7 representing 1 for Sundaym 2 for Monday and so on, should be treated with get_dummies or OHE`,
-    `nb_customers_on_day`: `Number of buying customers on a day, nice numerical data ranging from 0 to 5458, with mean of 633 and std of 464`, 
-    `open`: `Categorical data meaning if the store is open or not, it has 83% of open, no need for dummies`, 
-    `promotion`: `Categorical data meaning if there is a promotion or not, it has 38% of promotion, no need for dummies`, 
-    `school_holiday`:`Categorical data meaning if there is a school holyday, it has 18% of school holidays, no need for dummies`, 
-    `sales`:`The target variable, a numerical value representing the number of sales ranging from 0 to 41551 in a day`.
2 of those are objects:
-    `date`:`Date type in the format yyyy-mm-dd, shall be treated below`,
-    `state_holiday`:`Categorical data representing if there is no holiday represented by 0 and other types of holidays, we should use dummies`.
No row contains null values.

Results: Our best model was Random Forest we got an R2 score of 94.8 % for our validation data.

We scored the `REAL_DATA.csv` and added on our file `G3.csv` the real data and an extra column `y_pred` which is the prediction of our sales.
