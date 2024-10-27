Dưới đây là tổng hợp các function và method phổ biến trong Pandas:

### 1. Tạo DataFrame/Series

```python
import pandas as pd

# Tạo DataFrame
df = pd.DataFrame({
    'A': [1, 2, 3],
    'B': ['a', 'b', 'c']
})

# Từ dictionary
dict_df = pd.DataFrame.from_dict(data_dict)

# Từ file
csv_df = pd.read_csv('file.csv')
excel_df = pd.read_excel('file.xlsx')
json_df = pd.read_json('file.json')

# Tạo Series
series = pd.Series([1, 2, 3], index=['a', 'b', 'c'])
```

### 2. Xem Dữ Liệu

```python
# Thông tin cơ bản
df.head()                   # 5 hàng đầu
df.tail()                   # 5 hàng cuối
df.info()                   # Thông tin DataFrame
df.describe()               # Thống kê mô tả
df.shape                    # Kích thước
df.columns                  # Tên các cột
df.index                    # Index
df.dtypes                   # Kiểu dữ liệu

# Kiểm tra dữ liệu
df.isnull().sum()          # Đếm giá trị null
df.duplicated().sum()      # Đếm hàng trùng lặp
```

### 3. Lựa Chọn và Lọc Dữ Liệu

```python
# Lựa chọn cột
df['column']               # Một cột
df[['A', 'B']]            # Nhiều cột

# Lọc hàng
df.loc['index']           # Theo index label
df.iloc[0]                # Theo vị trí
df.loc[df['A'] > 2]       # Theo điều kiện
df.query('A > 2')         # Query string

# Boolean indexing
mask = df['A'] > 2
df[mask]

# Lấy giá trị
df.at['index', 'column']  # Label based
df.iat[0, 0]              # Integer based
```

### 4. Xử Lý Missing Data

```python
# Kiểm tra missing
df.isna()                 # Hoặc df.isnull()
df.notna()                # Hoặc df.notnull()

# Xử lý missing
df.fillna(0)              # Điền giá trị
df.dropna()               # Xóa hàng có NA
df.dropna(axis=1)         # Xóa cột có NA
df.interpolate()          # Nội suy

# Thay thế giá trị
df.replace(old_val, new_val)
```

### 5. Groupby và Aggregation

```python
# Groupby cơ bản
grouped = df.groupby('column')

# Các phép tính tổng hợp
grouped.mean()
grouped.sum()
grouped.count()
grouped.agg(['mean', 'sum'])

# Custom aggregation
grouped.agg({
    'A': 'sum',
    'B': 'mean'
})

# Transform
grouped.transform(lambda x: x - x.mean())
```

### 6. Merge và Join

```python
# Merge
pd.merge(df1, df2, on='key')
pd.merge(df1, df2, left_on='key1', right_on='key2')

# Join
df1.join(df2)
df1.join(df2, how='outer')

# Concat
pd.concat([df1, df2])             # Theo hàng
pd.concat([df1, df2], axis=1)     # Theo cột
```

### 7. Reshape và Pivot

```python
# Pivot
df.pivot(index='A', columns='B', values='C')
pd.pivot_table(df, values='D', index='A', columns='B')

# Melt
df.melt(id_vars=['A'], value_vars=['B', 'C'])

# Stack/Unstack
df.stack()
df.unstack()
```

### 8. Sắp Xếp

```python
# Sort
df.sort_values('column')
df.sort_values(['A', 'B'], ascending=[True, False])
df.sort_index()

# Rank
df.rank()
```

### 9. Thống Kê và Tính Toán

```python
# Thống kê cơ bản
df.mean()
df.median()
df.mode()
df.std()
df.var()
df.min()
df.max()
df.sum()

# Rolling statistics
df.rolling(window=3).mean()
df.expanding().mean()

# Correlation và covariance
df.corr()
df.cov()
```

### 10. Xử Lý String

```python
# String methods
df['column'].str.lower()
df['column'].str.upper()
df['column'].str.strip()
df['column'].str.contains('pattern')
df['column'].str.extract('(pattern)')
df['column'].str.split(',')
```

### 11. Time Series

```python
# Date/time handling
pd.to_datetime(df['date'])
df.resample('D').mean()
df.asfreq('D')
df.shift(periods=1)
df.rolling('7D').mean()
```

### 12. Input/Output

```python
# Đọc file
pd.read_csv('file.csv')
pd.read_excel('file.xlsx')
pd.read_sql('query', connection)

# Ghi file
df.to_csv('file.csv')
df.to_excel('file.xlsx')
df.to_sql('table', connection)
```

### 13. Apply và Map

```python
# Apply function
df.apply(func)
df['A'].map(lambda x: x*2)

# Applymap (element-wise)
df.applymap(func)
```

### 14. Xử Lý Duplicate

```python
# Kiểm tra và xử lý duplicate
df.duplicated()
df.drop_duplicates()
df.drop_duplicates(subset=['A', 'B'])
```

### Lưu ý quan trọng:

1. Sử dụng `.copy()` để tránh SettingWithCopyWarning
2. Chú ý đến inplace parameter trong các method
3. Vectorized operations nhanh hơn loops
4. Sử dụng categorical data type cho memory efficiency
5. Chú ý đến index khi merge/join
6. Sử dụng query() cho điều kiện phức tạp
7. Xử lý missing data trước khi phân tích
8. Sử dụng method chaining để code ngắn gọn hơn
