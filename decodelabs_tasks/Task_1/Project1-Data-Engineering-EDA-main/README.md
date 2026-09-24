# Data Engineering and Exploratory Data Analysis Pipeline

## Project 1 – E-Commerce Transaction Data

### Overview

This project implements a data preprocessing and exploratory data analysis pipeline for an e-commerce transaction dataset.

The main objective is to transform raw transaction data into a clean, consistent, and structured dataset suitable for further analysis and machine learning. The pipeline focuses on handling missing values, detecting and treating outliers, creating useful features, encoding categorical variables, and reducing redundant information.



## Objectives

The main objectives of this project are to:

- Inspect the structure and quality of the raw dataset.
- Identify and handle missing values.
- Detect and treat numerical outliers.
- Create meaningful features through feature engineering.
- Convert categorical variables into numerical representations.
- Identify highly correlated features.
- Reduce redundant or highly correlated predictors.
- Validate the final processed dataset.
- Export the cleaned dataset for further analysis and machine learning.



## Dataset

The dataset contains e-commerce transaction information, including:

- `Date`
- `Product`
- `Quantity`
- `UnitPrice`
- `TotalPrice`
- `ItemsInCart`
- `CouponCode`
- `PaymentMethod`
- `OrderStatus`
- `ReferralSource`



## Data Preprocessing

### 1. Data Inspection

The raw dataset was first examined to understand its structure, data types, missing values, numerical variables, and categorical features.

### 2. Missing Value Handling

The `CouponCode` feature contained a significant proportion of missing values.

Instead of removing those records, missing values were replaced with:

```text
NoCoupon
```

This preserves the transaction records while clearly representing that no coupon information was available.

### 3. Outlier Detection and Treatment

The Interquartile Range (IQR) method was used to identify potential outliers.

The boundaries were calculated as:

```text
IQR = Q3 - Q1

Lower Bound = Q1 - 1.5 × IQR
Upper Bound = Q3 + 1.5 × IQR
```

Eight extreme observations were identified in the `TotalPrice` feature.

Instead of removing the complete records, the extreme values were capped using `numpy.clip()`. This reduces the influence of extreme values while preserving the associated transaction records.

### 4. Feature Engineering

Three additional features were created:

#### UsedCoupon

A binary indicator showing whether a coupon was used:

```text
1 = Coupon used
0 = No coupon
```

#### OrderMonth

The month was extracted from the `Date` feature using Pandas datetime functions. This feature can help identify possible monthly or seasonal patterns.

#### AvgItemValue

The average value per item was calculated as:

```text
AvgItemValue = TotalPrice / Quantity
```

### 5. Categorical Encoding

The following categorical features were converted using One-Hot Encoding:

- `Product`
- `PaymentMethod`
- `OrderStatus`
- `ReferralSource`

One-Hot Encoding represents each category independently and avoids introducing an artificial numerical ranking between categories.

### 6. Correlation and Multicollinearity Analysis

A correlation matrix was calculated for the numerical predictor variables.

A correlation threshold of `|r| > 0.80` was used to identify highly correlated features.

`AvgItemValue` showed a perfect correlation with `UnitPrice` (`r = 1.0`). Since these features provided redundant information for this dataset, `AvgItemValue` was removed while `UnitPrice` was retained.



## Validation

The final dataset was checked to ensure that:

- Missing values were appropriately handled.
- Numerical outliers were treated.
- Categorical features were encoded.
- Redundant features were removed.
- The final dataset had a consistent structure.
- The processed data was suitable for further analysis.



## Project Workflow

```text
Raw E-Commerce Dataset
        ↓
Data Inspection
        ↓
Missing Value Handling
        ↓
Outlier Detection and Capping
        ↓
Feature Engineering
        ↓
Categorical Encoding
        ↓
Correlation Analysis
        ↓
Removal of Redundant Features
        ↓
Final Validation
        ↓
Cleaned Dataset
```



## Output

The processed dataset was exported as:

```text
Cleaned_Dataset_Project1.csv
```

The final dataset is intended for further exploratory data analysis, statistical analysis, visualization, and machine learning applications.



## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook / Google Colab

---

## Project Structure

```text
Project1-Data-Engineering-EDA/
│
├── data/
│   └── Cleaned_Dataset_Project1.csv
│
├── notebooks/
│   └── Project1_EDA.ipynb
│
├── src/
│   └── preprocessing.py
│
├── Project1_Implementation_Report.pdf
├── README.md
└── requirements.txt
```



## Learning Outcomes

Through this project, I gained practical experience in:

- Data cleaning and preprocessing
- Missing value treatment
- Outlier detection using the IQR method
- Feature engineering
- Categorical data encoding
- Correlation analysis
- Identifying redundant features
- Dataset validation
- Preparing data for machine learning workflows



## Conclusion

This project demonstrates a complete preprocessing workflow for e-commerce transaction data. The raw dataset was systematically cleaned, transformed, and validated to produce a structured dataset that can be used in subsequent exploratory analysis and machine learning tasks.

The project also provided practical experience in making preprocessing decisions based on the characteristics of the dataset rather than applying transformations without evaluation.
