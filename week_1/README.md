# Student Performance Prediction Using Machine Learning

An exploratory data analysis and machine learning project to understand student academic performance and classify students into grade categories based on their study habits, attendance, and classroom participation.

## 1. Project Overview

This project analyzes a Student Performance Dataset containing 1,000,000 student records. It investigates the relationship between students' academic performance and three important factors:

- Weekly self-study hours
- Attendance percentage
- Class participation

Machine learning classification models are trained to predict student grade categories: A, B, C, D, and F.

## 2. Objectives

- Understand and analyze the student performance dataset.
- Perform data cleaning and exploratory data analysis.
- Identify patterns and relationships among academic variables.
- Prepare features for machine learning.
- Train and evaluate multiple classification algorithms.
- Compare model performance using accuracy and macro F1 score.
- Identify the most influential input features.

## 3. Dataset Description

The dataset contains **1,000,000 records and 6 columns**.

| Column | Description |
|---|---|
| student_id | Unique student identifier |
| weekly_self_study_hours | Hours spent studying independently per week |
| attendance_percentage | Student attendance percentage |
| class_participation | Measure of classroom participation |
| total_score | Student's total academic score |
| grade | Final grade category (A, B, C, D, F) |

### Data Quality

The following checks were performed:

- Missing values
- Duplicate records
- Duplicate student IDs
- Invalid numerical ranges
- Data types and column inspection

No missing values, duplicate rows, duplicate student IDs, or invalid values were detected in the checks performed.

## 4. Exploratory Data Analysis

EDA was performed to understand individual feature distributions and relationships between variables.

### Univariate Analysis
- Histograms of numerical variables.
- Distribution of student grades.
- Analysis of study hours, attendance, participation, and total scores.

### Bivariate Analysis
- Study hours versus total score.
- Attendance versus total score.
- Class participation versus total score.
- Score distributions across grade categories.

### Multivariate Analysis
- Correlation matrix.
- Correlation heatmap.
- Relationships among numerical features.

### Advanced EDA
- Outlier identification using the IQR method.
- Box plots and feature-to-feature comparisons.
- Grouped analysis of student performance.
- Pearson and Spearman correlation analysis.

### Key Findings

- Weekly self-study hours showed a strong positive correlation with total score (Pearson correlation approximately 0.812).
- Attendance and class participation showed correlations close to zero with total score.
- Average scores generally increased with weekly self-study hours.
- The increase in average scores became smaller as scores approached the maximum of 100.
- Grade A was the most frequent category, representing approximately 54.86% of the dataset.

## 5. Machine Learning Preparation

The project was formulated as a multiclass classification problem.

**Target variable:** `grade`

**Input features:**
- `weekly_self_study_hours`
- `attendance_percentage`
- `class_participation`

The `student_id` column was excluded because it is an identifier rather than a meaningful predictive measurement.

The `total_score` column was excluded because it is closely tied to the grade assignment and could introduce target leakage.

The dataset was divided into training and testing sets using an 80:20 split, with stratification to preserve grade proportions.

## 6. Machine Learning Models

The following classification models were trained and evaluated:

1. Dummy Classifier
2. Logistic Regression
3. Weighted Logistic Regression
4. Decision Tree Classifier
5. Random Forest Classifier

StandardScaler was used in the Logistic Regression pipeline. Class weighting was also explored to address the imbalance among grade categories.

## 7. Model Evaluation

Two evaluation metrics were used:

- **Accuracy:** Measures the proportion of correctly classified samples.
- **Macro F1 Score:** Calculates the F1 score independently for each grade category and takes their unweighted average.

Macro F1 is particularly useful here because the grade distribution is imbalanced.

### Model Comparison

| Model | Accuracy | Macro F1 |
|---|---:|---:|
| Dummy Classifier | 54.86% | 0.1400 |
| Logistic Regression | 69.58% | 0.4496 |
| Weighted Logistic Regression | 64.43% | 0.4535 |
| Decision Tree | 60.06% | 0.4017 |
| Random Forest | 63.94% | **0.4659** |

### Best Model

Random Forest achieved the highest macro F1 score of approximately **0.4659**.

Logistic Regression achieved the highest accuracy of approximately **69.58%**.

Random Forest provided the strongest overall balance across the five grade categories according to macro F1, although its accuracy was lower than Logistic Regression's.

## 8. Feature Importance

Feature importance was extracted from the trained Random Forest model.

| Feature | Importance |
|---|---:|
| Weekly self-study hours | 0.8690 |
| Attendance percentage | 0.0766 |
| Class participation | 0.0544 |

### Interpretation

Weekly self-study hours contributed the largest share of the Random Forest model's feature importance.

This indicates that the model relied much more heavily on study hours than on the other two input features when making predictions.

Feature importance represents the model's relative reliance on features; it does not establish causation.

## 9. Conclusion

This project explored student academic performance through data cleaning, exploratory data analysis, and multiclass machine learning classification.

The analysis identified weekly self-study hours as the strongest feature associated with total academic scores.

Five classification models were evaluated. Random Forest achieved the highest macro F1 score, while Logistic Regression achieved the highest accuracy.

The results demonstrate how machine learning techniques can be used to explore academic performance patterns and classify student grades using selected behavioral and academic features.

## 10. Limitations

- The dataset contains only three selected predictive input features.
- The grade distribution is imbalanced.
- Performance for minority grade categories, particularly F, remains relatively weak.
- Feature importance does not establish a causal relationship.
- Model performance may differ on real-world student datasets.

## 11. Future Scope

- Explore additional student-related features.
- Experiment with hyperparameter optimization.
- Investigate advanced ensemble classification techniques.
- Improve minority-class prediction performance.
- Develop an interactive interface for student grade prediction.
- Evaluate model generalization on independent datasets.

## 12. Project Structure

```text
Internship Project/
│
├── .gitignore
│
└── week_1/
    ├── file1.ipynb
    ├── README.md
    ├── student_performance.csv
    ├── feature_engineered_dataset.csv
    └── final_ml_dataset.csv
```

## 13. How to Run

1. Clone or download the project repository.
2. Open the `week_1` folder.
3. Launch Jupyter Notebook.
4. Open `file1.ipynb`.
5. Execute the notebook cells sequentially.

Ensure the required Python libraries are installed and the dataset is available in the notebook's working directory.

## 14. Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

---

**Project:** Student Performance Prediction Using Machine Learning  
**Project Type:** Machine Learning / Data Analysis  
**Task:** Multiclass Classification