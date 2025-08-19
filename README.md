# Early Detection of Diabetic Foot Ulcers using Temperature Asymmetry

This project presents a novel, cost-effective machine learning workflow for the early prediction of Diabetic Foot Ulcers (DFUs). Instead of relying on expensive and complex thermal imaging, this approach leverages simple, sensor-based numerical temperature data. The core of the methodology is the analysis of **temperature asymmetry** between corresponding regions of the left and right feet, which serves as a powerful physiological indicator for inflammation and potential ulceration.

The final model, an **Ensemble Voting Classifier**, not only predicts the risk of DFU with high accuracy but also identifies the specific foot regions at risk and classifies the potential severity for diabetic patients.

---

## ✨ Key Features

* **High-Performance Ensemble Model:** Achieved **97.43% accuracy**, **100% precision**, and a **99% AUC score** using an ensemble of classifiers for robust and stable predictions.
* **Innovative Feature Engineering:** The model's predictive power is built on clinically significant engineered features like `max_temp` and `temp_range`, derived from the temperature difference between feet.
* **Cost-Effective & Accessible:** Provides an effective alternative to expensive infrared thermography by using readily available sensor data, making DFU monitoring more accessible.
* **Explainable AI (XAI) with SHAP:** Integrated **SHAP (SHapley Additive exPlanations)** to ensure model transparency, confirming that `max_temp` and `temp_range` are the most critical predictors for DFU identification.
* **Severity Classification:** The system sub-classifies predicted ulcers in diabetic patients into **Mild, Chronic, or Severe** categories based on the magnitude of the temperature difference, providing actionable insights.

---

## 📊 Dataset

This study utilizes a publicly available dataset from **Niemann et al. (2016)**, which contains plantar foot temperature data for both healthy and diabetic individuals.

* **Participants:** 18 healthy and 25 diabetic individuals.
* **Data Points:** Temperature readings were collected from a sensor-equipped sole across **8 distinct foot regions** (5 Metatarsal heads, Digitus of big toe, Lateral midfoot, and Calcaneus).
* **Final Dataset:** After preprocessing and feature engineering, the dataset was structured with 78 instances and 11 key features for model training.

---

## 🛠️ Methodology

The project workflow is designed for efficiency and interpretability, from data handling to final prediction.

1.  **Data Preprocessing & Feature Engineering:**
    * The core feature, **temperature asymmetry ($\Delta T_i$)**, was calculated as the absolute difference between the mean temperatures of the left and right foot for each of the 8 regions.
    * From this, additional powerful features were engineered: `max_temp`, `min_temp`, and `temp_range` to capture localized inflammation and overall thermal imbalance.
    * A target label was created based on clinical studies, classifying a patient as at risk for an ulcer if the `temp_range` across foot regions exceeds a **3℃ threshold**.

2.  **Model Training & Selection:**
    * A suite of classical machine learning classifiers was benchmarked, including Logistic Regression, SVM, KNN, Random Forest, Naive Bayes, and LightGBM.
    * The dataset was split 50/50 for training and testing to ensure robust evaluation.

3.  **Ensemble Modeling:**
    * To achieve the best and most stable performance, a **Voting Classifier** was constructed.
    * This ensemble model aggregates the predictions from four of the best-performing base models: **Logistic Regression, SVM, KNN, and LightGBM** using a hard voting (majority rule) mechanism.

---

## 📈 Results

The ensemble model demonstrated outstanding and well-balanced performance, proving its efficacy for DFU detection.

### Ensemble Voting Classifier Performance

| Metric | Score |
| :--- | :--- |
| **Accuracy** | **97.43%**  |
| **Precision** | **100%**  |
| **Sensitivity (Recall)** | 96.15%  |
| **F1-Score**| 98.03%  |
| **AUC Score**| 99%  |


### Feature Importance

SHAP analysis confirmed the validity of the feature engineering process, revealing that **`max_temp` and `temp_range`** were the most influential features in the model's decision-making process.


---

## 💻 Tech Stack

* **Programming Language:** Python
* **Machine Learning:** Scikit-Learn
* **Data Manipulation:** Pandas, NumPy
* **Explainable AI:** SHAP
* **Data Visualization:** Matplotlib, Seaborn
* **Hyperparameter Tuning:** Optuna
