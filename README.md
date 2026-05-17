# 💉 Diabetes Prediction using Machine Learning

![Python](https://img.shields.io/badge/Python-3.12-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-F7931E?style=for-the-badge&logo=scikitlearn)
![Machine Learning](https://img.shields.io/badge/Task-Binary%20Classification-success?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

---

## 📌 Project Overview

This project focuses on building a complete end-to-end Machine Learning pipeline for predicting whether a patient is likely to have diabetes based on diagnostic medical attributes.

The notebook was developed with strong attention to:

* Data understanding
* Data cleaning and preprocessing
* Exploratory Data Analysis (EDA)
* Feature engineering
* Machine Learning modeling
* Hyperparameter tuning
* Threshold optimization
* Model evaluation and interpretation
* Medical-oriented recommendation analysis

The project does not only aim to build a predictive model, but also to deeply understand the dataset, identify important medical indicators, and extract practical insights that could help in early diabetes detection.

---

## 🎯 Project Objective

The main goal of this project is to develop a reliable binary classification model capable of predicting diabetes status using patient medical data.

### Target Classes

| Value | Meaning     |
| ----- | ----------- |
| 0     | No Diabetes |
| 1     | Diabetes    |

The project particularly focuses on improving:

* Detection of diabetic patients
* Recall for the positive class
* Reduction of false negatives
* Model reliability in medical scenarios

In healthcare applications, missing a diabetic patient can be more dangerous than generating a false alert. Therefore, the project prioritizes recall and sensitivity in addition to overall accuracy.

---

## 🧠 Why This Project Matters

Diabetes is one of the most common chronic diseases worldwide, and early detection can significantly improve patient outcomes.

Machine Learning can support healthcare systems by:

* Assisting in early diagnosis
* Identifying high-risk patients
* Supporting medical decision-making
* Reducing diagnostic delays
* Improving preventive healthcare strategies

This project demonstrates how data science techniques can be applied to solve real-world healthcare problems.

---

## 📂 Dataset Description

The dataset contains medical and demographic information collected from patients and is used to predict whether a patient has diabetes.

### Dataset Shape

* Rows: 642
* Columns: 10

The dataset contains both numerical and categorical features.

---

## 📊 Features Explanation

| Feature                  | Description                                    |
| ------------------------ | ---------------------------------------------- |
| Pregnancies              | Number of pregnancies the patient has had      |
| Glucose                  | Plasma glucose concentration                   |
| BloodPressure            | Diastolic blood pressure (mm Hg)               |
| SkinThickness            | Triceps skin fold thickness (mm)               |
| Insulin                  | 2-Hour serum insulin (mu U/ml)                 |
| BMI                      | Body Mass Index                                |
| DiabetesPedigreeFunction | Likelihood of diabetes based on family history |
| Age                      | Patient age                                    |
| Gender                   | Patient gender                                 |
| WeightGroup              | Weight category of the patient                 |
| AgeGroup                 | Categorized age group                          |
| Outcome                  | Target variable indicating diabetes status     |

---

## 🔍 Deep Data Understanding

A major part of this project focused on deeply analyzing the dataset before modeling.

### ✔️ Data Type Inspection

The dataset initially contained some inconsistent data types.

Examples:

* `DiabetesPedigreeFunction` was incorrectly stored as an object instead of float
* Some categorical columns contained inconsistent labels

These issues were carefully corrected before modeling.

---

### ✔️ Missing Values Analysis

Missing values existed mainly in:

* Glucose
* BloodPressure
* SkinThickness
* Insulin

#### Handling Strategy

Median imputation was selected because:

* Medical data often contains outliers
* Median is more robust than mean
* It preserves distribution stability

Categorical missing values were handled using mode imputation.

---

### ✔️ Duplicate Records

The dataset contained duplicate rows.

Duplicates were removed before splitting the data to:

* Prevent data leakage
* Improve model generalization
* Ensure fair evaluation

---

### ✔️ Inconsistency Detection

Several data quality issues were identified and fixed.

#### Examples

* Impossible pregnancy value (`1000`) detected and corrected
* Gender inconsistency (`m` vs `M`) standardized
* Typographical issue in obesity categories corrected
* Placeholder values such as `MISSING` replaced properly
* Age group inconsistencies corrected

This stage was extremely important because model quality heavily depends on data quality.

---

## 📈 Exploratory Data Analysis (EDA)

Extensive EDA was performed to understand the dataset behavior and relationships.

### 🔹 Target Distribution

The target variable was relatively balanced, with a slight majority of non-diabetic cases.

This balance allowed accuracy to remain meaningful during evaluation.

---

### 🔹 Feature Distributions

Distributions of numerical features were analyzed to:

* Detect skewness
* Detect outliers
* Understand medical ranges
* Observe feature behavior

Important observations:

* Glucose showed strong separation between diabetic and non-diabetic patients
* Insulin had large variability and extreme values
* BMI and Age showed meaningful trends with diabetes

---

### 🔹 Correlation Analysis

Feature correlation analysis helped identify:

* Strong predictors
* Relationships between variables
* Potential multicollinearity

Glucose consistently appeared as one of the strongest correlated features with diabetes outcome.

---

### 🔹 Outlier Analysis

Outliers were carefully inspected rather than blindly removed because:

* Medical datasets naturally contain extreme cases
* Some extreme values may represent real patients
* Removing them carelessly may reduce medical realism

---

## ⚙️ Data Preprocessing Pipeline

A complete preprocessing workflow was implemented.

### Numerical Processing

* Missing value imputation using median
* Feature scaling where appropriate

### Categorical Processing

* Missing value handling using mode
* Encoding categorical features

### Additional Steps

* Data splitting
* Pipeline integration
* Leakage prevention

The preprocessing pipeline ensured consistent transformations across all models.

---

## 🤖 Machine Learning Models

Several Machine Learning models were trained and evaluated.

### 1️⃣ Logistic Regression

Used as a strong baseline model.

#### Advantages

* Simple and interpretable
* Stable generalization
* Useful coefficient interpretation

---

### 2️⃣ K-Nearest Neighbors (KNN)

Used to explore instance-based learning behavior.

#### Characteristics

* Sensitive to local patterns
* Distance-based classification
* Performance affected by scaling

---

### 3️⃣ Random Forest

The strongest performing model in this project.

#### Advantages

* Handles nonlinear relationships
* Robust against overfitting
* Supports feature importance analysis
* Works well with mixed feature behaviors

Hyperparameter tuning was applied using GridSearchCV.

---

## 🎛️ Hyperparameter Tuning

Model optimization was performed using GridSearchCV to search for the best parameter combinations.

This helped improve:

* Recall
* Generalization
* Stability
* Predictive performance

---

## 🎯 Threshold Optimization

Instead of relying only on the default classification threshold (0.5), threshold tuning was applied.

The threshold was adjusted to improve:

* Detection of diabetic patients
* Positive class recall
* Sensitivity in medical prediction

Final optimized threshold:

```python
0.49
```

This step significantly improved the ability of the model to detect diabetic cases.

---

## 📊 Model Evaluation

Multiple evaluation metrics were used to ensure balanced assessment.

### Metrics Used

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix

---

## 🏆 Final Results

The final selected model was:

### ✅ Random Forest + Optimized Threshold

#### Final Strengths

* Strong diabetic case detection
* Improved recall performance
* Stable overall accuracy
* Better sensitivity for healthcare scenarios

#### Key Observation

Although model accuracies were relatively close, the major difference appeared in recall performance.

This is especially important in medical prediction because detecting diabetic patients is more critical than maximizing raw accuracy.

---

## 🔬 Model Interpretability

Interpretability analysis was performed using:

* Feature importance
* Permutation importance
* Logistic Regression coefficients

### Most Important Features

The most influential predictors included:

* Glucose
* Insulin
* Pregnancies
* SkinThickness
* WeightGroup
* DiabetesPedigreeFunction

#### Important Insight

Glucose consistently appeared as the strongest predictor across nearly all analysis methods.

This aligns with real-world medical understanding of diabetes.

---

## 💡 Practical Insights & Recommendations

The project provides several meaningful healthcare insights.

### Key Recommendations

#### 🩸 Monitor Glucose Carefully

Patients with elevated glucose levels showed significantly higher diabetes risk.

Regular monitoring can support early detection.

---

#### ⚖️ Maintain Healthy Weight

Weight-related features demonstrated noticeable influence on prediction outcomes.

Lifestyle improvements may reduce diabetes risk.

---

#### 👨‍👩‍👧 Family History Matters

DiabetesPedigreeFunction contributed strongly to prediction.

Patients with family history should receive earlier screening attention.

---

#### 🧑‍⚕️ Use ML as Decision Support

Machine Learning models can support — not replace — healthcare professionals.

Such systems can help prioritize high-risk patients for further medical evaluation.

---

## 🛠️ Technologies & Libraries Used

| Tool             | Purpose                            |
| ---------------- | ---------------------------------- |
| Python           | Main programming language          |
| Pandas           | Data analysis and preprocessing    |
| NumPy            | Numerical operations               |
| Matplotlib       | Visualization                      |
| Seaborn          | Statistical visualization          |
| Scikit-Learn     | Machine Learning and preprocessing |
| Jupyter Notebook | Development environment            |

---

## 🚀 How to Run the Project

### 1️⃣ Clone Repository

```bash
git clone https://github.com/Maryam-Skaik/diabetes-prediction-ml-pipeline.git
cd Diabetes-Prediction
```

### 2️⃣ Install Requirements

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 3️⃣ Run Notebook

```bash
jupyter notebook
```

Open:

```bash
Diabetes-Prediction-End-to-End-ML-Project.ipynb
```

---

## 📚 Learning Outcomes

This project helped strengthen practical skills in:

* Real-world data cleaning
* Data preprocessing pipelines
* Exploratory Data Analysis
* Medical dataset understanding
* Machine Learning modeling
* Hyperparameter tuning
* Threshold optimization
* Model evaluation
* Feature importance analysis
* Healthcare-oriented ML thinking

It also emphasized the importance of:

* Data quality
* Preventing leakage
* Choosing metrics carefully
* Understanding business/domain objectives

---

## 🌟 Final Conclusion

This project demonstrates a complete and professional Machine Learning workflow for diabetes prediction.

The work goes beyond simply training a model by focusing on:

* Data quality
* Medical relevance
* Careful evaluation
* Practical interpretability
* Real-world healthcare considerations

The final Random Forest model combined with threshold optimization achieved strong performance in detecting diabetic patients while maintaining stable overall metrics.

Most importantly, the project highlights how Machine Learning can contribute to early disease detection and smarter healthcare support systems.

---

## 👩‍💻 Author

**Maryam Skaik**
Computer Science Graduate | Backend Developer | Data Science & ML Enthusiast
