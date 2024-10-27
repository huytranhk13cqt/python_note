Dưới đây là các phương thức phổ biến nhất của List trong Python:

### 1. Thêm phần tử

```python
my_list = [1, 2, 3]

# Thêm một phần tử vào cuối
my_list.append(4)           # [1, 2, 3, 4]

# Thêm nhiều phần tử vào cuối
my_list.extend([5, 6])      # [1, 2, 3, 4, 5, 6]

# Chèn phần tử vào vị trí cụ thể
my_list.insert(0, 0)        # [0, 1, 2, 3, 4, 5, 6]
```

### 2. Xóa phần tử

```python
my_list = [1, 2, 2, 3, 4, 5]

# Xóa phần tử theo giá trị (phần tử đầu tiên tìm thấy)
my_list.remove(2)           # [1, 2, 3, 4, 5]

# Xóa và trả về phần tử ở vị trí index
popped = my_list.pop()      # Xóa phần tử cuối
popped = my_list.pop(0)     # Xóa phần tử ở index 0

# Xóa tất cả phần tử
my_list.clear()             # []

# Xóa theo index hoặc slice
del my_list[0]              # Xóa phần tử đầu tiên
del my_list[1:3]            # Xóa phần tử từ index 1 đến 2
```

### 3. Tìm kiếm và đếm

```python
my_list = [1, 2, 2, 3, 4, 2]

# Đếm số lần xuất hiện
count = my_list.count(2)    # 3

# Tìm vị trí đầu tiên của phần tử
index = my_list.index(2)    # 1
# Tìm trong khoảng cụ thể
index = my_list.index(2, 2, 5)  # Tìm số 2 từ index 2 đến 4
```

### 4. Sắp xếp

```python
my_list = [3, 1, 4, 1, 5, 9]

# Sắp xếp tại chỗ
my_list.sort()              # [1, 1, 3, 4, 5, 9]
my_list.sort(reverse=True)  # [9, 5, 4, 3, 1, 1]

# Sắp xếp với key function
words = ['banana', 'apple', 'cherry']
words.sort(key=len)         # Sắp xếp theo độ dài
words.sort(key=str.lower)   # Sắp xếp không phân biệt hoa thường

# Đảo ngược list
my_list.reverse()
```

### 5. Copy list

```python
# Shallow copy
list1 = [1, 2, [3, 4]]
list2 = list1.copy()        # hoặc list2 = list1[:]

# Deep copy
from copy import deepcopy
list3 = deepcopy(list1)
```

### 6. List Comprehension

```python
# Tạo list mới với điều kiện
numbers = [1, 2, 3, 4, 5]
squares = [x**2 for x in numbers]              # [1, 4, 9, 16, 25]
evens = [x for x in numbers if x % 2 == 0]     # [2, 4]

# Nested list comprehension
matrix = [[1, 2, 3], [4, 5, 6]]
flattened = [x for row in matrix for x in row] # [1, 2, 3, 4, 5, 6]
```

### 7. Các phương thức kiểm tra

```python
my_list = [1, 2, 3]

# Kiểm tra phần tử có trong list
2 in my_list               # True
5 in my_list               # False

# Độ dài list
len(my_list)               # 3

# Giá trị lớn nhất, nhỏ nhất
max(my_list)               # 3
min(my_list)               # 1
```

### 8. Slicing (Cắt list)

```python
my_list = [0, 1, 2, 3, 4, 5]

# Lấy phần tử từ index
print(my_list[1:4])        # [1, 2, 3]
print(my_list[::2])        # [0, 2, 4] (bước nhảy 2)
print(my_list[::-1])       # [5, 4, 3, 2, 1, 0] (đảo ngược)
```

### 9. List làm việc với vòng lặp

```python
my_list = ['a', 'b', 'c']

# Enumerate để lấy cả index và giá trị
for index, value in enumerate(my_list):
    print(f"Index {index}: {value}")

# Zip để kết hợp nhiều list
list1 = [1, 2, 3]
list2 = ['a', 'b', 'c']
for num, letter in zip(list1, list2):
    print(f"{num}-{letter}")
```

### Lưu ý quan trọng:

1. Lists trong Python là mutable (có thể thay đổi).
2. Phương thức `sort()` sắp xếp tại chỗ, trong khi hàm `sorted()` trả về list mới.
3. List comprehension thường nhanh hơn vòng lặp for thông thường.
4. Shallow copy chỉ copy tham chiếu của các object bên trong, trong khi deep copy tạo bản sao hoàn toàn mới.
5. Slicing tạo ra một list mới.
6. Các phương thức như `append()`, `extend()`, `sort()`, `reverse()` thay đổi list gốc và trả về None.
