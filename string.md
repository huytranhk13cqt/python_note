Dưới đây là các phương thức phổ biến nhất của String trong Python:

### 1. Các phương thức chuyển đổi chuỗi

```python
text = "Hello Python"

# Chuyển đổi chữ hoa/thường
print(text.upper())      # HELLO PYTHON
print(text.lower())      # hello python
print(text.title())      # Hello Python
print(text.capitalize()) # Hello python
print(text.swapcase())   # hELLO pYTHON
```

### 2. Các phương thức kiểm tra chuỗi

```python
text = "Hello123"

# Kiểm tra loại ký tự
print(text.isalpha())    # False (vì có số)
print(text.isdigit())    # False (vì có chữ)
print(text.isalnum())    # True (vì có cả chữ và số)
print(text.isupper())    # False
print(text.islower())    # False
print(text.isspace())    # False
print("  ".isspace())    # True
```

### 3. Các phương thức tìm kiếm và thay thế

```python
text = "Hello Python Python"

# Tìm kiếm
print(text.find("Python"))      # 6 (vị trí đầu tiên)
print(text.rfind("Python"))     # 13 (vị trí cuối cùng)
print(text.index("Python"))     # 6 (giống find nhưng raise error nếu không tìm thấy)
print(text.count("Python"))     # 2 (số lần xuất hiện)

# Thay thế
print(text.replace("Python", "World"))  # Hello World World
print(text.replace("Python", "World", 1))  # Hello World Python
```

### 4. Các phương thức cắt và nối chuỗi

```python
text = "  Hello World  "

# Cắt khoảng trắng
print(text.strip())      # "Hello World"
print(text.lstrip())     # "Hello World  "
print(text.rstrip())     # "  Hello World"

# Tách chuỗi
text = "Python,Java,C++"
print(text.split(","))   # ['Python', 'Java', 'C++']

# Nối chuỗi
words = ['Python', 'Java', 'C++']
print(",".join(words))   # Python,Java,C++
```

### 5. Các phương thức định dạng

```python
# format()
name = "Alice"
age = 25
print("Name: {}, Age: {}".format(name, age))
print("Name: {0}, Age: {1}".format(name, age))
print("Age: {age}, Name: {name}".format(name=name, age=age))

# f-strings (Python 3.6+)
print(f"Name: {name}, Age: {age}")

# Căn lề
text = "Python"
print(text.ljust(10, '*'))   # Python****
print(text.rjust(10, '*'))   # ****Python
print(text.center(10, '*'))  # **Python**
```

### 6. Các phương thức kiểm tra tiền tố/hậu tố

```python
text = "Hello World"

# Kiểm tra bắt đầu/kết thúc
print(text.startswith("Hello"))  # True
print(text.endswith("World"))    # True

# Có thể chỉ định vị trí bắt đầu, kết thúc
print(text.startswith("World", 6))  # True
```

### 7. Các phương thức mã hóa

```python
text = "Python"

# Mã hóa
print(text.encode())         # b'Python'
print(text.encode('utf-8'))  # b'Python'

# Giải mã
encoded = text.encode()
print(encoded.decode())      # Python
```

### 8. Các phương thức điền/thay thế

```python
# zfill - thêm số 0 vào đầu
num = "42"
print(num.zfill(5))     # 00042

# expandtabs - điều chỉnh kích thước tab
text = "Python\tJava"
print(text.expandtabs(4))  # Python  Java
```

### Lưu ý quan trọng:

1. Strings trong Python là immutable (không thể thay đổi). Các phương thức luôn trả về chuỗi mới.
2. Phương thức `find()` trả về -1 nếu không tìm thấy, trong khi `index()` sẽ raise ValueError.
3. Từ Python 3.6+, f-strings là cách được khuyến nghị để định dạng chuỗi.
4. Nhiều phương thức có thể nhận các tham số tùy chọn như start và end để chỉ định phạm vi hoạt động.
