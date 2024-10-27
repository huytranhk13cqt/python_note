Dưới đây là các phương thức và hàm phổ biến trong NumPy Array (Python):

### 1. Tạo Array

```python
import numpy as np

# Tạo array từ list
arr = np.array([1, 2, 3])
arr_2d = np.array([[1, 2], [3, 4]])

# Tạo array đặc biệt
zeros = np.zeros((3, 3))          # Array toàn số 0
ones = np.ones((2, 2))            # Array toàn số 1
empty = np.empty((2, 3))          # Array không khởi tạo
identity = np.eye(3)              # Ma trận đơn vị
arange = np.arange(0, 10, 2)      # Array từ 0 đến 9, bước 2
linspace = np.linspace(0, 1, 5)   # 5 số cách đều từ 0 đến 1
```

### 2. Thông tin về Array

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])

# Thuộc tính cơ bản
print(arr.shape)      # Kích thước array (2, 3)
print(arr.ndim)       # Số chiều
print(arr.size)       # Tổng số phần tử
print(arr.dtype)      # Kiểu dữ liệu
print(arr.itemsize)   # Kích thước (bytes) của mỗi phần tử
```

### 3. Thao tác với Array

```python
# Reshape array
arr = np.array([1, 2, 3, 4, 5, 6])
reshaped = arr.reshape(2, 3)      # Đổi thành array 2x3

# Transpose (đảo chiều)
transposed = arr.T

# Flatten (làm phẳng array nhiều chiều)
flattened = arr.flatten()         # Copy mới
ravel = arr.ravel()               # View của array gốc

# Stack arrays
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
vertical = np.vstack((a, b))      # Stack theo chiều dọc
horizontal = np.hstack((a, b))    # Stack theo chiều ngang
```

### 4. Toán tử và Phép tính

```python
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])

# Phép tính cơ bản
print(arr1 + arr2)    # Cộng từng phần tử
print(arr1 * arr2)    # Nhân từng phần tử
print(arr1 / arr2)    # Chia từng phần tử
print(arr1 ** 2)      # Bình phương từng phần tử

# Hàm toán học
print(np.sqrt(arr1))  # Căn bậc hai
print(np.exp(arr1))   # e mũ x
print(np.log(arr1))   # Logarit tự nhiên
print(np.sin(arr1))   # Sin
```

### 5. Thống kê

```python
arr = np.array([1, 2, 3, 4, 5])

# Các hàm thống kê cơ bản
print(np.mean(arr))       # Trung bình
print(np.median(arr))     # Trung vị
print(np.std(arr))        # Độ lệch chuẩn
print(np.var(arr))        # Phương sai
print(np.min(arr))        # Giá trị nhỏ nhất
print(np.max(arr))        # Giá trị lớn nhất
print(np.sum(arr))        # Tổng
print(np.prod(arr))       # Tích
```

### 6. Lọc và Tìm kiếm

```python
arr = np.array([1, 2, 3, 4, 5])

# Lọc điều kiện
mask = arr > 2
filtered = arr[mask]      # [3, 4, 5]

# Tìm kiếm
indices = np.where(arr > 2)   # Trả về indices thỏa điều kiện
nonzero = np.nonzero(arr)     # Trả về indices của phần tử khác 0
```

### 7. Sắp xếp và Unique

```python
arr = np.array([3, 1, 4, 1, 5, 9, 2])

# Sắp xếp
sorted_arr = np.sort(arr)         # Trả về array mới đã sắp xếp
arr.sort()                        # Sắp xếp tại chỗ

# Tìm giá trị unique
unique = np.unique(arr)           # Trả về array các giá trị duy nhất
```

### 8. Random

```python
# Tạo số ngẫu nhiên
random = np.random.rand(3, 3)         # Array ngẫu nhiên [0,1]
randint = np.random.randint(0, 10, 5) # 5 số nguyên ngẫu nhiên từ 0-9
normal = np.random.normal(0, 1, 1000) # Phân phối chuẩn

# Xáo trộn array
arr = np.array([1, 2, 3, 4, 5])
np.random.shuffle(arr)                # Xáo trộn tại chỗ
```

### 9. Linear Algebra

```python
# Đại số tuyến tính
a = np.array([[1, 2], [3, 4]])
b = np.array([[5, 6], [7, 8]])

dot = np.dot(a, b)           # Nhân ma trận
det = np.linalg.det(a)       # Định thức
inv = np.linalg.inv(a)       # Ma trận nghịch đảo
eig = np.linalg.eig(a)       # Trị riêng và vector riêng
```

### Lưu ý quan trọng:

1. NumPy arrays hiệu quả hơn Python lists về mặt bộ nhớ và tốc độ tính toán
2. Các phép tính được thực hiện trên từng phần tử (vectorization)
3. Broadcasting cho phép thực hiện phép tính giữa arrays khác kích thước
4. View vs Copy: một số thao tác tạo ra view (tham chiếu), một số tạo ra copy mới
5. NumPy hỗ trợ nhiều kiểu dữ liệu số học khác nhau (int32, float64, etc.)
