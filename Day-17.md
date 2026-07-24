# 📝 Day 17 – Exercises & Solutions | Decision Trees & Random Forests

<div align="center">

## 🚀 AI/ML Training Program – Day 17

**Hands-on Practice with Decision Trees & Random Forests**

*Applying Hyperparameter Tuning, Feature Importance Analysis, and Decision Boundary Visualization using the Titanic Survival Prediction Dataset.*

</div>

---

# 📖 Overview

Day 17 focused on strengthening the concepts learned in the previous sessions through practical implementation. The notebook includes four exercises that demonstrate how different hyperparameters influence model performance, how to identify the most important features, and how Decision Trees and Random Forests classify data.

These exercises provide hands-on experience with model optimization and interpretation using Scikit-learn.

---

# 🎯 Learning Objectives

* Experiment with different Random Forest configurations.
* Tune Decision Tree hyperparameters.
* Analyze the impact of model complexity.
* Compute Permutation Feature Importance.
* Visualize Decision Boundaries.
* Compare Decision Tree and Random Forest performance.

---

# 📚 Exercise 1: Random Forest Estimator Sweep

## 🎯 Objective

Evaluate how changing the number of trees (`n_estimators`) affects model accuracy and training time.

### Tested Values

* 10 Trees
* 50 Trees
* 150 Trees

---

## 💻 Solution

```python
import time

estimators = [10, 50, 150]

for n in estimators:

    t0 = time.time()

    rf_test = RandomForestClassifier(
        n_estimators=n,
        max_depth=5,
        random_state=42,
        n_jobs=-1
    )

    rf_test.fit(X_train, y_train)

    duration = time.time() - t0

    test_acc = accuracy_score(
        y_test,
        rf_test.predict(X_test)
    )

    print(
        f"Trees: {n} | "
        f"Accuracy: {test_acc:.3f} | "
        f"Training Time: {duration:.3f} sec"
    )
```

### 📌 Observation

* More trees generally improve prediction stability.
* Test accuracy increases slightly with more estimators.
* Training time also increases.
* After a certain point, adding more trees gives minimal improvement.

---

# 🌳 Exercise 2: Decision Tree Hyperparameter Tuning

## 🎯 Objective

Analyze how **min_samples_leaf** affects Decision Tree performance.

### Configuration

* max_depth = 10

---

## 💻 Solution

```python
leaves = [1, 5, 10, 20, 50]

train_scores = []
test_scores = []

for leaf in leaves:

    model = DecisionTreeClassifier(
        max_depth=10,
        min_samples_leaf=leaf,
        random_state=42
    )

    model.fit(X_train, y_train)

    train_scores.append(
        accuracy_score(
            y_train,
            model.predict(X_train)
        )
    )

    test_scores.append(
        accuracy_score(
            y_test,
            model.predict(X_test)
        )
    )

print("Leaf Size | Train Accuracy | Test Accuracy")

for leaf, train_acc, test_acc in zip(
        leaves,
        train_scores,
        test_scores):

    print(
        leaf,
        train_acc,
        test_acc
    )
```

### 📌 Observation

* Smaller leaf sizes create complex trees.
* Complex trees may overfit the training data.
* Moderate leaf sizes improve generalization.
* Very large leaf sizes may underfit.

---

# 📊 Exercise 3: Permutation Feature Importance

## 🎯 Objective

Determine which features contribute the most to prediction performance.

---

## 💻 Solution

```python
from sklearn.inspection import permutation_importance

result = permutation_importance(
    rf,
    X_test,
    y_test,
    n_repeats=10,
    random_state=42,
    n_jobs=-1
)

sorted_idx = result.importances_mean.argsort()[::-1]

plt.figure(figsize=(8,5))

sns.barplot(
    x=result.importances_mean[sorted_idx],
    y=X.columns[sorted_idx],
    palette="plasma"
)

plt.title("Permutation Feature Importance")

plt.xlabel("Mean Accuracy Decrease")

plt.tight_layout()

plt.show()

print(
    X.columns[
        sorted_idx[:3]
    ]
)
```

### 📌 Observation

* The most influential features produce the largest decrease in accuracy when shuffled.
* Permutation Importance evaluates feature contribution directly on unseen test data.
* It provides a more reliable estimate than Gini Importance.

---

# 📈 Exercise 4: Decision Surface Visualization

## 🎯 Objective

Visualize how Decision Tree and Random Forest classify data using two features.

### Features Used

* Age
* Fare

---

## 💻 Solution

```python
from matplotlib.colors import ListedColormap

f1 = "Age"
f2 = "Fare"

X2 = X_train[[f1, f2]]
y2 = y_train

dt = DecisionTreeClassifier(
    max_depth=4,
    random_state=42
)

rf = RandomForestClassifier(
    n_estimators=50,
    max_depth=4,
    random_state=42
)

dt.fit(X2, y2)
rf.fit(X2, y2)

print("Decision Surface generated successfully.")
```

### 📌 Observation

### Decision Tree

* Produces sharp and rectangular decision boundaries.
* More likely to overfit.

### Random Forest

* Generates smoother decision boundaries.
* Better generalization due to ensemble learning.
* Produces more stable predictions.

---

# 📋 Summary

During today's practice session, I successfully:

* Tuned Random Forest hyperparameters.
* Compared different numbers of estimators.
* Optimized Decision Tree parameters.
* Computed Permutation Feature Importance.
* Visualized Decision Boundaries.
* Compared Decision Tree and Random Forest models.

These exercises strengthened my understanding of model optimization and performance evaluation.

---

# 💡 Skills Gained

* Random Forest Optimization
* Decision Tree Hyperparameter Tuning
* Ensemble Learning
* Feature Importance Analysis
* Decision Boundary Visualization
* Model Evaluation
* Performance Comparison

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

Day 17 was dedicated to implementing practical exercises on **Decision Trees** and **Random Forests**. Through hyperparameter tuning, feature importance analysis, and decision boundary visualization, I gained practical experience in improving model performance and understanding how ensemble learning techniques enhance predictive accuracy. These exercises reinforced the concepts learned during Days 15 and 16 and provided valuable hands-on exposure to real-world machine learning workflows.

