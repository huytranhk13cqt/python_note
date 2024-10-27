Dưới đây là tổng hợp các trường hợp slicing trong NumPy Array:

### 1. Slicing Cơ bản 1D Array

```python
import numpy as np
arr = np.array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])

# Cú pháp cơ bản: array[start:stop:step]
print(arr[2:7])      # [2 3 4 5 6]        # Từ index 2 đến 6
print(arr[::2])      # [0 2 4 6 8]        # Mỗi 2 phần tử
print(arr[1::2])     # [1 3 5 7 9]        # Bắt đầu từ 1, mỗi 2 phần tử

# Lấy từ đầu hoặc đến cuối
print(arr[:5])       # [0 1 2 3 4]        # 5 phần tử đầu
print(arr[5:])       # [5 6 7 8 9]        # Từ index 5 đến hết

# Đảo ngược
print(arr[::-1])     # [9 8 7 6 5 4 3 2 1 0]  # Đảo ngược toàn bộ
print(arr[::-2])     # [9 7 5 3 1]            # Đảo ngược, mỗi 2 phần tử
```

### 2. Slicing 2D Array (Matrix)

```python
arr_2d = np.array([
    [0,  1,  2,  3],
    [4,  5,  6,  7],
    [8,  9, 10, 11],
    [12, 13, 14, 15]
])

# Lấy hàng và cột
print(arr_2d[1:3])           # Lấy hàng 1 và 2
print(arr_2d[:, 1:3])        # Lấy cột 1 và 2
print(arr_2d[1:3, 1:3])      # Lấy submatrix 2x2

# Lấy các hàng/cột cách đều
print(arr_2d[::2, ::2])      # Lấy hàng và cột cách 2

# Đảo ngược
print(arr_2d[::-1])          # Đảo ngược các hàng
print(arr_2d[:, ::-1])       # Đảo ngược các cột
print(arr_2d[::-1, ::-1])    # Đảo ngược cả hàng và cột
```

### 3. Slicing Nâng cao

```python
# Lấy đường chéo chính
diag = np.diag(arr_2d)

# Lấy tam giác trên/dưới
triu = np.triu(arr_2d)    # Upper triangular
tril = np.tril(arr_2d)    # Lower triangular

# Lấy các góc của matrix
top_left = arr_2d[0:2, 0:2]
top_right = arr_2d[0:2, -2:]
bottom_left = arr_2d[-2:, 0:2]
bottom_right = arr_2d[-2:, -2:]
```

### 4. Slicing với Boolean Indexing

```python
# Lọc theo điều kiện
mask = arr_2d > 7
print(arr_2d[mask])           # Lấy các phần tử > 7

# Kết hợp nhiều điều kiện
condition = (arr_2d > 3) & (arr_2d < 8)
print(arr_2d[condition])
```

### 5. Fancy Indexing

```python
# Lấy các phần tử theo index cụ thể
indices = [0, 2, 3]
print(arr_2d[indices])        # Lấy hàng 0, 2, 3

# Lấy các phần tử theo cặp tọa độ
rows = [0, 1, 2]
cols = [1, 2, 3]
print(arr_2d[rows, cols])     # Lấy (0,1), (1,2), (2,3)
```

### 6. Slicing 3D Array

```python
arr_3d = np.array([
    [[0, 1], [2, 3]],
    [[4, 5], [6, 7]],
    [[8, 9], [10, 11]]
])

# Lấy theo chiều
print(arr_3d[1:])            # Từ matrix thứ 2
print(arr_3d[:, 1:])         # Từ hàng thứ 2 của mỗi matrix
print(arr_3d[:, :, 1:])      # Cột thứ 2 của mỗi matrix

# Lấy specific elements
print(arr_3d[1, 1, 1])       # Phần tử cụ thể
```

### 7. Các Trường Hợp Đặc Biệt

```python
# Sử dụng Ellipsis (...)
print(arr_3d[..., 0])        # Tương đương arr_3d[:, :, 0]

# Sử dụng newaxis
expanded = arr[:, np.newaxis]  # Thêm chiều mới

# Stride tricks
from numpy.lib.stride_tricks import as_strided
# Tạo sliding windows
```

### 8. Tips và Lưu ý

```python
# Copy vs View
slice1 = arr_2d[1:3]         # View (tham chiếu)
slice2 = arr_2d[1:3].copy()  # Copy (bản sao độc lập)

# Gán giá trị cho slice
arr_2d[0:2, 0:2] = 99       # Gán giá trị cho một phần của array

# Kiểm tra memory sharing
np.may_share_memory(slice1, arr_2d)  # True cho view
```

### Lưu ý quan trọng:

1. Slicing trong NumPy trả về view (không copy dữ liệu) trừ khi dùng `.copy()`
2. Có thể dùng số âm để đếm từ cuối array
3. Step có thể là số âm để đảo ngược
4. Boolean indexing luôn tạo copy
5. Fancy indexing luôn tạo copy
6. Cẩn thận với memory usage khi làm việc với large arrays
