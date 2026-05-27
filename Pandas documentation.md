
---

### ✅ Common / Important Parameters (Use 90% of the time)

| Parameter | What it does | Example |
|-----------|--------------|---------|
| `filepath` | File path (first argument) | `pd.read_csv('data.csv')` |
| `sep` | Delimiter (default is `,`) | `pd.read_csv('data.tsv', sep='\t')` |
| `header` | Which row is column names (default `0`) | `pd.read_csv('data.csv', header=None)` |
| `names` | Custom column names | `pd.read_csv('data.csv', names=['A','B'])` |
| `index_col` | Which column becomes row index | `pd.read_csv('data.csv', index_col=0)` |
| `usecols` | Load only specific columns | `pd.read_csv('data.csv', usecols=['date','price'])` |
| `dtype` | Specify data type for columns | `pd.read_csv('data.csv', dtype={'id': int})` |
| `parse_dates` | Convert column to datetime | `pd.read_csv('data.csv', parse_dates=['date'])` |
| `encoding` | File encoding (fix Unicode errors) | `pd.read_csv('data.csv', encoding='latin-1')` |
| `skiprows` | Skip first N rows | `pd.read_csv('data.csv', skiprows=2)` |

---

### ❌ Rare / Niche Parameters (Look up when needed)

| Parameter | What it does | When to use |
|-----------|--------------|-------------|
| `nrows` | Read only first N rows | Testing large files |
| `chunksize` | Read in chunks (returns iterator) | Files too big for memory |
| `na_values` | Custom missing value strings | `pd.read_csv('data.csv', na_values=['N/A','-'])` |
| `true_values` / `false_values` | Custom boolean values | `pd.read_csv('data.csv', true_values=['yes'])` |
| `thousands` | Thousands separator | `pd.read_csv('data.csv', thousands=',')` |
| `decimal` | Decimal point character | `pd.read_csv('data.csv', decimal=',')` |
| `comment` | Skip lines starting with character | `pd.read_csv('data.csv', comment='#')` |
| `on_bad_lines` | Handle error lines | `pd.read_csv('data.csv', on_bad_lines='skip')` |
| `engine` | 'c', 'python', or 'pyarrow' | Performance tuning |
| `skipfooter` | Skip last N rows | `pd.read_csv('data.csv', skipfooter=1)` |
| `compression` | Read compressed files | `pd.read_csv('data.csv.gz', compression='gzip')` |

---

## 🚀 Code Examples

---

| Parameter | What it does |
|-----------|--------------|
| `parse_dates=['col']` | Convert text dates to real date objects |
| `header=None +  names =['']` | CSV has no header row (data starts immediately) and set each column names|
| `index_col='col'` | Use a column as row labels instead of 0,1,2... |

---

### When to use 

| CSV has header row? | Use |
|---------------------|-----|
| ✅ Yes (first row has names) | `header=0` (default) |
| ❌ No (starts with data) | `header=None` |

---

### Fix Encoding Errors (UnicodeDecodeError)

```python
df = pd.read_csv('data.csv', encoding='latin-1')
# or
df = pd.read_csv('data.csv', encoding='ISO-8859-1')
```

---

### Read Large File in Chunks (Memory Efficient)

```python
chunk_list = []
for chunk in pd.read_csv('large_file.csv', chunksize=10000):
    chunk_list.append(chunk)
df = pd.concat(chunk_list)
```

---

### Skip Bad Lines (ParserError)

```python
df = pd.read_csv('messy_file.csv', on_bad_lines='skip')
```

---

### Complete Realistic Example (Crypto Data)

```python
df = pd.read_csv(
    'bitcoin_prices.csv',
    parse_dates=['Date'],
    index_col='Date',
    usecols=['Date', 'Open', 'High', 'Low', 'Close', 'Volume'],
    dtype={
        'Open': 'float32',
        'High': 'float32',
        'Low': 'float32',
        'Close': 'float32',
        'Volume': 'int64'
    },
    encoding='utf-8'
)
```

---

## 📋 Quick Reference Card

| You want to... | Use this |
|----------------|----------|
| Read a CSV | `pd.read_csv('file.csv')` |
| Read TSV | `pd.read_csv('file.tsv', sep='\t')` |
| Load only some columns | `usecols=['col1', 'col2']` |
| Set date column as index | `parse_dates=['date'], index_col='date'` |
| Fix encoding error | `encoding='latin-1'` |
| Handle missing file | Wrap in `try/except` |
| Read large file | `chunksize=10000` |
| Skip bad rows | `on_bad_lines='skip'` |

---
