# Heart Disease Diagnostic Classification Analysis

## 📊 Dataset & Source
This project utilizes the **Kaggle Heart Disease Dataset** (originating from the classic Cleveland Clinic database) to classify whether a patient has an absence (`0`) or presence (`1`) of heart disease based on 14 clinical, physiological, and metabolic indicators.

🔗 **Dataset Link:** [Kaggle - Heart Disease Dataset](https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset/data)

---

## 🛠️ Code Workflow & Implementation Steps

The Python pipeline is executed sequentially to transform raw medical metrics into reliable predictive outputs:

1. **Exploratory Data Analysis (EDA):** Evaluated data shapes, confirmed the absence of missing values, and mapped feature distributions for structural inconsistencies across the 1,025 samples using `Seaborn` and `Matplotlib`.
2. **Clinical Metric Profiling:** Inspected continuous variables (such as cholesterol, age, and max heart rate) against discrete categorical measurements (such as chest pain type and thalassemia) to understand underlying patterns.
3. **Train-Test Division:** Split the dataset into training ($80\%$) and testing ($20\%$) subsets using stratified splitting to ensure that the proportions of healthy and heart disease patients remained identical across both splits.
4. **Feature Standardization:** Initialized a feature scaling pipeline to normalize continuous metrics with highly varied numeric ranges (e.g., comparing blood pressure numbers to decimals). This prevents variables with larger magnitudes from biasing the classification boundaries.
5. **Model Training:** Configured and trained a supervised classification model optimized to establish complex decision hyperplanes capable of differentiating healthy patients from cardiovascular risk cases.
6. **Performance Assessment:** Extracted predictions from the unseen test split and compiled a full metric suite including accuracy scoring, a detailed classification report, and a confusion matrix visualization.

---

## 📈 Visualizations & Graph Analysis

### 1. Feature Correlation Heatmap
<img width="767" height="585" alt="hd_correlation_heatmap" src="https://github.com/user-attachments/assets/d10c121d-8a04-4fc3-b23f-06c3fd296206" />

**Analysis:** This heatmap visualizes the Pearson correlation coefficients across the dataset features. It tracks how clinical attributes interact with one another and the final target variable. Key indicators like chest pain type (`cp`) and maximum heart rate achieved (`thalach`) demonstrate prominent positive correlations with the presence of heart disease, whereas exercise-induced angina (`exang`) shows an inverse relationship. These insights help isolate which physiological metrics provide the model with the strongest directional signals.

### 2. Clinical Data Distribution
<img width="1067" height="392" alt="hd_graph" src="https://github.com/user-attachments/assets/16def8d0-d3c9-465d-b1d2-f3823ac16763" />

**Analysis:** A matrix of individual charts illustrating the distribution and density split of patient metadata between healthy individuals (0) and those with heart disease (1). By analyzing continuous metrics like age, resting blood pressure (`trestbps`), and cholesterol (`chol`), we can pinpoint specific clinical thresholds where statistical separation occurs—allowing us to observe how clinical variance directly feeds the model's underlying classification criteria.

---

## 🔬 Model Performance Evaluation

<img width="491" height="622" alt="confusion_matrix_report_hd" src="https://github.com/user-attachments/assets/9aceb53e-6d4d-43ed-9d7c-ffa38a94deb3" />

## 🧩 Confusion Matrix Analysis

A Confusion Matrix provides a detailed look at where the model made correct predictions and where it faltered by mapping predicted categories directly against true clinical diagnoses.

Based on the testing split evaluation (**205 samples**), the model achieved an overall **Model Accuracy of 80.98%** (rounded to 0.81 in the report) with the following distribution:

---

### 📈 Visual Breakdown of the Matrix

* **True Negatives (TN) = 70:** The model predicted **No Disease (0)** for 70 samples, and they were truly healthy.
* **True Positives (TP) = 96:** The model predicted **Disease (1)** for 96 samples, and they were truly diagnosed with a cardiac condition.
* **False Positives (FP) = 30:** The model made 30 false alarms, mistakenly flagging healthy individuals as having heart disease.
* **False Negatives (FN) = 9:** The model missed 9 actual heart disease cases, mistakenly predicting them as healthy.

---

### 🩺 Diagnostic & Clinical Significance

In medical machine learning, analyzing the quadrants of a confusion matrix is far more vital than checking a single macro accuracy score:

1. **The Cost of False Negatives (Type II Error):** The 9 missed cases represent the most critical risk in medical diagnostics. A false negative means an individual with an active cardiac condition leaves with an incorrect "clean bill of health." Lowering this number to zero is the primary goal of future parameter tuning to maximize patient safety.
2. **The Implications of False Positives (Type I Error):** The 30 false alarms represent individuals who do not have heart disease but were flagged by the model. While medically safer than a false negative, false positives cause preventable patient anxiety and require secondary confirmation procedures, tying up clinical resources.

---

### 🟢 Class-by-Class Metric Breakdown

#### 🔹 Class 0: No Heart Disease (100 Samples)
* **Precision (0.89):** Out of all cases the model predicted as healthy, 89% of them were truly free of heart disease. This indicates high reliability when the model delivers a clean report.
* **Recall (0.70):** The model successfully caught 70% of the actual healthy individuals in the test set, while misclassifying 30% of them as positive risks.
* **F1-Score (0.78):** Indicates a solid baseline performance for capturing healthy patient profiles.

#### 🔸 Class 1: Heart Disease Present (105 Samples)
* **Precision (0.76):** When the model flags a patient as having heart disease, it is correct 76% of the time.
* **Recall (0.91):** **High Sensitivity.** Out of 105 patients who actually had heart disease, the model successfully identified 91% of them (96 patients), missing only 9%. In medical analytics, a high recall for the positive disease class is crucial.
* **F1-Score (0.83):** Confirms a strong diagnostic capability for capturing positive cardiac anomalies.
---

## 💻 Tech Stack Used
**Language:** Python  
**Data Engineering Libraries:** Pandas, NumPy  
**Machine Learning Environment:** Scikit-Learn (`train_test_split`, `StandardScaler`, `confusion_matrix`, `classification_report`)  
**Data Visualization Suite:** Matplotlib, Seaborn
