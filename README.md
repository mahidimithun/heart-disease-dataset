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

A Confusion Matrix provides a detailed look at where the model made correct predictions and where it faltered by mapping predicted categories directly against true clinical diagnoses from the testing split.

### 📈 Visual Breakdown of the Matrix

* **True Negatives (TN):** Located in the top-left quadrant (`Actual 0 / Predicted 0`). These represent healthy patients who were correctly classified by the model as having **No Heart Disease**.
* **True Positives (TP):** Located in the bottom-right quadrant (`Actual 1 / Predicted 1`). These represent high-risk patients who were accurately diagnosed with **Heart Disease Present**.
* **False Positives (FP):** Located in the top-right quadrant (`Actual 0 / Predicted 1`). These represent false alarms where healthy individuals were incorrectly labeled as positive cases.
* **False Negatives (FN):** Located in the bottom-left quadrant (`Actual 1 / Predicted 0`). These represent missed diagnoses where patients with heart disease were incorrectly flagged as healthy.

---

### 🩺 Diagnostic & Clinical Significance

In medical machine learning, analyzing the quadrants of a confusion matrix is far more vital than checking a single macro accuracy score:

1. **The Cost of False Negatives (Type II Error):** Missed diagnoses represent the absolute highest risk profile in automated medical diagnostics. A false negative means an individual with an active cardiac condition leaves with an incorrect "clean bill of health." Minimizing this quadrant via threshold tuning or recall optimization remains the primary focus of diagnostic pipeline revisions.
2. **The Implications of False Positives (Type I Error):** False alarms cause avoidable psychological distress for patients and trigger unnecessary, expensive secondary screening procedures. Keeping the False Positive rate low ensures that when the system raises a cardiac alert, clinical practitioners can trust its predictive specificity.

---

## 🔬 Final Model Performance Analysis

The classification model achieved highly balanced diagnostic performance on the test dataset, demonstrating robust predictive capability on completely unseen clinical profiles.

### 📑 Class-by-Class Metric Breakdown

#### 🟢 Class 0: No Heart Disease
* **Precision:** Measures the model's accuracy when predicting the absence of disease. A high precision score indicates that the negative assignments are highly reliable and rarely include true heart disease patients.
* **Recall (Sensitivity):** Reflects the model's capacity to find all truly healthy individuals within the dataset without accidentally misclassifying them as positive risks.
* **F1-Score:** The harmonic mean of precision and recall for the negative class, proving stable diagnostic baseline consistency.

#### 🔴 Class 1: Heart Disease Present
* **Precision:** The Positive Predictive Value. This indicates the probability that a patient flagged by the system as having heart disease actually has the condition confirmed by clinical metrics.
* **Recall (Sensitivity):** Tracks the percentage of actual cardiac patients that the model successfully caught. High recall here proves the algorithm's strength in identifying active medical risks.
* **F1-Score:** Confirms the overall diagnostic equilibrium and robustness of the model when handling positive cardiac anomalies.

---

### 🧮 Global Averages & Pipeline Integrity

* **Macro Average:** Computes the unweighted mean of performance metrics across both classes. Its high value confirms that the model maintains deep, independent predictive strength for both categories rather than being artificially inflated by a single majority class bias.
* **Weighted Average:** Factors in class volumes (`Support`) across the dataset. Because the Macro and Weighted metrics track closely together, it proves that our stratified train-test split kept the data perfectly balanced, preventing majority groups from skewing the final decision boundaries.

---

## 💻 Tech Stack Used
**Language:** Python  
**Data Engineering Libraries:** Pandas, NumPy  
**Machine Learning Environment:** Scikit-Learn (`train_test_split`, `StandardScaler`, `confusion_matrix`, `classification_report`)  
**Data Visualization Suite:** Matplotlib, Seaborn
