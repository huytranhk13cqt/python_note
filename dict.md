Dưới đây là tổng hợp các phương thức và thao tác với Dictionary trong Python:

### 1. Khởi Tạo Dictionary

```python
# Các cách tạo dictionary
dict1 = {}                          # Dictionary rỗng
dict2 = dict()                      # Dictionary rỗng
dict3 = {'a': 1, 'b': 2}           # Trực tiếp
dict4 = dict(a=1, b=2)             # Sử dụng dict()
dict5 = dict([('a', 1), ('b', 2)]) # Từ list of tuples
dict6 = dict.fromkeys(['a', 'b'], 0) # Tạo dict với giá trị mặc định
```

### 2. Truy Cập và Thêm/Sửa Phần Tử

```python
d = {'a': 1, 'b': 2, 'c': 3}

# Truy cập phần tử
print(d['a'])                # 1 (raises KeyError nếu key không tồn tại)
print(d.get('a'))           # 1
print(d.get('x', 0))        # 0 (giá trị mặc định nếu key không tồn tại)

# Thêm/Sửa phần tử
d['d'] = 4                  # Thêm phần tử mới
d['a'] = 10                 # Cập nhật giá trị
d.update({'e': 5, 'f': 6})  # Thêm nhiều phần tử
d.update(g=7, h=8)          # Thêm bằng keyword arguments
```

### 3. Xóa Phần Tử

```python
d = {'a': 1, 'b': 2, 'c': 3, 'd': 4}

# Xóa phần tử
del d['a']                  # Xóa phần tử (raises KeyError nếu không tồn tại)
value = d.pop('b')          # Xóa và trả về giá trị
value = d.pop('x', None)    # Xóa với giá trị mặc định nếu key không tồn tại
last = d.popitem()          # Xóa và trả về cặp (key, value) cuối cùng

# Xóa tất cả
d.clear()                   # Xóa tất cả phần tử
```

### 4. Kiểm Tra Tồn Tại

```python
d = {'a': 1, 'b': 2, 'c': 3}

# Kiểm tra key
print('a' in d)             # True
print('x' in d)             # False
print('x' not in d)         # True

# Kiểm tra value
print(1 in d.values())      # True
```

### 5. Lấy Views của Dictionary

```python
d = {'a': 1, 'b': 2, 'c': 3}

# Lấy các view
keys = d.keys()             # dict_keys(['a', 'b', 'c'])
values = d.values()         # dict_values([1, 2, 3])
items = d.items()           # dict_items([('a', 1), ('b', 2), ('c', 3)])

# Views tự động cập nhật khi dict thay đổi
d['d'] = 4
print(keys)                 # dict_keys(['a', 'b', 'c', 'd'])
```

### 6. Copy Dictionary

```python
d = {'a': 1, 'b': {'x': 10}}

# Shallow copy
d1 = d.copy()              # Hoặc dict(d)

# Deep copy
import copy
d2 = copy.deepcopy(d)
```

### 7. Dictionary Comprehension

```python
# Tạo dict mới với điều kiện
squares = {x: x**2 for x in range(5)}
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# Lọc dict
even_squares = {x: x**2 for x in range(5) if x % 2 == 0}
# {0: 0, 2: 4, 4: 16}
```

### 8. Merge Dictionaries

```python
d1 = {'a': 1, 'b': 2}
d2 = {'c': 3, 'd': 4}

# Python 3.5+
merged1 = {**d1, **d2}

# Python 3.9+
merged2 = d1 | d2

# Truyền thống
merged3 = d1.copy()
merged3.update(d2)
```

### 9. Phương Thức Đặc Biệt

```python
d = {'a': 1, 'b': 2}

# setdefault: lấy giá trị hoặc thêm mới nếu không tồn tại
value = d.setdefault('c', 3)    # Thêm 'c': 3 nếu 'c' không tồn tại

# Lấy giá trị mặc định cho key không tồn tại
from collections import defaultdict
dd = defaultdict(int)            # Giá trị mặc định là 0
dd['new_key'] += 1               # Tự động tạo key với giá trị 0
```

### 10. Sắp Xếp Dictionary

```python
d = {'b': 2, 'a': 1, 'c': 3}

# Sắp xếp theo key
sorted_by_key = dict(sorted(d.items()))

# Sắp xếp theo value
sorted_by_value = dict(sorted(d.items(), key=lambda x: x[1]))

# Sắp xếp phức tạp hơn
from operator import itemgetter
sorted_dict = dict(sorted(d.items(), key=itemgetter(1), reverse=True))
```

### 11. Các Phương Thức Tiện Ích

```python
# Đếm tần suất
from collections import Counter
counter = Counter(['a', 'b', 'a', 'c', 'b', 'a'])
# Counter({'a': 3, 'b': 2, 'c': 1})

# OrderedDict (giữ thứ tự thêm vào - Python 3.7+ dict mặc định có thứ tự)
from collections import OrderedDict
od = OrderedDict([('a', 1), ('b', 2)])
```

### Lưu ý quan trọng:

1. Dictionary là mutable (có thể thay đổi)
2. Keys phải là immutable (không thể thay đổi)
3. Từ Python 3.7+, dict giữ thứ tự thêm vào
4. Views (keys(), values(), items()) là dynamic
5. copy() tạo shallow copy
6. Nên dùng get() thay vì truy cập trực tiếp để tránh KeyError
7. Dictionary comprehension thường nhanh hơn vòng lặp for
8. defaultdict và Counter rất hữu ích cho nhiều use cases
