# Decision Trees – ML Notes with Real Examples

## 🌳 What are Decision Trees?

A **Decision Tree** is a flowchart-like structure used for making decisions. It splits data based on feature values to classify or predict outcomes.

* Internal nodes = features (e.g., Contains\_Free\_Money)
* Edges = decision outcomes (e.g., Yes/No)
* Leaves = final prediction (Spam / Not Spam)

They're intuitive, interpretable, and used in rule-based systems.

---

## 🧠 Real-Life Use Case: Email Spam Detection

* Features like:

  * Whether the email has "Free Money"
  * Number of links
  * Excessive capital letters
  * Sender reputation
* The tree learns patterns like:

> "IF email contains 'Free Money' AND has 5+ capital letters → THEN Spam"

---

## 🔢 Example – Training a Simple Decision Tree (Depth = 1)

```python
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import accuracy_score
import pandas as pd

data = {
    'Contains_Free_Money': [1, 0, 1, 0, 1, 0, 1, 1, 0, 0],
    'Spam': [1, 0, 1, 0, 1, 0, 1, 1, 0, 0]
}

X = pd.DataFrame(data)['Contains_Free_Money'].values.reshape(-1,1)
y = data['Spam']

clf = DecisionTreeClassifier(criterion='gini', max_depth=1)
clf.fit(X, y)

pred = clf.predict(X)
accuracy = accuracy_score(y, pred)
print("Accuracy:", accuracy)
```

📌 **Result**:

* Before split: 50% (baseline)
* After split: Higher accuracy (depending on decision rule)

---

## 📊 More Complex Example – Using Random Forest

Using features like `Links`, `FreeMoney`, `Caps`, `Reputation`, we can train an ensemble tree model:

```python
from sklearn.ensemble import RandomForestClassifier
import numpy as np

new_email = np.array([[2, 1, 4, 1]])  # Example: 2 links, FreeMoney = yes, 4 caps, reputation = medium
prediction = rf_model.predict(new_email)
```

📌 Output: Whether the email is spam or not.

---

## 📏 Splitting Criterion: Gini Index

The Gini Index measures how "impure" a node is:

* Gini = 0 → perfectly pure (all labels same)
* Gini = high → mixed labels

The goal is to split nodes to reduce Gini impurity.

---

## 🔁 Summary

* Decision Trees break decisions into a set of questions
* Used in real-time systems (email filters, credit risk scoring)
* Highly interpretable but prone to overfitting → solved with ensemble methods like **Random Forests**

---

## 🧩 Keywords

`Decision Tree`, `Gini Index`, `Random Forest`, `Spam Detection`, `Interpretable ML`, `Rule-Based Learning`, `Ensemble Learning`

---


