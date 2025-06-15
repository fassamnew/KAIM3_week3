# Project Report: Week 3 Task 1

## Section 1: Setup and Data Loading

### Objective
The goal of this section is to load the dataset and configure the environment for Exploratory Data Analysis (EDA). This includes importing necessary libraries, setting up visualization styles, and loading the data file.

---

### Methodology

#### 1. Import Libraries
- **Libraries Used**:
  - `pandas`: For data manipulation and analysis.
  - `numpy`: For numerical computations.
  - `matplotlib.pyplot`: For data visualization.
  - `seaborn`: For enhanced visualization aesthetics.

#### 2. Configure Plot Styles
- **Plot Settings**:
  - `sns.set_style("whitegrid")`: Sets a clean grid style for plots.
  - `plt.rcParams`: Configures global plot parameters such as figure size, font size, and axis label sizes.

#### 3. Load Dataset
- **File Path**:
  - The dataset is expected to be located at `../../data/MachineLearningRating_v3.txt`.
- **File Format**:
  - The file is a pipe-delimited (`|`) text file.
- **Error Handling**:
  - The `on_bad_lines='skip'` parameter ensures that rows with parsing errors are skipped.

---

Data loaded successfully from './data/MachineLearningRating_v3.txt'
Columns found: ['UnderwrittenCoverID', 'PolicyID', 'TransactionMonth', 'IsVATRegistered', 'Citizenship', 'LegalType', 'Title', 'Language', 'Bank', 'AccountType', 'MaritalStatus', 'Gender', 'Country', 'Province', 'PostalCode', 'MainCrestaZone', 'SubCrestaZone', 'ItemType', 'mmcode', 'VehicleType', 'RegistrationYear', 'make', 'Model', 'Cylinders', 'cubiccapacity', 'kilowatts', 'bodytype', 'NumberOfDoors', 'VehicleIntroDate', 'CustomValueEstimate', 'AlarmImmobiliser', 'TrackingDevice', 'CapitalOutstanding', 'NewVehicle', 'WrittenOff', 'Rebuilt', 'Converted', 'CrossBorder', 'NumberOfVehiclesInFleet', 'SumInsured', 'TermFrequency', 'CalculatedPremiumPerTerm', 'ExcessSelected', 'CoverCategory', 'CoverType', 'CoverGroup', 'Section', 'Product', 'StatutoryClass', 'StatutoryRiskType', 'TotalPremium', 'TotalClaims']
Data loaded with 1000098 rows and 52 columns.


## Section 2: Data Summarization

### Objective
The goal of this section is to summarize the dataset by reviewing its structure and generating descriptive statistics for numerical features. This helps in understanding the central tendency, dispersion, and variability of key numerical columns.

---

### Methodology

#### 2.1 Data Structure (dtype Review)
- **Objective**: Inspect the data types of each column to ensure they are correctly interpreted by pandas.
- **Approach**:
  - Used `df.info()` to review column data types and identify columns that might need type conversion (e.g., objects that should be numeric or datetime).

#### 2.2 Descriptive Statistics
- **Objective**: Calculate descriptive statistics for numerical features to understand their central tendency, dispersion, and shape.
- **Approach**:
  - Selected numerical columns using `df.select_dtypes(include=np.number)`.
  - Used `df.describe()` to generate summary statistics (mean, standard deviation, min, max, etc.).
  - Specifically addressed variability for key financial columns by calculating:
    - Mean
    - Standard Deviation
    - Minimum and Maximum values
    - Interquartile Range (IQR)

---
--- Variability for Key Numerical Features ---

PostalCode:
  Mean: 3,020.60
  Standard Deviation: 2,649.85
  Min: 1.00
  Max: 9,870.00
  Interquartile Range (IQR): 3,353.00

RegistrationYear:
  Mean: 2,010.23
  Standard Deviation: 3.26
  Min: 1,987.00
  Max: 2,015.00
  Interquartile Range (IQR): 5.00

Cylinders:
  Mean: 4.05
  Standard Deviation: 0.29
  Min: 0.00
  Max: 10.00
  Interquartile Range (IQR): 0.00

cubiccapacity:
  Mean: 2,466.74
  Standard Deviation: 442.80
  Min: 0.00
  Max: 12,880.00
  Interquartile Range (IQR): 457.00

kilowatts:
  Mean: 97.21
  Standard Deviation: 19.39
  Min: 0.00
  Max: 309.00
  Interquartile Range (IQR): 36.00

NumberOfDoors:
  Mean: 4.02
  Standard Deviation: 0.47
  Min: 0.00
  Max: 6.00
  Interquartile Range (IQR): 0.00

CustomValueEstimate:
  Mean: 225,531.13
  Standard Deviation: 564,515.75
  Min: 20,000.00
  Max: 26,550,000.00
  Interquartile Range (IQR): 145,000.00

SumInsured:
  Mean: 604,172.73
  Standard Deviation: 1,508,331.84
  Min: 0.01
  Max: 12,636,200.00
  Interquartile Range (IQR): 245,000.00

CalculatedPremiumPerTerm:
  Mean: 117.88
  Standard Deviation: 399.70
  Min: 0.00
  Max: 74,422.17
  Interquartile Range (IQR): 86.78

TotalPremium:
  Mean: 61.91
  Standard Deviation: 230.28
  Min: -782.58
  Max: 65,282.60
  Interquartile Range (IQR): 21.93

TotalClaims:
  Mean: 64.86
  Standard Deviation: 2,384.07
  Min: -12,002.41
  Max: 393,092.11
  Interquartile Range (IQR): 0.00

### Objective
The goal of this section is to assess the quality of the dataset by identifying and handling missing values. This ensures the dataset is clean and ready for further analysis or modeling.

---

### Methodology

#### 3.1 Check for Missing Values
- **Objective**: Identify the presence and percentage of missing values in each column.
- **Approach**:
  - Used `df.isnull().sum()` to calculate the count of missing values for each column.
  - Calculated the percentage of missing values using `(df.isnull().sum() / len(df)) * 100`.
  - Created a DataFrame (`missing_df`) to summarize missing values and sorted it by the percentage of missing values in descending order.

#### Handling Missing Values
- **Steps Taken**:
  1. **Remove Empty Columns**:
     - Columns with 100% missing values were identified and removed.
  2. **Remove Rows with Missing Values**:
     - Rows containing any missing values were removed.
  3. **Validation**:
     - Checked the dataset after handling missing values to ensure no missing values remained.

--- Missing Values Check ---
                         Missing Count  Missing %
NumberOfVehiclesInFleet        1000098      100.0
Removed empty columns: ['NumberOfVehiclesInFleet']
Removed rows with missing values: 0

--- Missing values after handling ---
0
All missing values have been handled.


## Section 4: Univariate Analysis

### Objective
The goal of this section is to analyze the distribution of individual features in the dataset. This includes both numerical and categorical variables to understand their patterns, variability, and potential anomalies.

---

### Methodology

#### 4.1 Distribution of Numerical Variables
- **Objective**: Visualize the distribution of numerical columns using histograms.
- **Approach**:
  - Selected numerical columns (`key_numerical_features`) and added additional relevant columns (`RegistrationYear`, `NumberOfDoors`).
  - Removed duplicates and filtered out columns that do not exist in the dataset.
  - Plotted histograms for each numerical column using `sns.histplot`:
    - Included kernel density estimation (KDE) to visualize the shape of the distribution.
    - Used 30 bins for better granularity.
    - Applied dynamic figure sizing to accommodate all plots.

#### 4.2 Distribution of Categorical Variables
- **Objective**: Visualize the frequency distribution of categorical columns using bar charts.
- **Approach**:
  - Selected categorical columns using `df.select_dtypes(include=['object', 'bool', 'category'])`.
  - Excluded columns containing IDs, dates, or months to focus on meaningful categories.
  - Plotted bar charts for each categorical column using `sns.countplot`:
    - Ordered bars by frequency for better readability.
    - Applied dynamic figure sizing to accommodate all plots.

---

## Section 5: Bivariate and Multivariate Analysis

### Objective
The goal of this section is to explore relationships between multiple features in the dataset. This includes analyzing correlations and associations between numerical variables and aggregating data by PostalCode and TransactionMonth to uncover patterns.

---

### Methodology

#### 5.1 Correlations and Associations: TotalPremium vs. TotalClaims by ZipCode
- **Objective**: Analyze the relationship between monthly changes in `TotalPremium` and `TotalClaims` as a function of `PostalCode`.
- **Approach**:
  1. **Data Preparation**:
     - Converted `TransactionDate` to datetime format and extracted `TransactionMonth` as a period.
     - Aggregated data monthly by `PostalCode` to compute:
       - `MonthlyPremium`: Sum of `TotalPremium`.
       - `MonthlyClaims`: Sum of `TotalClaims`.
       - `NumPolicies`: Count of unique `PolicyID`.
  2. **Visualization**:
     - Created a scatter plot to visualize `MonthlyPremium` vs. `MonthlyClaims` per `PostalCode`.
     - Used log scales for both axes to handle large ranges.
     - Represented `NumPolicies` as the size of points in the scatter plot.

#### Correlation Matrix of Key Numerical Variables
- **Objective**: Compute and visualize correlations between key numerical features.
- **Approach**:
  1. **Data Cleaning**:
     - Selected relevant numerical columns for correlation analysis.
     - Converted columns to numeric format and dropped rows with missing values.
  2. **Visualization**:
     - Generated a heatmap to display the correlation matrix.

---

## Section 6: Data Comparison (Trends Over Geography)

### Objective
The goal of this section is to analyze trends in insurance data across different provinces. This includes comparing average premiums, popular auto makes, and the distribution of cover types.

---

### Methodology

#### 6.1 Average Premium by Province
- **Objective**: Calculate and visualize the average `TotalPremium` for each province.
- **Approach**:
  - Grouped data by `Province` and calculated the mean of `TotalPremium`.
  - Sorted provinces by average premium in descending order.
  - Created a bar plot to visualize the average premium across provinces.

#### 6.2 Top 5 Auto Makes by Province (Count)
- **Objective**: Identify the top 5 most common auto makes in each province.
- **Approach**:
  - Selected the top 5 provinces based on the number of policies for clarity.
  - For each province, counted the occurrences of auto makes and selected the top 5.
  - Created individual bar plots for each province to visualize the top auto makes.

#### 6.3 Distribution of Cover Types by Province
- **Objective**: Analyze the distribution of insurance cover types across provinces.
- **Approach**:
  - Used a count plot to visualize the frequency of cover types (`CoverType`) for each province.
  - Applied a hue to differentiate cover types within each province.

---

## Section 7: Outlier Detection

### Objective
The goal of this section is to identify outliers in numerical data using box plots. Outliers are defined as data points that fall outside 1.5 times the interquartile range (IQR) above the upper quartile or below the lower quartile.

---

### Methodology

#### Outlier Detection Using Box Plots
- **Objective**: Visualize numerical columns to detect outliers.
- **Approach**:
  1. **Column Selection**:
     - Filtered numerical columns (`numerical_cols_for_hist`) based on their presence in the dataset.
     - Excluded irrelevant columns such as `UnderwrittenCoverID`, `PolicyID`, `mmcode`, `NumberOfVehiclesInFleet`, and `PostalCode`.
  2. **Visualization**:
     - Created box plots for each numerical column using `sns.boxplot`.
     - Organized plots in a grid layout for better readability, with up to 4 plots per row.
     - Added titles and labels to each plot for clarity.

---

## Section 8: Creative and Beautiful Plots Capturing Key Insights

### Objective
This section aims to visualize key insights gained from the Exploratory Data Analysis (EDA) in an engaging and informative way. The plots focus on claims behavior, vehicle age, premium distribution, and their relationships with other attributes.

---

### Methodology

#### Plot 1: Claims Frequency and Average Claim Amount by Gender & Marital Status
- **Objective**: Analyze how claims behavior differs based on gender and marital status.
- **Approach**:
  1. **Claims Frequency**:
     - Grouped data by `Gender` and `MaritalStatus` to calculate normalized claims frequency.
     - Visualized the frequency using a stacked bar plot.
  2. **Average Claim Amount**:
     - Grouped data by `Gender` and `MaritalStatus` to calculate the average claim amount.
     - Visualized the average claim amount using a bar plot.

#### Plot 2: Relationship between Vehicle Age, Premium, and Claims
- **Objective**: Explore how the age of the vehicle impacts both premium and claims.
- **Approach**:
  - Calculated `VehicleAge` as the difference between `TransactionDate` and `RegistrationYear`.
  - Created a scatter plot with:
    - `VehicleAge` on the x-axis.
    - `TotalPremium` on the y-axis.
    - `TotalClaims` represented by the size of points.
    - `CoverCategory` represented by color.

#### Plot 3: Premium Distribution by Province and Cover Category
- **Objective**: Visualize the distribution of `TotalPremium` across provinces, split by `CoverCategory`.
- **Approach**:
  - Used a violin plot to show the distribution of premiums.
  - Highlighted variations within provinces and cover categories.

---

### Conclusion of EDA

This Exploratory Data Analysis has provided initial insights into the AlphaCare insurance dataset.
We've examined data structure, quality, and distributions of key variables.

**Key Observations:**
 - Data types were mostly appropriate, with date columns handled.
 - Missing values were addressed using simple imputation strategies - (removed empty columns and rows with empty values).
 - Distributions of financial metrics like `TotalPremium` and `TotalClaims` are highly skewed, indicating a need for potential transformations (e.g., log transformation) for modeling.
 - There are clear variations in average premiums and claims across provinces, and different preferences for auto makes and cover types.
 - Outliers are present in many numerical features, which will require careful consideration during model building.
 - Relationships between vehicle age, premium, and claims, and the impact of demographic factors like gender and marital status on claims behavior, have been highlighted through visualizations.

 These insights will be crucial for guiding the A/B hypothesis testing and machine learning model development phases of the project