# Scikit-Learn Cheatsheet

## Basic Pattern

```python
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
model = RandomForestClassifier(n_estimators=100, random_state=42)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
print(f"Accuracy: {accuracy_score(y_test, y_pred):.4f}")
```

## Preprocessing

```python
from sklearn.preprocessing import StandardScaler, MinMaxScaler, LabelEncoder, OneHotEncoder
from sklearn.impute import SimpleImputer

# Scaling
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)  # Use transform, NOT fit_transform!

# Imputation
imputer = SimpleImputer(strategy="median")
X_imputed = imputer.fit_transform(X)

# Encoding
le = LabelEncoder()
y_encoded = le.fit_transform(y)
```

## Pipelines

```python
from sklearn.pipeline import Pipeline
from sklearn.compose import ColumnTransformer

num_pipe = Pipeline([("imputer", SimpleImputer()), ("scaler", StandardScaler())])
cat_pipe = Pipeline([("imputer", SimpleImputer(strategy="most_frequent")),
                     ("encoder", OneHotEncoder(handle_unknown="ignore"))])

preprocessor = ColumnTransformer([
    ("num", num_pipe, num_cols),
    ("cat", cat_pipe, cat_cols),
])

full_pipeline = Pipeline([
    ("preprocess", preprocessor),
    ("model", RandomForestClassifier()),
])

full_pipeline.fit(X_train, y_train)
```

## Model Selection

```python
from sklearn.model_selection import GridSearchCV, RandomizedSearchCV

param_grid = {"n_estimators": [50, 100, 200], "max_depth": [5, 10, None]}
grid = GridSearchCV(RandomForestClassifier(), param_grid, cv=5, scoring="f1")
grid.fit(X_train, y_train)
print(f"Best params: {grid.best_params_}")
print(f"Best score: {grid.best_score_:.4f}")
```

## Common Models Quick Reference

| Model | Import |
|-------|--------|
| Logistic Regression | `from sklearn.linear_model import LogisticRegression` |
| Random Forest | `from sklearn.ensemble import RandomForestClassifier` |
| Gradient Boosting | `from sklearn.ensemble import GradientBoostingClassifier` |
| SVM | `from sklearn.svm import SVC` |
| KNN | `from sklearn.neighbors import KNeighborsClassifier` |
| Decision Tree | `from sklearn.tree import DecisionTreeClassifier` |
| Linear Regression | `from sklearn.linear_model import LinearRegression` |
| Ridge / Lasso | `from sklearn.linear_model import Ridge, Lasso` |
| K-Means | `from sklearn.cluster import KMeans` |
| PCA | `from sklearn.decomposition import PCA` |
