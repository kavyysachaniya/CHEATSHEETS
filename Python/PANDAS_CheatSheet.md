# PANDAS CHEATSHEET

> **Universal Pandas Template**
>
> Covers:
> - Series
> - DataFrame
> - Indexing
> - Selection
> - Filtering
> - Missing Values
> - Duplicates
> - Sorting
> - Statistics
> - Correlation
> - Apply
> - Replace
> - Concat
> - Merge
> - GroupBy
> - Pivot Table
> - File Handling
> - Visualization

---

# 1. IMPORT LIBRARIES

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from pandas.plotting import parallel_coordinates
```

---

# 2. CREATE SERIES

```python
pd.Series([10,20,30])
pd.Series([100,200,300], index=['A','B','C'])
pd.Series({'A':100,'B':200,'C':300})
pd.Series(np.array([1,2,3]))
pd.Series(range(1,6))
```

---

# 3. CREATE DATAFRAME

```python
pd.DataFrame(data)
pd.DataFrame(data, columns=['Name','Age'])
pd.read_csv('data.csv')
pd.read_excel('data.xlsx')
pd.read_json('data.json')
pd.DataFrame()
```

---

# 4. INDEXING

```python
df.set_index('ID')
df.set_index('ID', drop=False)
df.set_index('ID', inplace=True)
df.reset_index()
```

**Parameters**

- keys → Column name
- drop → Remove old column
- inplace → Modify original DataFrame

---

# 5. DATAFRAME ATTRIBUTES

```python
df.shape
df.size
df.ndim
df.columns
df.index
df.dtypes
df.values
```

---

# 6. SELECTION

```python
df.loc[101]
df.loc[101:103]
df.loc[101,'Marks']
df.iloc[0]
df.iloc[0:2]
df.iloc[0,1]
```

- loc → Label based
- iloc → Position based

---

# 7. FILTERING

```python
df[df['Marks']>80]
df[(df['Marks']>80) & (df['Age']>20)]
df[(df['Marks']>80) | (df['Age']>20)]
df[~(df['Dept']=='IT')]
df[df['Marks'].between(80,95)]
df[df['Dept'].isin(['IT','HR'])]
```

Operators

- & → AND
- | → OR
- ~ → NOT

---

# 8. DISPLAY DATA

```python
df.head()
df.head(10)
df.tail()
df.sample()
```

---

# 9. INFORMATION

```python
df.info()
df.describe()
df.describe(include='all')
```

---

# 10. UNIQUE VALUES

```python
df['Dept'].unique()
df['Dept'].nunique()
df['Dept'].value_counts()
```

---

# 11. MISSING VALUES

```python
df.isnull()
df.isnull().sum()
df.fillna(0)
df.fillna(method='ffill')
df.dropna()
df.dropna(subset=['Marks'])
```

---

# 12. DROP

```python
df.drop(index=0)
df.drop(columns=['Marks'])
df.drop(labels='Dept', axis=1)
```

---

# 13. DUPLICATES

```python
df.duplicated()
df.duplicated(subset=['Name'])
df.drop_duplicates()
df.drop_duplicates(keep='last')
```

---

# 14. OUTLIER (IQR)

```python
Q1=df['Marks'].quantile(0.25)
Q3=df['Marks'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
df=df[(df['Marks']>=lower)&(df['Marks']<=upper)]
```

---

# 15. SORTING

```python
df.sort_values(by='Marks')
df.sort_values(by=['Dept','Marks'])
df.sort_values(by=['Dept','Marks'], ascending=[True,False])
df.sort_index()
```

---

# 16. STATISTICS

```python
df.sum()
df.mean()
df.max()
df.min()
df.mode()
df.median()
df.count()
df.quantile(0.25)
df.quantile([0.25,0.5,0.75])
df.corr(numeric_only=True)
```

---

# 17. APPLY

```python
df.apply(sum)
df.apply(np.mean)
df.apply(lambda x:x*2)
```

---

# 18. DATA TYPE

```python
df.astype(float)
df.astype({'Marks':'float'})
```

---

# 19. REPLACE

```python
df.replace(90,100)
df.replace({'A':'X'})
df['Name'].replace('C','M')
```

---

# 20. CONCAT

```python
pd.concat([df1,df2])
pd.concat([df1,df2], axis=1)
pd.concat([df1,df2], join='inner')
pd.concat([df1,df2], ignore_index=True)
```

---

# 21. MERGE

```python
pd.merge(df1,df2,on='ID')
pd.merge(df1,df2,how='left')
pd.merge(df1,df2,how='right')
pd.merge(df1,df2,how='inner')
pd.merge(df1,df2,how='outer')
```

---

# 22. GROUPBY

```python
df.groupby('Dept').sum()
df.groupby('Dept').mean()
df.groupby('Dept').count()
df.groupby('Dept')['Marks'].max()
```

---

# 23. PIVOT TABLE

```python
pd.pivot_table(df,index='Dept',values='Marks')
pd.pivot_table(df,index='Dept',values='Marks',aggfunc='mean')
```

---

# 24. CROSSTAB

```python
pd.crosstab(df['Dept'],df['Gender'])
pd.crosstab(df['Dept'],df['Gender'],margins=True)
```

---

# 25. FILE HANDLING

```python
pd.read_csv('data.csv')
pd.read_excel('data.xlsx')
pd.read_json('data.json')
df.to_csv('output.csv')
df.to_excel('output.xlsx')
```

---
# 26. VISUALIZATION

## Scatter Matrix

```python
pd.plotting.scatter_matrix(df, alpha=0.7, figsize=(6,6))
plt.show()
```

**Parameters**

- frame → DataFrame
- alpha → Transparency (0–1)
- figsize → Figure size

---

## Parallel Coordinates

```python
parallel_coordinates(df, class_column='Dept', cols=None, color=['red','blue'])
plt.show()
```

**Parameters**

- frame → DataFrame
- class_column → Category column
- cols → Columns to plot
- color → Line colors

---

## DataFrame Plot

```python
df.plot(kind='line')
df.plot(kind='bar')
df.plot(kind='hist')
df.plot(kind='scatter', x='Age', y='Marks')
```

**Common Parameters**

- kind → line, bar, hist, scatter, pie, box
- x → X-axis column
- y → Y-axis column
- figsize → Figure size
- color → Plot color
- title → Graph title
- grid → Show grid (True/False)
- legend → Show legend (True/False)

---

# QUICK REFERENCE

| Task | Function |
|------|----------|
| Create Series | `pd.Series()` |
| Create DataFrame | `pd.DataFrame()` |
| Read CSV | `pd.read_csv()` |
| Read Excel | `pd.read_excel()` |
| Index | `set_index()` |
| Reset Index | `reset_index()` |
| Select | `loc`, `iloc` |
| Filter | `&`, `|`, `~` |
| Missing Values | `isnull()`, `fillna()`, `dropna()` |
| Duplicates | `duplicated()`, `drop_duplicates()` |
| Sorting | `sort_values()`, `sort_index()` |
| Statistics | `sum()`, `mean()`, `median()`, `mode()` |
| Correlation | `corr()` |
| Apply | `apply()` |
| Replace | `replace()` |
| Merge | `merge()` |
| Concat | `concat()` |
| Group | `groupby()` |
| Pivot | `pivot_table()` |
| Crosstab | `crosstab()` |

---

# MOST USED METHODS

```python
shape
size
columns
index
dtypes
values
head()
tail()
sample()
info()
describe()
unique()
nunique()
value_counts()
isnull()
fillna()
dropna()
drop()
duplicated()
drop_duplicates()
sort_values()
sort_index()
sum()
mean()
max()
min()
mode()
median()
count()
quantile()
corr()
apply()
astype()
replace()
concat()
merge()
groupby()
pivot_table()
crosstab()
```
