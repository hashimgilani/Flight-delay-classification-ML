# Flight Delay Prediction — Boosted Classification Models

This project builds and evaluates tree based and boosting classification models to predict whether a flight will be delayed. A delay is defined as an arrival at least 15 minutes later than scheduled. The analysis focuses on model performance, class imbalance, interpretability, and real-world operational insights.

The dataset includes all commercial flights departing the Washington, DC area and arriving in New York during January 2004.

---

## 🎯 Objective

The goal of this project is to:

- Predict flight delays using classification models
- Compare single trees, AdaBoost, and Gradient Boosting
- Understand the impact of **class imbalance**
- Evaluate models using accuracy, recall, ROC curves, and lift/gains charts
- Translate technical results into actionable airline operations insights

---

## 📂 Dataset
`FlightDelays.csv`
Each row represents a flight with features such as:

- Departure and arrival airports
- Distance
- Day of week
- Scheduled departure time
- Carrier information
- Flight status (Delayed vs On Time)

A flight is labeled **Delayed = 1** if it arrives at least 15 minutes late.

---

## 🧱 Data Preprocessing

Key preprocessing steps:

- Converted **day of week** into a categorical variable
- Converted scheduled departure time into **minutes after midnight**
- Binned departure time into **8 equal time intervals**
- One-hot encoded categorical variables
- Partitioned data into:
  - **60% training**
  - **40% validation**
  - `random_state = 1`
- Verified class imbalance between delayed and on-time flights

---

## 🌲 Models Built

### **1. Single Decision Tree**
- Tuned depth, minimum leaf size, and pruning parameter
- Served as a baseline model
- Performed reasonably but struggled with delayed flights due to class imbalance

---

### **2. AdaBoost Classifier**
- Used shallow decision trees as base learners
- Tuned:
  - Number of estimators
  - Learning rate
  - Base tree depth
- Achieved higher overall accuracy and better stability than a single tree

**Key Insight:**  
AdaBoost improved performance by focusing successive trees on previously misclassified flights.

---

### **3. Weighted Decision Tree**
- Applied class weights to penalize misclassifying delayed flights
- Recall for delayed flights increased significantly
- Overall accuracy dropped, highlighting the tradeoff between accuracy and recall

---

### **4. Gradient Boosting Classifier**
- Tuned:
  - Number of estimators
  - Learning rate
  - Tree depth
- Learned from residual errors rather than reweighting samples
- Achieved similar accuracy to AdaBoost with slightly better probability ranking

---

## 📊 Model Evaluation

Models were evaluated using:

- **Accuracy**
- **Recall for delayed flights**
- **Confusion matrices**
- **ROC curves**
- **AUC (Area Under the Curve)**
- **Lift and gains charts**

Key findings:

- Both AdaBoost and Gradient Boosting outperformed a single decision tree
- Class imbalance caused models to favor on-time flights
- Gradient Boosting produced smoother ROC curves and slightly higher AUC
- Recall for delayed flights remained low without cost-sensitive adjustments

---

## 🔁 Scenario Analysis & Robustness

### **Redefining Delay (≥ 30 Minutes)**
- Delay definition tightened to 30 minutes
- Delayed flights became much rarer
- Overall accuracy increased
- Recall for delayed flights dropped sharply (~5%)

This demonstrates how stricter definitions increase class imbalance and reduce detection of rare events.

---

## ⚠️ Class Imbalance Considerations

Key issues identified:

- Accuracy alone is misleading when delays are rare
- Models tend to predict the majority “on-time” class
- Boosting helps but does not fully solve imbalance

Potential solutions discussed:
- Class weighting
- Threshold adjustment
- Cost-sensitive learning
- Adding more informative predictors

---

## 🧠 Key Insights & Interpretation

Operationally meaningful drivers of delay include:

- **Departure time bins** (busy travel hours)
- **Day of week**
- **Origin airport**
- **Carrier**

These factors align with real airline operations such as congestion, scheduling, and hub traffic.

---

## 🛠 Tools & Technologies

- **Python**
  - pandas, numpy
  - scikit-learn
- **Models**
  - Decision Tree
  - AdaBoost
  - Gradient Boosting
- **Evaluation**
  - Confusion matrix
  - ROC & AUC
  - Lift & gains charts
- **dmba** utilities
- **Jupyter Notebook / Google Colab**

---

## 🧠 What This Project Demonstrates

- End-to-end classification modeling
- Handling class imbalance in real-world data
- Boosting vs single-tree performance
- Interpreting ensemble models
- Translating ML results into business decisions
- Evaluating tradeoffs between accuracy and recall

---

## 🔗 Connect With Me

- **Portfolio:** https://hashimgilani.github.io  
- **LinkedIn:** https://linkedin.com/in/syedhashimgilani  
- **Email:** hashimgilani331@gmail.com  

⭐ *Thanks for checking out this flight delay prediction project!*

