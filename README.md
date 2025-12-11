# **Fraud Detection Project**

## **Authors**

* Ath Thahir Muhammad Isa Rahmatullah – 5025231181
* Abimanyu Danendra A. – 5025231182
* Alden Zhorif Muhammad – 5025231184

---

## **EDA Output**

```
Starting Comprehensive EDA...
================================================================================
COMPREHENSIVE EXPLORATORY DATA ANALYSIS
================================================================================

1. BASIC DATASET INFORMATION
----------------------------------------
Train dataset shape: (1296675, 23)
Test dataset shape: (555719, 23)

Train dataset columns:
['Unnamed: 0', 'trans_date_trans_time', 'cc_num', 'merchant', 'category', 'amt', 'first', 'last', 'gender', 'street', 'city', 'state', 'zip', 'lat', 'long', 'city_pop', 'job', 'dob', 'trans_num', 'unix_time', 'merch_lat', 'merch_long', 'is_fraud']

Train dataset info:
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 1296675 entries, 0 to 1296674
Data columns (total 23 columns):
 #   Column                 Non-Null Count    Dtype  
---  ------                 --------------    -----  
 0   Unnamed: 0             1296675 non-null  int64  
 1   trans_date_trans_time  1296675 non-null  object 
 2   cc_num                 1296675 non-null  int64  
 3   merchant               1296675 non-null  object 
 4   category               1296675 non-null  object 
 5   amt                    1296675 non-null  float64
 6   first                  1296675 non-null  object 
 7   last                   1296675 non-null  object 
 8   gender                 1296675 non-null  object 
 9   street                 1296675 non-null  object 
 10  city                   1296675 non-null  object 
 11  state                  1296675 non-null  object 
 12  zip                    1296675 non-null  int64  
 13  lat                    1296675 non-null  float64
 14  long                   1296675 non-null  float64
 15  city_pop               1296675 non-null  int64  
 16  job                    1296675 non-null  object 
 17  dob                    1296675 non-null  object 
 18  trans_num              1296675 non-null  object 
 19  unix_time              1296675 non-null  int64  
 20  merch_lat              1296675 non-null  float64
 21  merch_long             1296675 non-null  float64
 22  is_fraud               1296675 non-null  int64  
dtypes: float64(5), int64(6), object(12)
memory usage: 227.5+ MB
None

3. TARGET VARIABLE ANALYSIS
----------------------------------------
Train dataset - Fraud distribution:
  Non-Fraud (0): 1,289,169 (99.42%)
  Fraud (1): 7,506 (0.58%)
  Imbalance Ratio: 171.75:1

Test dataset - Fraud distribution:
  Non-Fraud (0): 553,574 (99.61%)
  Fraud (1): 2,145 (0.39%)
  Imbalance Ratio: 258.08:1

4. CORRELATION ANALYSIS WITH HEATMAP
----------------------------------------
Found 12 numeric columns
Top 10 features positively correlated with fraud:
is_fraud      1.000000
amt           0.219404
hour          0.013799
city_pop      0.002136
lat           0.001894
merch_lat     0.001741
merch_long    0.001721
long          0.001721
cc_num       -0.000981
zip          -0.002162
Top 10 features negatively correlated with fraud:
hour          0.013799
city_pop      0.002136
lat           0.001894
merch_lat     0.001741
merch_long    0.001721
long          0.001721
cc_num       -0.000981
zip          -0.002162
Unnamed: 0   -0.004767
unix_time    -0.005078

5. CATEGORICAL VARIABLES ANALYSIS
----------------------------------------
Found 11 categorical columns
merchant: Unique values: 693
category: Unique values: 14
first: Unique values: 352
last: Unique values: 481
gender: Unique values: 2
street: Unique values: 983
city: Unique values: 894
state: Unique values: 51
job: Unique values: 494
dob: Unique values: 968
trans_num: Unique values: 1296675

6. NUMERICAL VARIABLES DISTRIBUTION
----------------------------------------

7. PAIRPLOT ANALYSIS
----------------------------------------

8. MULTIVARIATE ANALYSIS HEATMAPS
----------------------------------------

9. TEMPORAL ANALYSIS
----------------------------------------

10. OUTLIER ANALYSIS
----------------------------------------

11. STATISTICAL SUMMARY
----------------------------------------
(Statistical summary for train, fraud, and non-fraud transactions)
...

12. DATA QUALITY REPORT
----------------------------------------
Total rows: 1,296,675
Total columns: 28
Total missing values: 0
Percentage of missing values: 0.00%
Top 10 columns with most unique values:
- Unnamed: 0: 1,296,675
- trans_num: 1,296,675
- merch_long: 1,275,745
...

13. FEATURE IMPORTANCE CORRELATION MATRIX
----------------------------------------
Top 20 Most Important Features (correlation with target)
- is_fraud: 1.0
- amt: 0.219
- hour: 0.0138
...

================================================================================
EDA COMPLETED SUCCESSFULLY!
================================================================================
```

---

## **Preprocessing Output**

```
PREPROCESSING TRAINING DATA
1. Extracting features...
2. Dropping unnecessary columns...
3. Handling outliers (amt, city_pop, amt_zscore, amt_per_pop, long_distance_flag)
4. Encoding categorical features...
5. Scaling numerical features...
✅ Preprocessing completed!
   Original shape: (1296675, 28)
   Processed shape: (1296675, 45)

PREPROCESSING TEST DATA
✅ Final Check:
   X_train shape: (1296675, 45)
   y_train shape: (1296675,)
   X_test shape: (555719, 45)
   y_test shape: (555719,)
   Training fraud rate: 0.5789%
   Test fraud rate: 0.3860%
✅ Processed data saved to CSV files
```

---

## **Fraud Detection Pipeline Output**

```
Starting Fraud Detection Pipeline with 3 Key Features...
✅ Data loaded successfully
Training sample: 50,000 rows (fraud: 15.01%)
Test sample: 555,719 rows (fraud: 0.386%)

HYPERPARAMETER OPTIMIZATION WITH OPTUNA
- Best trial F1 Score: 0.9825
- Best model: LGBM

ENSEMBLE WEIGHTS OPTIMIZATION
- RF: F1 = 0.8793
- XGB: F1 = 0.9002
- LGBM: F1 = 0.8953
- Optimized weights: RF=0.33, XGB=0.34, LGBM=0.33

TRAINING RESULTS
- RF: F1=0.3047, Precision=0.1881, Recall=0.8028
- XGB: F1=0.3524, Precision=0.2429, Recall=0.6415
- LGBM: F1=0.4624, Precision=0.3637, Recall=0.6345
- Stacking: F1=0.3850, Precision=0.2611, Recall=0.7329
- Voting: F1=0.4356, Precision=0.3235, Recall=0.6667

BEST MODEL
- LGBM
- F1 Score: 0.4624
- Precision: 0.3637
- Recall: 0.6345
- ROC-AUC: 0.9752

RECOMMENDATIONS
1. Increase sample size
2. Add more feature engineering
3. Try different class balancing techniques
4. Use more complex ensemble methods

✅ PIPELINE COMPLETED SUCCESSFULLY!
```
