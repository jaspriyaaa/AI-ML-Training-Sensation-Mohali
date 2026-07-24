# 🌲 Day 16 – Random Forests

## 📌 Overview

Day 16 focused on **Random Forests**, an advanced **ensemble learning algorithm** that combines multiple Decision Trees to produce more accurate and reliable predictions. Unlike a single Decision Tree, Random Forest builds several trees using different subsets of the training data and combines their predictions through majority voting. This approach reduces overfitting, improves generalization, and delivers better performance on unseen data.

In this session, I learned how Random Forest works, trained a Random Forest classifier on the Titanic Survival Prediction dataset, analyzed feature importance, and compared its performance with Logistic Regression and Decision Tree models.

---

# 🎯 Learning Objectives

* Understand the concept of Ensemble Learning.
* Learn Bootstrap Aggregation (Bagging).
* Understand Random Feature Selection.
* Train a Random Forest classifier.
* Evaluate Random Forest performance.
* Understand Feature Importance.
* Compare Random Forest with Logistic Regression.
* Compare multiple Machine Learning classifiers.

---

# 🌳 Section 6: Ensemble Methods — Random Forests

Random Forest is an **ensemble learning algorithm** that builds multiple Decision Trees instead of relying on a single tree. Each tree is trained independently, and the final prediction is obtained by combining the predictions of all trees. This approach reduces the chances of overfitting and improves the model's ability to generalize to new data.

## 🔄 Working Process

### 1️⃣ Bootstrap Sampling (Bagging)

Each Decision Tree is trained on a different random subset of the training dataset. These subsets are created by sampling the data **with replacement**, meaning the same sample may appear multiple times in one subset while others may be excluded.

This process introduces diversity among the trees and helps reduce model variance.

---

### 2️⃣ Random Feature Selection

Instead of considering all available features at every split, Random Forest randomly selects a subset of features for each Decision Tree.

This ensures that every tree learns different patterns from the data, making the overall model more robust and reducing correlation among individual trees.

---

### 3️⃣ Majority Voting

After all Decision Trees make their predictions, the Random Forest combines the results using **majority voting**.

For classification tasks, the class that receives the highest number of votes becomes the final prediction.

This ensemble approach generally produces more accurate and stable predictions than a single Decision Tree.

---

## ✅ Advantages of Random Forest

* Higher prediction accuracy.
* Lower model variance.
* Better generalization on unseen data.
* Reduced risk of overfitting.
* More stable and reliable predictions.
* Works effectively on large and complex datasets.
* Provides feature importance for model interpretation.

---

# 🌲 Section 7: Fitting a Random Forest Classifier

The notebook trains a Random Forest model using the **RandomForestClassifier** from Scikit-learn.

### Model Configuration

* **n_estimators = 100**

  * Builds 100 Decision Trees.

* **max_depth = 5**

  * Restricts the maximum depth of each tree to prevent overfitting.

* **random_state = 42**

  * Ensures reproducible results.

* **n_jobs = -1**

  * Utilizes all available CPU cores for faster training.

---

## 📊 Model Evaluation

After training, the model performance is evaluated using several metrics:

* **Training Accuracy**

  * Measures how well the model performs on the training dataset.

* **Testing Accuracy**

  * Evaluates the model on unseen test data.

* **Cross-validation Accuracy**

  * Measures the model's ability to generalize using multiple train-test splits.

* **Predicted Probabilities**

  * Estimates the probability of each passenger belonging to each class.

* **Confusion Matrix**

  * Displays correct and incorrect classifications, providing a detailed evaluation of prediction performance.

The notebook demonstrates that Random Forest achieves strong performance while maintaining better generalization compared to a single Decision Tree.

---

# 📈 Section 8: Feature Importance — Trees vs. Logistic Regression

One of the most powerful features of Random Forest is its ability to estimate **Feature Importance** using **Gini Importance (Mean Decrease in Impurity)**.

The notebook compares:

* Random Forest Feature Importance
* Logistic Regression Coefficients

A comparison table highlights which features contribute the most to predicting passenger survival.

This analysis helps identify the most influential variables and improves the interpretability of the machine learning model.

---

# 📊 Section 9: Grand Classifier Comparison

The notebook compares the performance of three classification models:

* **Logistic Regression**
* **Tuned Decision Tree**
* **Random Forest**

Each model is evaluated using **testing accuracy** to determine which algorithm performs best on the Titanic Survival Prediction dataset.

This comparison demonstrates the effectiveness of ensemble learning and helps in selecting the most suitable model for the classification task.

---

# 📌 Summary

Key concepts learned during this session include:

* Random Forest combines multiple Decision Trees to improve predictive performance.
* Bootstrap Aggregation (Bagging) reduces model variance.
* Random Feature Selection increases diversity among Decision Trees.
* Majority Voting improves prediction reliability.
* Feature Importance helps interpret model behavior.
* Random Forest generally performs better than a single Decision Tree.
* Comparing multiple machine learning models is essential before selecting the final classifier.

---

# 💡 Skills Learned

* Ensemble Learning
* Random Forest Classifier
* Bootstrap Aggregation (Bagging)
* Random Feature Selection
* Majority Voting
* Feature Importance Analysis
* Model Evaluation
* Cross Validation
* Confusion Matrix Analysis
* Classifier Comparison

---

# 🛠️ Technologies Used

* Python
* NumPy
* Pandas
* Matplotlib
* Seaborn
* Scikit-learn
* Jupyter Notebook

---

# ✅ Conclusion

Day 16 introduced **Random Forests**, one of the most powerful ensemble learning algorithms in Machine Learning. Through this session, I learned how combining multiple Decision Trees using bootstrap sampling and majority voting significantly improves prediction accuracy while reducing overfitting. I also explored feature importance analysis and compared Random Forest with Logistic Regression and Decision Tree models, gaining practical experience in selecting the most effective classification algorithm.
