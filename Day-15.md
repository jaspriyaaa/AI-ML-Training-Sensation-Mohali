# 🌳 Day 15: Decision Trees

> **AI/ML Training Program – Day 15**
>
> Today, I learned the fundamentals of **Decision Trees**, a supervised machine learning algorithm widely used for classification and regression tasks. Using the Titanic Survival Prediction dataset, I explored how Decision Trees make predictions, how overfitting occurs, and how regularization techniques improve model performance.

---

# 📌 Learning Objectives

- Understand the working of Decision Trees.
- Learn how Decision Trees split data.
- Understand Gini Impurity.
- Train a Decision Tree classifier.
- Visualize Decision Trees.
- Prevent overfitting using regularization.
- Tune Decision Tree hyperparameters.
- Evaluate model performance.

---

# 📂 Dataset

**Dataset Used:** Titanic Survival Prediction Dataset

**Target Variable:**
- Survived

**Features Used:**
- Passenger Class (Pclass)
- Age
- Fare
- Number of Siblings/Spouses (SibSp)
- Number of Parents/Children (Parch)
- Gender (IsFemale)

---

# 🛠️ Section 0: Imports & Setup

The notebook begins by importing all required Python libraries.

### Libraries Used

- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- DecisionTreeClassifier
- train_test_split
- accuracy_score
- classification_report
- confusion_matrix
- ConfusionMatrixDisplay
- plot_tree

These libraries are used for data preprocessing, visualization, model training, and evaluation.

---

# 📊 Section 1: Load Data & Preprocessing

Before training the model, the dataset was cleaned and prepared.

### Data Preprocessing Steps

### ✅ Handling Missing Values

- Missing values in the **Age** column were filled using the **median**.
- Missing values in the **Embarked** column were filled using the **mode**.

### ✅ Encoding Categorical Features

The **Sex** column was converted into numerical values.

- Male → 0
- Female → 1

A new feature named **IsFemale** was created.

### ✅ Feature Selection

The following columns were selected as input features:

- Pclass
- Age
- Fare
- SibSp
- Parch
- IsFemale

The target variable was:

- Survived

### ✅ Train-Test Split

The dataset was divided into:

- **80% Training Data**
- **20% Testing Data**

This ensures that the model is evaluated on unseen data.

---

# 🌳 Section 2: How Decision Trees Split Data

Decision Trees classify data by repeatedly splitting it into smaller subsets based on feature values.

The algorithm selects the split that produces the purest child nodes.

## Gini Impurity

Decision Trees use **Gini Impurity** to measure the quality of a split.

### Formula

\[
Gini = 1 - \sum p_i^2
\]

where \(p_i\) represents the probability of each class.

### Interpretation

| Gini Value | Meaning |
|------------|---------|
| **0** | Pure node |
| **0.5** | Maximum impurity |

The Decision Tree always chooses the split that minimizes impurity.

---

# 🌲 Section 3: Training an Unconstrained Decision Tree

An unconstrained Decision Tree was trained using:

```python
DecisionTreeClassifier(random_state=42)
```

No restrictions were placed on the tree depth.

### Model Evaluation

The following metrics were calculated:

- Training Accuracy
- Testing Accuracy
- Tree Depth
- Number of Leaf Nodes

### Observation

Since there was no depth limit:

- The tree became very deep.
- Training accuracy became extremely high.
- Testing accuracy decreased.

This demonstrates **overfitting**, where the model memorizes the training data instead of learning meaningful patterns.

---

# 🌿 Section 4: Visualizing Shallow Decision Trees

To improve interpretability, a shallow Decision Tree was created using:

```python
max_depth = 3
```

The notebook uses **plot_tree()** to visualize the model.

The visualization displays:

- Split feature
- Gini impurity
- Number of samples
- Predicted class
- Class distribution

### Benefits

- Easy to understand
- Easy to explain
- Shows decision-making process
- Highlights important features

---

# ⚙️ Section 5: Regularization — Tuning Tree Hyperparameters

Deep trees generally overfit the training data.

To improve generalization, the notebook introduces regularization.

## Hyperparameters

### 1️⃣ max_depth

Limits how deep the tree can grow.

Lower values reduce model complexity.

---

### 2️⃣ min_samples_split

Defines the minimum number of samples required before splitting a node.

Higher values reduce unnecessary splits.

---

### 3️⃣ min_samples_leaf

Defines the minimum number of samples required in each leaf node.

This prevents the creation of very small leaf nodes.

---

## Hyperparameter Tuning

The notebook evaluates tree depths ranging from **1 to 15**.

For each depth:

- Model is trained.
- Training accuracy is calculated.
- Testing accuracy is calculated.

The best depth is selected based on the highest testing accuracy.

A graph comparing training and testing accuracy helps visualize the **bias-variance trade-off**.

---

# 📈 Key Learnings

- Decision Trees split data recursively.
- Gini Impurity determines the best split.
- Deep trees often overfit.
- Regularization improves model generalization.
- Tree visualization makes model interpretation easier.
- Hyperparameter tuning helps achieve optimal performance.

---

# 🛠️ Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

---

# 📚 Skills Gained

- Decision Tree Classification
- Gini Impurity
- Tree Visualization
- Hyperparameter Tuning
- Model Evaluation
- Overfitting Analysis
- Data Preprocessing

---

# ✅ Conclusion

Day 15 focused on understanding **Decision Trees**, one of the most intuitive machine learning algorithms. The session covered data preprocessing, tree construction, visualization, overfitting, and hyperparameter tuning using the Titanic Survival Prediction dataset. These concepts provide a strong foundation for advanced ensemble techniques such as Random Forests.
