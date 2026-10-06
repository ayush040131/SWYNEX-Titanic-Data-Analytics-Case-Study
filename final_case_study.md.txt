# Titanic Passenger Survival — Data Analytics Case Study

## 1. Problem Statement

### Business Context

Understanding the factors associated with passenger survival can help demonstrate how data analytics can be used to identify meaningful patterns within a real-world dataset.

The Titanic dataset contains information about passengers, including demographic characteristics, passenger class, fare, family relationships, and survival status.

### Project Objective

The objective of this project is to perform an end-to-end data analytics process on the Titanic passenger dataset by:

- Inspecting and validating the raw dataset
- Identifying and handling missing values and duplicate records
- Preparing a reliable dataset for analysis
- Performing exploratory data analysis to identify patterns and relationships
- Building an interactive Power BI dashboard
- Communicating key findings through data-driven insights

### Key Analytical Questions

This project aims to answer the following questions:

1. How did survival rates differ between male and female passengers?
2. How was passenger class associated with survival?
3. Did passengers traveling alone have different survival rates from those traveling with others?
4. How did average fare differ between survivors and non-survivors?
5. Did the average age differ between survivors and non-survivors?
6. Are there any unusual values or patterns that require further investigation?

## 2. Dataset Information

### Dataset Overview

The Titanic passenger dataset is a publicly available dataset containing information about passengers aboard the RMS Titanic.

The dataset includes demographic, travel, and passenger-class information along with the survival outcome.

### Dataset Source

The dataset was obtained from the publicly available Titanic dataset provided through the Seaborn dataset repository.

### Dataset Size

The original dataset contained:

- **891 rows**
- **15 columns**

After data cleaning, the final analytical dataset contained:

- **780 rows**
- **14 columns**

### Important Variables

| Variable | Description |
|---|---|
| `survived` | Survival status: 0 = Did Not Survive, 1 = Survived |
| `pclass` | Passenger class: 1st, 2nd, or 3rd |
| `sex` | Passenger gender |
| `age` | Passenger age |
| `sibsp` | Number of siblings/spouses aboard |
| `parch` | Number of parents/children aboard |
| `fare` | Passenger fare |
| `embarked` | Port of embarkation |
| `class` | Passenger class as a categorical value |
| `who` | Passenger category: man, woman, or child |
| `adult_male` | Whether the passenger was an adult male |
| `embark_town` | Town associated with the embarkation port |
| `alive` | Survival status as a categorical value |
| `alone` | Whether the passenger was traveling alone |

## 3. Data Cleaning & Preparation

The raw Titanic dataset was inspected using Python and Pandas before performing any transformations.

### 3.1 Initial Data Inspection

The following data-quality checks were performed:

- Dataset dimensions and column names
- Data types
- Missing values
- Duplicate records
- Unique categorical values
- Potentially inconsistent values

### 3.2 Missing Values

The initial dataset contained missing values in the following columns:

| Column | Missing Values | Treatment |
|---|---:|---|
| `age` | 177 | Replaced with the median age |
| `embarked` | 2 | Replaced with the mode |
| `deck` | 688 | Removed due to a very high proportion of missing values |
| `embark_town` | 2 | Replaced with the mode |

### 3.3 Duplicate Records

The initial dataset contained **107 duplicate records** based on complete-row comparison.

These duplicates were removed during the cleaning process.

After missing-value treatment and column removal, an additional duplicate check identified **4 remaining duplicate rows**, which were also removed.

The final dataset therefore contained:

**891 original rows → 780 cleaned rows**

### 3.4 Data Types and Consistency

The dataset data types were inspected to ensure that numerical, categorical, and Boolean fields were represented appropriately.

Categorical values such as gender, passenger class, embarkation port, and survival status were also checked for inconsistent formatting or unexpected categories.

No major categorical inconsistencies requiring manual correction were identified.

### 3.5 Column Removal

The `deck` column was removed because approximately **77% of its values were missing**, making reliable analysis of this variable impractical for this project.

### 3.6 Final Dataset

After cleaning:

- **Rows:** 780
- **Columns:** 14
- **Remaining missing values:** 0
- **Remaining duplicate rows:** 0

The cleaned dataset was saved as:

`data/cleaned_titanic.csv`

## 4. Exploratory Data Analysis

After cleaning the dataset, exploratory data analysis was performed using **Python, Pandas, and Matplotlib**.

The analysis focused on identifying relationships between survival and passenger characteristics.

### 4.1 Overall Survival

The final cleaned dataset contained **780 passengers**.

- Survivors: **322**
- Overall survival rate: **41.28%**

This indicates that fewer than half of the passengers in the cleaned dataset survived.

### 4.2 Survival by Gender

| Gender | Survival Rate |
|---|---:|
| Female | 73.97% |
| Male | 21.72% |

Female passengers had a substantially higher observed survival rate than male passengers.

This was one of the strongest differences identified in the analysis.

### 4.3 Survival by Passenger Class

| Passenger Class | Survival Rate |
|---|---:|
| 1st Class | 63.68% |
| 2nd Class | 50.61% |
| 3rd Class | 25.74% |

Survival rates decreased progressively from 1st class to 3rd class.

This indicates a strong association between passenger class and survival in the analyzed dataset.

### 4.4 Survival by Traveling Status

| Traveling Status | Survival Rate |
|---|---:|
| Traveling with someone | 51.18% |
| Traveling alone | 33.71% |

Passengers traveling with someone had a higher observed survival rate than passengers traveling alone.

### 4.5 Average Fare by Survival Status

| Survival Status | Average Fare |
|---|---:|
| Did Not Survive | 24.03 |
| Survived | 50.19 |

The average fare paid by survivors was considerably higher than the average fare paid by passengers who did not survive.

This is consistent with the observed relationship between passenger class and survival.

### 4.6 Average Age by Survival Status

| Survival Status | Average Age |
|---|---:|
| Did Not Survive | 30.50 years |
| Survived | 28.33 years |

Survivors were approximately **2.17 years younger on average** than non-survivors.

The difference is relatively small compared with the differences observed for gender and passenger class, so age should not be treated as the strongest factor based on this analysis alone.

### 4.7 Outlier and Anomaly Analysis

The maximum recorded fare was **512.3292**, while the median fare was **15.95**.

This represents a substantial difference and makes the maximum fare an important value to investigate.

However, the high fare values were not automatically removed because they can represent legitimate premium fares, particularly among 1st-class passengers.

Therefore, these values were retained while being documented as potential outliers rather than assumed to be data errors.

## 5. Data Visualizations

The exploratory analysis was supported by five visualizations created using **Matplotlib**.

These visualizations were designed to make the major survival patterns easier to interpret.

### 5.1 Survival Rate by Gender

![Survival Rate by Gender](../charts/survival_by_gender.png)

This visualization highlights the substantial difference in observed survival rates between female and male passengers.

### 5.2 Survival Rate by Passenger Class

![Survival Rate by Passenger Class](../charts/survival_by_class.png)

The visualization shows a clear decline in survival rate from 1st class to 3rd class.

### 5.3 Average Age by Survival Status

![Average Age by Survival Status](../charts/average_age_by_survival.png)

This chart compares the average age of passengers who survived with those who did not.

### 5.4 Average Fare by Survival Status

![Average Fare by Survival Status](../charts/average_fare_by_survival.png)

The visualization shows that survivors paid a substantially higher average fare than non-survivors.

### 5.5 Survival Rate by Traveling Status

![Survival Rate by Traveling Status](../charts/survival_by_traveling_status.png)

This visualization compares passengers traveling alone with passengers traveling with others.

## 6. Key Analytical Insights

The analysis identified several important patterns in the cleaned Titanic dataset.

### Insight 1 — Gender was strongly associated with survival

Female passengers had an observed survival rate of **73.97%**, compared with **21.72%** for male passengers.

This represents a difference of approximately **52.25 percentage points**, making gender one of the strongest survival differences observed in the analysis.

### Insight 2 — Passenger class showed a clear survival gradient

The observed survival rate was:

- **63.68%** for 1st class
- **50.61%** for 2nd class
- **25.74%** for 3rd class

The consistent decline across classes suggests a strong association between passenger class and survival.

### Insight 3 — Survivors paid higher fares on average

Passengers who survived paid an average fare of **50.19**, compared with **24.03** among non-survivors.

This difference is consistent with the higher survival rate observed among 1st-class passengers, although fare itself should not be interpreted as a direct cause of survival.

### Insight 4 — Traveling with others was associated with higher survival

Passengers traveling with someone had an observed survival rate of **51.18%**, compared with **33.71%** for passengers traveling alone.

This suggests that traveling status was another meaningful factor associated with survival in the dataset.

### Insight 5 — Age showed a smaller difference

The average age of survivors was **28.33 years**, compared with **30.50 years** for non-survivors.

The difference of approximately **2.17 years** is relatively small compared with the differences observed for gender and passenger class.

### Insight 6 — Extreme fare values require context

The maximum fare of **512.3292** was substantially higher than the median fare of **15.95**.

Although this value is an extreme observation, it was retained because high fares can represent legitimate premium travel rather than data-entry errors.

### Overall Finding

The strongest patterns in this analysis were associated with **gender and passenger class**, while traveling status and fare also showed meaningful differences. Age showed a comparatively smaller difference between survivors and non-survivors.

These findings describe **associations within the dataset and do not establish causal relationships**.

## 7. Interactive Power BI Dashboard

To communicate the analytical findings interactively, a Power BI dashboard was created using the cleaned Titanic dataset.

### 7.1 Dashboard Overview

The dashboard consists of two pages:

#### Page 1 — Titanic Passenger Dashboard

The overview page presents the main KPIs:

- **Total Passengers:** 780
- **Total Survivors:** 322
- **Survival Rate:** 41.28%
- **Average Fare:** 34.83

These KPIs provide a quick summary of the dataset and overall survival outcome.

#### Page 2 — Titanic Survival Analysis

The analysis page provides interactive visualizations for examining survival patterns across different passenger characteristics.

### 7.2 Interactive Filters

The dashboard includes slicers for:

- **Gender**
- **Passenger Class**
- **Traveling Status**

These filters allow users to interactively explore how survival rates change for different passenger groups.

### 7.3 Dashboard Visualizations

The dashboard contains the following visualizations:

1. Survival Rate by Gender
2. Survival Rate by Passenger Class
3. Survival Rate by Traveling Status
4. Average Fare by Survival Status
5. Average Age by Survival Status

### 7.4 Dashboard Features

Key dashboard features include:

- KPI cards for high-level metrics
- Interactive slicers
- Data labels for easier interpretation
- Separate overview and analytical pages
- Consistent visual formatting
- Interactive exploration of survival patterns

### 7.5 Dashboard File

The Power BI dashboard file is available in the repository:

`dashboard/SWYNEX_Titanic_Interactive_Dashboard.pbix`

## 8. Limitations

Although the analysis provides useful insights, several limitations should be considered.

### 8.1 Dataset Limitations

The analysis is based on a historical Titanic passenger dataset. The findings describe patterns within this dataset and may not generalize to other populations or situations.

### 8.2 Duplicate Records

Duplicate removal was based on complete-row comparison. Because the dataset does not contain a unique passenger identifier in the selected version, identical rows cannot always be confirmed as accidental duplicates.

### 8.3 Missing Age Values

Missing age values were replaced using the median age. This provides a complete dataset for analysis but may not represent the actual ages of individual passengers.

### 8.4 Association Does Not Mean Causation

The analysis identifies relationships between variables and survival but does not establish that any particular variable directly caused survival or death.

### 8.5 Dashboard Scope

The Power BI dashboard focuses on descriptive and exploratory analysis. It does not perform predictive modeling or estimate the probability of survival for individual passengers.

## 9. Conclusion

This project demonstrates a complete end-to-end data analytics workflow using the Titanic passenger dataset.

The process began with raw data inspection and cleaning, followed by exploratory analysis using Python and Matplotlib. An interactive Power BI dashboard was then developed to communicate the major findings in a clear and accessible way.

The analysis identified strong differences in observed survival rates across gender and passenger class, while traveling status and fare also showed meaningful associations with survival. Age showed a comparatively smaller difference between survivors and non-survivors.

The project demonstrates practical skills in:

- Data cleaning and preparation
- Exploratory data analysis
- Statistical summary and interpretation
- Data visualization
- Power BI dashboard development
- Interactive filtering
- Analytical storytelling
- Communicating data-driven insights

Overall, the project demonstrates how raw data can be transformed into meaningful insights through a structured analytics workflow.

## 10. Project Workflow

The project followed a structured data analytics workflow:

```text
Raw Titanic Dataset
        ↓
Data Inspection
        ↓
Data Cleaning & Preparation
        ↓
Cleaned Dataset
        ↓
Exploratory Data Analysis
        ↓
Data Visualizations
        ↓
Interactive Power BI Dashboard
        ↓
Key Analytical Insights
        ↓
Final Case Study

## 11. Technologies Used

| Technology | Purpose |
|---|---|
| Python | Data inspection, cleaning, and analysis |
| Pandas | Data manipulation and preparation |
| Matplotlib | Data visualization |
| Microsoft Power BI | Interactive dashboard development |
| GitHub | Project version control and sharing |
| Markdown | Project documentation |

### Project Deliverables

The repository contains:

- Raw Titanic dataset
- Cleaned Titanic dataset
- Python data inspection script
- Python data cleaning script
- Python exploratory analysis script
- Exploratory analysis charts
- Interactive Power BI dashboard
- Complete analytics case study documentation

## 12. Repository Structure

```text
SWYNEX-Titanic-Data-Analytics-Case-Study/
│
├── data/
│   ├── titanic.csv
│   └── cleaned_titanic.csv
│
├── scripts/
│   ├── inspect_data.py
│   ├── clean_data.py
│   └── exploratory_analysis.py
│
├── charts/
│   ├── survival_by_gender.png
│   ├── survival_by_class.png
│   ├── average_age_by_survival.png
│   ├── average_fare_by_survival.png
│   └── survival_by_traveling_status.png
│
├── dashboard/
│   └── SWYNEX_Titanic_Interactive_Dashboard.pbix
│
├── docs/
│   └── final_case_study.md
│
└── README.md

---

## Project Status

**Completed**

This case study combines the complete analytics workflow developed during the SWYNEX Technologies internship, from raw data preparation through exploratory analysis and interactive dashboard development.