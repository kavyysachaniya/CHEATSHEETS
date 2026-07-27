# CHEATSHEET FOR ML

> **Universal Machine Learning Template**  
> Covers:
> - Linear Regression
> - Multiple Regression
> - Polynomial Regression
> - KNN
> - Decision Tree
> - Random Forest
> - SVM

---

# 1. IMPORT LIBRARIES

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import accuracy_score, r2_score, mean_squared_error, mean_absolute_error, confusion_matrix
from sklearn.preprocessing import PolynomialFeatures
from sklearn.neighbors import KNeighborsClassifier
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
from sklearn.svm import SVC
import numpy as np
import matplotlib.pyplot as pt
```

---

# 2. LOAD DATASET

```python
data = pd.read_csv("diabetes.csv")
```

---

# 3. DATA PREPROCESSING

## Handle Missing Values

```python
cols_zero = ['Glucose', 'BloodPressure', 'SkinThickness', 'Insulin', 'BMI']

for i in cols_zero:
    data = data[data[i] != 0]
```

## Define Features & Target

```python
x = data.drop('Outcome', axis=1)      # Multiple Features
y = data['Outcome']
```

---

# 4. TRAIN TEST SPLIT

```python
x_train, x_test, y_train, y_test = train_test_split(
    x, y,
    test_size=0.2,
    random_state=41
)
```

---

# 5. LINEAR / MULTIPLE REGRESSION

```python
model = LinearRegression()

model.fit(x_train, y_train)

y_pred = model.predict(x_test)
```

---

# 6. POLYNOMIAL REGRESSION

## Create Polynomial Features

```python
poly = PolynomialFeatures(degree=2)

x_train_poly = poly.fit_transform(x_train)
x_test_poly = poly.transform(x_test)
```

## Train Model

```python
model = LinearRegression()

model.fit(x_train_poly, y_train)

y_pred = model.predict(x_test_poly)
```

---

# 7. K-NEAREST NEIGHBOUR (KNN)

```python
model = KNeighborsClassifier(
    n_neighbors=3
)

model.fit(x_train, y_train)

y_pred = model.predict(x_test)
```

## Confusion Matrix

```python
cm = confusion_matrix(y_test, y_pred)

TN, FP, FN, TP = cm.ravel()

specificity = TN / (TN + FP)
```

---

# 8. DECISION TREE

```python
model = DecisionTreeClassifier(
    criterion='entropy',
    random_state=42,
    max_depth=None      # or any integer
)

model.fit(x_train, y_train)

y_pred = model.predict(x_test)
```

## Confusion Matrix

```python
cm = confusion_matrix(y_test, y_pred)

TN, FP, FN, TP = cm.ravel()

specificity = TN / (TN + FP)
```

---

# 9. RANDOM FOREST

```python
model = RandomForestClassifier(
    n_estimators=51,
    criterion='entropy',
    random_state=42
)

model.fit(x_train, y_train)

y_pred = model.predict(x_test)
```

## Confusion Matrix

```python
cm = confusion_matrix(y_test, y_pred)

TN, FP, FN, TP = cm.ravel()

specificity = TN / (TN + FP)
```

---

# 10. SUPPORT VECTOR MACHINE (SVM)

```python
model = SVC(
    kernel='rbf',
    C=1,
    random_state=42
)

model.fit(x_train, y_train)

y_pred = model.predict(x_test)
```

## Confusion Matrix

```python
cm = confusion_matrix(y_test, y_pred)

TN, FP, FN, TP = cm.ravel()

specificity = TN / (TN + FP)
```

---

# 11. MODEL EVALUATION

## Regression Models (Linear / Multiple / Polynomial)

```python
print("R2 Score:", r2_score(y_test, y_pred))
print("MSE:", mean_squared_error(y_test, y_pred))
print("MAE:", mean_absolute_error(y_test, y_pred))
```

---

## Classification Models (KNN / Decision Tree / Random Forest / SVM)

```python
accuracy = accuracy_score(y_test, y_pred)

print("Accuracy:", accuracy)
print("Specificity:", specificity)
print("Confusion Matrix:\n", cm)
```

---

# 12. NEW DATA PREDICTION

```python
new_data = [[2,120,70,20,80,25,0.5,30]]
```

## Linear Regression

```python
prediction = model.predict(new_data)
```

---

## Polynomial Regression

```python
prediction = model.predict(poly.transform(new_data))
```

---

## KNN / Decision Tree / Random Forest / SVM

```python
prediction = model.predict(new_data)
```

---

## Display Prediction

```python
print("Prediction:", prediction)

# For classification models:
# print("Prediction:", prediction[0])
```

---

# QUICK REFERENCE

| Model | Important Parameters |
|--------|----------------------|
| Linear Regression | `LinearRegression()` |
| Polynomial | `PolynomialFeatures(degree=2)` |
| KNN | `n_neighbors=3` |
| Decision Tree | `criterion='entropy'`, `max_depth=None` |
| Random Forest | `n_estimators=51`, `criterion='entropy'` |
| SVM | `kernel='rbf'`, `C=1` |

---

# COMMON METRICS

### Regression
- R² Score
- Mean Squared Error (MSE)
- Mean Absolute Error (MAE)

### Classification
- Accuracy
- Specificity
- Confusion Matrix
