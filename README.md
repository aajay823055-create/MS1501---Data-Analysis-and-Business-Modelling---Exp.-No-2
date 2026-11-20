# Exp No.2 : Exploratory Data Analysis (EDA)

## Aim
To perform Exploratory Data Analysis (EDA) on the heart disease dataset to understand the data distribution, relationships, and key patterns useful for business insights and model building.

## Dataset
The dataset used for this experiment is `heartdisease.csv`. It contains medical and demographic information such as age, sex, cholesterol levels (`totChol`), `BMI`, blood pressure, and target values (`TenYearCHD`) indicating heart disease presence.

## Algorithm
1. Import required Python libraries (`numpy`, `pandas`, `seaborn`, `matplotlib`).
2. Load the dataset into a Pandas DataFrame.
3. Display the dataset structure, shape, and descriptive statistics.
4. Check for missing values and duplicate rows.
5. Examine correlations among numeric features using a correlation matrix and heatmap.
6. Visualize univariate distributions using histograms, boxplots, and countplots.
7. Analyze bivariate and multivariate relationships using scatter plots and pairplots.

## Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Basic Exploration** | `df.info()` | Inspect dataset structure and data types |
| | `df.describe()` | Generate descriptive statistics |
| | `df.isnull().sum()` | Detect missing values in each column |
| | `df.duplicated().sum()` | Identify duplicate rows |
| | `df.corr()` | Find correlations between numeric variables |
| **Univariate Analysis** | `sns.histplot()` | Plot histogram (distribution of single variable) |
| | `sns.boxplot()` | Identify outliers using boxplot |
| | `sns.countplot()` | Count occurrences of categorical variables |
| **Bivariate Analysis** | `sns.scatterplot()` | Display relationship between two variables |
| | `sns.heatmap()` | Show correlation matrix visually |
| **Multivariate Analysis** | `sns.pairplot()` | Show pairwise relationships across variables |
| **Visualization Controls** | `plt.figure()`, `plt.title()`, `plt.xlabel()`, `plt.ylabel()`, `plt.show()` | Configure and display plotted charts |

## Program & Output

# Exploratory Data Analysis (EDA) on Heart Disease Dataset

# Step 1: Import Essential Libraries
import numpy as np  
import pandas as pd  
import seaborn as sns  
import matplotlib.pyplot as plt  

# Step 2: Load the Dataset
df = pd.read_csv(r'C:\Python Code 2025\0 Dataset\heartdisease.csv')  

# Step 3: Basic Exploration

# Inspect dataset structure and data types
print("\n--- Dataset Information ---")  
print(df.info())  

# Generate descriptive statistics
print("\n--- Descriptive Statistics ---")  
print(df.describe())  

# Check number of rows and columns
print("\n--- Dataset Shape ---")  
print("Rows:", df.shape[0], "Columns:", df.shape[1])  

# Display first 10 rows
print("\n--- First 10 Rows ---")  
print(df.head(10))  


# Step 4: Check Data Quality

# Check missing values
print("\n--- Missing Values in Each Column ---")  
print(df.isnull().sum())  

# Check duplicate rows
print("\n--- Number of Duplicate Rows ---")  
print(df.duplicated().sum())  


# Step 5: Correlation Analysis

# Calculate correlation between numeric columns
print("\n--- Correlation Matrix ---")   
print(df.corr(numeric_only=True))  

# Visualize correlation using heatmap
plt.figure(figsize=(10, 6))   
sns.heatmap(  
    df.corr(numeric_only=True),  
    annot=True,   
    cmap='coolwarm'   
)  
plt.title("Correlation Heatmap of Heart Disease Dataset")  
plt.show()  


# Step 6: Univariate Analysis

# Histogram for Age distribution
print("\n--- Histogram for Age Distribution ---")  
plt.figure(figsize=(8, 5))   
sns.histplot(df['age'], kde=True, bins=20, color='teal')   
plt.title("Distribution of Age")    
plt.xlabel("Age")    
plt.ylabel("Count")   
plt.show()   

# Boxplot for Cholesterol
print("\n--- Boxplot for Cholesterol ---")    
plt.figure(figsize=(6, 4))    
sns.boxplot(x=df['totChol'])    
plt.title("Boxplot of Cholesterol Levels")   
plt.xlabel("Cholesterol")    
plt.show()    

# Countplot for Gender
print("\n--- Countplot for Gender ---")     
if 'sex' in df.columns:   
    plt.figure(figsize=(5, 4))   
    sns.countplot(x='sex', data=df)   
    plt.title("Count of Gender")   
    plt.xlabel("Sex (0 = Female, 1 = Male)")   
    plt.ylabel("Count")   
    plt.show()   


# Step 7: Bivariate Analysis

# Scatter plot: Age vs Cholesterol
print("\n--- Scatter Plot: Age vs Cholesterol ---")   
plt.figure(figsize=(8, 5))    
sns.scatterplot(   
    x='age',   
    y='totChol',   
    data=df,   
    hue='TenYearCHD',   
    palette='coolwarm'   
)   
plt.title("Age vs Cholesterol (by Heart Disease Target)")  
plt.xlabel("Age")   
plt.ylabel("Cholesterol")   
plt.show()   


# Step 8: Multivariate Analysis

# Pairplot for multiple relationships
print("\n--- Pairplot for Multiple Relationships ---")  

selected_columns = ['age', 'totChol', 'BMI', 'TenYearCHD']   

sns.pairplot(   
    df[selected_columns],   
    diag_kind='kde'   
)  

plt.suptitle(  
    "Pairwise Relationship between Variables",      
    y=1.02   
)  
plt.show()   


## Result
