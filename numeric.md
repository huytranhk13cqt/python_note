Dưới đây là tổng hợp các phương thức và hàm xử lý số trong Python:

### 1. Hàm Số Học Cơ Bản (Built-in Functions)

```python
# Chuyển đổi kiểu số
int("123")           # 123 (string to int)
float("123.45")      # 123.45 (string to float)
complex(1, 2)        # (1+2j) (tạo số phức)

# Làm tròn
round(3.14159, 2)    # 3.14 (làm tròn 2 chữ số thập phân)
abs(-5)              # 5 (giá trị tuyệt đối)
pow(2, 3)           # 8 (2^3)
divmod(7, 3)        # (2, 1) (thương và dư)
```

### 2. Module Math (import math)

```python
import math

# Hằng số
print(math.pi)       # 3.141592653589793
print(math.e)        # 2.718281828459045
print(math.inf)      # Dương vô cùng
print(math.nan)      # Not a Number

# Làm tròn
print(math.ceil(3.1))        # 4 (làm tròn lên)
print(math.floor(3.9))       # 3 (làm tròn xuống)
print(math.trunc(3.9))       # 3 (cắt phần thập phân)

# Lũy thừa và logarit
print(math.pow(2, 3))        # 8.0 (2^3)
print(math.sqrt(16))         # 4.0 (căn bậc 2)
print(math.exp(1))           # 2.718281828459045 (e^1)
print(math.log(math.e))      # 1.0 (ln)
print(math.log10(100))       # 2.0 (log cơ số 10)
print(math.log2(8))          # 3.0 (log cơ số 2)

# Lượng giác (radians)
print(math.sin(math.pi/2))   # 1.0
print(math.cos(math.pi))     # -1.0
print(math.tan(math.pi/4))   # ~1.0
print(math.asin(1))          # 1.5707963267948966 (arcsin)
print(math.degrees(math.pi))  # 180.0 (rad to deg)
print(math.radians(180))     # 3.141592653589793 (deg to rad)

# Hyperbolic
print(math.sinh(1))          # sinh
print(math.cosh(1))          # cosh
print(math.tanh(1))          # tanh

# Các hàm đặc biệt
print(math.factorial(5))     # 120 (giai thừa)
print(math.gcd(12, 8))       # 4 (ước chung lớn nhất)
print(math.fsum([0.1, 0.2, 0.3])) # Tổng chính xác
```

### 3. Module Random (import random)

```python
import random

# Số ngẫu nhiên
print(random.random())           # [0.0, 1.0)
print(random.uniform(1, 10))     # [1, 10]
print(random.randint(1, 10))     # [1, 10]
print(random.randrange(0, 101, 2))  # Số chẵn 0-100

# Lựa chọn ngẫu nhiên
my_list = [1, 2, 3, 4, 5]
print(random.choice(my_list))    # Chọn 1 phần tử
print(random.sample(my_list, 3)) # Chọn k phần tử
random.shuffle(my_list)          # Xáo trộn list
```

### 4. Module Decimal (Số Thập Phân Chính Xác)

```python
from decimal import Decimal, getcontext

# Đặt độ chính xác
getcontext().prec = 4

# Tính toán chính xác
d1 = Decimal('0.1')
d2 = Decimal('0.2')
print(d1 + d2)              # 0.3000
print(Decimal('1.23456').quantize(Decimal('0.01')))  # 1.23
```

### 5. Module Fractions (Phân số)

```python
from fractions import Fraction

# Tạo phân số
f1 = Fraction(1, 3)         # 1/3
f2 = Fraction('1.25')       # 5/4
print(f1 + f2)              # 19/12
```

### 6. Module Statistics (Thống kê)

```python
import statistics

numbers = [1, 2, 3, 4, 5, 5, 6, 6, 7]

print(statistics.mean(numbers))      # Trung bình
print(statistics.median(numbers))    # Trung vị
print(statistics.mode(numbers))      # Mode
print(statistics.stdev(numbers))     # Độ lệch chuẩn
print(statistics.variance(numbers))  # Phương sai
```

### 7. Toán Tử Số Học

```python
# Các toán tử cơ bản
print(5 + 3)    # 8 (cộng)
print(5 - 3)    # 2 (trừ)
print(5 * 3)    # 15 (nhân)
print(5 / 3)    # 1.6666666666666667 (chia)
print(5 // 3)   # 1 (chia lấy phần nguyên)
print(5 % 3)    # 2 (chia lấy dư)
print(5 ** 3)   # 125 (lũy thừa)

# Toán tử gán kết hợp
x = 5
x += 3      # x = x + 3
x -= 3      # x = x - 3
x *= 3      # x = x * 3
x /= 3      # x = x / 3
x //= 3     # x = x // 3
x %= 3      # x = x % 3
x **= 3     # x = x ** 3
```

### 8. Kiểm Tra Số

```python
# Kiểm tra kiểu số
print(isinstance(5, int))           # True
print(isinstance(5.0, float))       # True
print(isinstance(1+2j, complex))    # True

# Kiểm tra tính chất
print(math.isfinite(5))            # True
print(math.isinf(math.inf))        # True
print(math.isnan(math.nan))        # True
```

### Lưu ý quan trọng:

1. Python có độ chính xác hữu hạn với số thực (float)
2. Dùng Decimal cho tính toán tài chính/chính xác
3. Complex numbers hỗ trợ sẵn trong Python
4. Random không thích hợp cho mục đích bảo mật
5. Math functions thường trả về float, ngay cả với input integer
6. Một số hàm có thể raise exceptions (như sqrt với số âm)
