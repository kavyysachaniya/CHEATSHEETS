# CHEATSHEET FOR OFFLINE WEB SCRAPING

> **Universal Offline Web Scraping Template**  
> Covers:
> - Opening Local HTML Files
> - BeautifulSoup
> - `find()` & `find_all()`
> - Extracting Text
> - Extracting Attributes
> - Handling Missing Values
> - Creating DataFrames
> - Saving Data

---

# 1. IMPORT LIBRARIES

```python
from bs4 import BeautifulSoup
import pandas as pd
import numpy as np
```

---

# 2. OPEN HTML FILE

```python
file = open("filename.html", encoding="utf-8")
response = file.read()
```

---

# 3. CREATE BEAUTIFULSOUP OBJECT

```python
soup = BeautifulSoup(response, "html.parser")
```

---

# 4. CREATE EMPTY LISTS

```python
column1 = []
column2 = []
column3 = []
column4 = []
column5 = []
column6 = []
```

---

# 5. FIND MAIN CONTAINER

## Multiple Elements

```python
data = soup.find_all("tag_name", class_="class_name")
```

---

## Single Element

```python
data = soup.find("tag_name",class_="class_name")
```

---

# 6. EXTRACT DATA

```python
for i in data:
    column1.append(i.find("tag_name",class_="class_name").text.strip())
    column2.append(i.find("tag_name",class_="class_name").text.strip())
    column3.append(i.find("tag_name",class_="class_name").text.strip())
```

---

## Extract Multiple Elements

```python
column4.append(i.find_all("tag_name",class_="class_name")[0].text.strip())
```

---

## Extract Attribute

```python
column5.append(i.find("tag_name")["href"])
```

---

## Split Text

```python
column6.append(i.find("tag_name").text.strip().split()[0])
```

---

# 7. HANDLE MISSING VALUES (OPTIONAL)

```python
try:
    column.append(i.find("tag_name",class_="class_name").text.strip())
except:
    column.append(np.nan)
```

---

# 8. CREATE DATAFRAME

```python
df = pd.DataFrame({
    "Column 1": column1,
    "Column 2": column2,
    "Column 3": column3,
    "Column 4": column4,
    "Column 5": column5,
    "Column 6": column6
})
```

---

# 9. DISPLAY DATA

```python
print(df)
```

---

# 10. SAVE DATA

## Save as CSV

```python
df.to_csv("output.csv", index=False)
```

---

## Save as Excel

```python
df.to_excel("output.xlsx", index=False)
```

---

# QUICK REFERENCE

| Task | Function |
|------|----------|
| Open HTML File | `open()` |
| Read File | `.read()` |
| Create Parser | `BeautifulSoup(html, "html.parser")` |
| Find First Element | `find()` |
| Find Multiple Elements | `find_all()` |
| Extract Text | `.text.strip()` |
| Extract Attribute | `["href"]`, `["src"]`, `["title"]` |
| Split Text | `.split()` |
| Handle Missing Values | `try-except` |
| Create DataFrame | `pd.DataFrame()` |
| Save CSV | `to_csv()` |
| Save Excel | `to_excel()` |

---

# COMMON METHODS

### BeautifulSoup
- `find()`
- `find_all()`

### Text Processing
- `.text`
- `.strip()`
- `.split()`

### Attributes
- `["href"]`
- `["src"]`
- `["alt"]`
- `["title"]`

### Pandas
- `pd.DataFrame()`
- `print(df)`
- `to_csv()`
- `to_excel()`
