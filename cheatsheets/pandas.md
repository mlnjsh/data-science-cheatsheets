# Pandas Cheatsheet

## Creating DataFrames

```python
import pandas as pd

df = pd.DataFrame({"name": ["A","B"], "val": [1, 2]})
df = pd.read_csv("file.csv")
df = pd.read_excel("file.xlsx")
df = pd.read_json("file.json")
```

## Inspection

```python
df.head(10)           # First 10 rows
df.tail(5)            # Last 5 rows
df.shape              # (rows, cols)
df.dtypes             # Column types
df.describe()         # Stats summary
df.info()             # Memory + types
df.columns            # Column names
df.nunique()          # Unique counts
df.isnull().sum()     # Missing values per column
```

## Selection

```python
df["col"]             # Single column (Series)
df[["col1", "col2"]]  # Multiple columns (DataFrame)
df.loc[0:5, "col"]    # By label
df.iloc[0:5, 0:3]     # By position
df.query("col > 5")   # SQL-like filter
df[df["col"] > 5]     # Boolean filter
```

## Groupby

```python
df.groupby("category")["value"].mean()
df.groupby("category").agg({"value": ["mean", "std", "count"]})
df.groupby(["cat1", "cat2"]).size()
```

## Merge / Join

```python
pd.merge(df1, df2, on="key")                     # Inner join
pd.merge(df1, df2, on="key", how="left")          # Left join
pd.merge(df1, df2, left_on="id", right_on="key")  # Different column names
pd.concat([df1, df2], axis=0)                      # Stack vertically
pd.concat([df1, df2], axis=1)                      # Stack horizontally
```

## Common Operations

```python
df.sort_values("col", ascending=False)
df.drop_duplicates(subset=["col"])
df.rename(columns={"old": "new"})
df.fillna(0)
df.dropna(subset=["col"])
df["new"] = df["a"] + df["b"]
df["col"].apply(lambda x: x * 2)
df["col"].map({"A": 1, "B": 2})
df.pivot_table(values="val", index="row", columns="col", aggfunc="mean")
```

## Time Series

```python
df["date"] = pd.to_datetime(df["date"])
df.set_index("date", inplace=True)
df.resample("M").mean()              # Monthly average
df["col"].rolling(window=7).mean()    # 7-day rolling average
df["col"].shift(1)                    # Lag by 1
df["col"].pct_change()               # Percent change
```

## I/O

```python
df.to_csv("out.csv", index=False)
df.to_parquet("out.parquet")
df.to_json("out.json", orient="records")
df.to_excel("out.xlsx", index=False)
```
