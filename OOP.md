Dưới đây là tổng hợp đầy đủ về OOP trong Python:

### 1. Tính Đóng Gói (Encapsulation)

```python
class BankAccount:
    def __init__(self, owner, balance=0):
        self.__owner = owner      # Private attribute
        self.__balance = balance  # Private attribute
        self._branch = "Main"     # Protected attribute

    # Getter methods
    @property
    def balance(self):
        return self.__balance

    @property
    def owner(self):
        return self.__owner

    # Setter method
    @balance.setter
    def balance(self, amount):
        if amount >= 0:
            self.__balance = amount
        else:
            raise ValueError("Balance cannot be negative")

    # Public methods
    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            return True
        return False

    def withdraw(self, amount):
        if 0 < amount <= self.__balance:
            self.__balance -= amount
            return True
        return False

# Sử dụng
account = BankAccount("John Doe", 1000)
print(account.balance)        # Truy cập qua property
account.balance = 2000        # Sử dụng setter
# print(account.__balance)    # Error: không thể truy cập trực tiếp
```

### 2. Tính Kế Thừa (Inheritance)

```python
# Single Inheritance
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        return f"{self.name} says Woof!"

class Cat(Animal):
    def speak(self):
        return f"{self.name} says Meow!"

# Multiple Inheritance
class Flying:
    def fly(self):
        return "I can fly!"

class Swimming:
    def swim(self):
        return "I can swim!"

class Duck(Animal, Flying, Swimming):
    def speak(self):
        return f"{self.name} says Quack!"

# Method Resolution Order (MRO)
print(Duck.__mro__)  # Hiển thị thứ tự tìm kiếm method

# Super()
class Bird(Animal):
    def __init__(self, name, wingspan):
        super().__init__(name)
        self.wingspan = wingspan
```

### 3. Tính Đa Hình (Polymorphism)

```python
# Method Overriding
class Shape:
    def area(self):
        pass

    def perimeter(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def perimeter(self):
        return 2 * (self.width + self.height)

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius ** 2

    def perimeter(self):
        return 2 * 3.14 * self.radius

# Duck Typing
def calculate_area(shape):
    return shape.area()

# Operator Overloading
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)

    def __str__(self):
        return f"Vector({self.x}, {self.y})"
```

### 4. Tính Trừu Tượng (Abstraction)

```python
from abc import ABC, abstractmethod

class Database(ABC):
    @abstractmethod
    def connect(self):
        pass

    @abstractmethod
    def disconnect(self):
        pass

    @abstractmethod
    def execute(self, query):
        pass

class MySQLDatabase(Database):
    def connect(self):
        return "Connected to MySQL"

    def disconnect(self):
        return "Disconnected from MySQL"

    def execute(self, query):
        return f"Executing query in MySQL: {query}"

class PostgreSQLDatabase(Database):
    def connect(self):
        return "Connected to PostgreSQL"

    def disconnect(self):
        return "Disconnected from PostgreSQL"

    def execute(self, query):
        return f"Executing query in PostgreSQL: {query}"
```

### 5. Composition và Aggregation

```python
# Composition (strong relationship)
class Engine:
    def start(self):
        return "Engine started"

    def stop(self):
        return "Engine stopped"

class Car:
    def __init__(self):
        self.engine = Engine()  # Composition

    def start(self):
        return self.engine.start()

    def stop(self):
        return self.engine.stop()

# Aggregation (weak relationship)
class Student:
    def __init__(self, name):
        self.name = name

class Course:
    def __init__(self, name, students=None):
        self.name = name
        self.students = students or []

    def add_student(self, student):
        self.students.append(student)
```

### 6. Static và Class Methods

```python
class MathOperations:
    pi = 3.14  # Class variable

    def __init__(self):
        self.result = 0  # Instance variable

    @staticmethod
    def add(x, y):
        return x + y

    @classmethod
    def circle_area(cls, radius):
        return cls.pi * radius ** 2

    @property
    def get_result(self):
        return self.result
```

### 7. Magic Methods (Dunder Methods)

```python
class Book:
    def __init__(self, title, author, pages):
        self.title = title
        self.author = author
        self.pages = pages

    def __str__(self):
        return f"{self.title} by {self.author}"

    def __len__(self):
        return self.pages

    def __eq__(self, other):
        return self.title == other.title and self.author == other.author

    def __lt__(self, other):
        return self.pages < other.pages
```

### 8. Properties và Descriptors

```python
class Temperature:
    def __init__(self):
        self._celsius = 0

    @property
    def celsius(self):
        return self._celsius

    @celsius.setter
    def celsius(self, value):
        if value < -273.15:
            raise ValueError("Temperature below absolute zero!")
        self._celsius = value

    @property
    def fahrenheit(self):
        return self._celsius * 9/5 + 32

    @fahrenheit.setter
    def fahrenheit(self, value):
        self.celsius = (value - 32) * 5/9
```

### 9. Context Managers

```python
class FileManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode
        self.file = None

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_val, exc_tb):
        if self.file:
            self.file.close()

# Usage
with FileManager('test.txt', 'w') as f:
    f.write('Hello, World!')
```

### Lưu ý quan trọng:

1. Python sử dụng name mangling cho private attributes (`__var`)
2. Multiple inheritance có thể phức tạp, cần hiểu rõ MRO
3. Duck typing là cách Python implement polymorphism
4. Abstract classes không thể instantiate
5. Properties giúp implement encapsulation tốt hơn
6. Static và class methods không cần instance
7. Magic methods customize behavior của objects
8. Context managers giúp quản lý resources
