Dưới đây là tổng hợp các function và method phổ biến trong Matplotlib:

### 1. Cơ Bản

```python
import matplotlib.pyplot as plt
import numpy as np

# Tạo figure và axes
fig, ax = plt.subplots(figsize=(10, 6))

# Plot cơ bản
x = np.linspace(0, 10, 100)
plt.plot(x, np.sin(x))
plt.show()

# Lưu plot
plt.savefig('plot.png', dpi=300, bbox_inches='tight')
```

### 2. Các Loại Plot Cơ Bản

```python
# Line plot
plt.plot(x, y, 'r--', label='line')

# Scatter plot
plt.scatter(x, y, c='blue', s=50, alpha=0.5)

# Bar plot
plt.bar(x, y, width=0.8, align='center')

# Histogram
plt.hist(data, bins=50, density=True)

# Pie chart
plt.pie(sizes, labels=labels, autopct='%1.1f%%')

# Box plot
plt.boxplot(data)

# Violin plot
plt.violinplot(data)

# Heatmap
plt.imshow(data, cmap='hot')
plt.colorbar()
```

### 3. Tùy Chỉnh Trục và Labels

```python
# Tiêu đề và labels
plt.title('Title', fontsize=14, pad=20)
plt.xlabel('X axis', fontsize=12)
plt.ylabel('Y axis', fontsize=12)

# Giới hạn trục
plt.xlim([0, 10])
plt.ylim([-1, 1])

# Ticks
plt.xticks([0, 2, 4, 6, 8, 10])
plt.yticks([-1, -0.5, 0, 0.5, 1])

# Rotation của ticks
plt.xticks(rotation=45)

# Grid
plt.grid(True, linestyle='--', alpha=0.7)
```

### 4. Multiple Subplots

```python
# Tạo nhiều subplots
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 5))
ax1.plot(x1, y1)
ax2.plot(x2, y2)

# Grid của subplots
fig, axes = plt.subplots(2, 3, figsize=(15, 10))
for i, ax in enumerate(axes.flat):
    ax.plot(data[i])

# Subplot với gridspec
from matplotlib.gridspec import GridSpec
gs = GridSpec(3, 3)
ax1 = plt.subplot(gs[0, :])
ax2 = plt.subplot(gs[1:, :-1])
ax3 = plt.subplot(gs[1:, -1])
```

### 5. Tùy Chỉnh Style

```python
# Line styles
plt.plot(x, y1, 'r--', linewidth=2)
plt.plot(x, y2, 'b-.', linewidth=1.5)
plt.plot(x, y3, 'g:', linewidth=1)

# Marker styles
plt.plot(x, y, 'o-', markersize=8, markerfacecolor='red')

# Fill between
plt.fill_between(x, y1, y2, alpha=0.3)

# Color maps
plt.scatter(x, y, c=colors, cmap='viridis')

# Style sheets
plt.style.use('seaborn')
plt.style.use('ggplot')
plt.style.use('dark_background')
```

### 6. Legend và Annotations

```python
# Legend
plt.plot(x, y1, label='Line 1')
plt.plot(x, y2, label='Line 2')
plt.legend(loc='best', fontsize=12)

# Text annotation
plt.annotate('Peak', xy=(2, 1), xytext=(3, 1.5),
            arrowprops=dict(facecolor='black', shrink=0.05))

# Text box
plt.text(0.5, 0.5, 'Text Box', bbox=dict(facecolor='white', alpha=0.5))
```

### 7. 3D Plots

```python
from mpl_toolkits.mplot3d import Axes3D

# 3D surface plot
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')
ax.plot_surface(X, Y, Z, cmap='viridis')

# 3D scatter plot
ax.scatter(xs, ys, zs)

# 3D wireframe
ax.plot_wireframe(X, Y, Z)
```

### 8. Statistical Plots

```python
# Error bars
plt.errorbar(x, y, yerr=yerr, fmt='o')

# Confidence intervals
plt.fill_between(x, y-std, y+std, alpha=0.2)

# Regression plot
from scipy import stats
slope, intercept, r_value, p_value, std_err = stats.linregress(x, y)
line = slope * x + intercept
plt.plot(x, line, 'r', label=f'R² = {r_value**2:.3f}')
```

### 9. Tùy Chỉnh Figure

```python
# Figure size và DPI
plt.figure(figsize=(10, 6), dpi=100)

# Margins và spacing
plt.margins(x=0.1, y=0.1)
plt.tight_layout()

# Subplot spacing
plt.subplots_adjust(wspace=0.3, hspace=0.3)

# Background color
plt.gca().set_facecolor('lightgray')
```

### 10. Interactive Features

```python
# Zoom và pan tools
from matplotlib.widgets import Slider, Button

# Slider
axslider = plt.axes([0.2, 0.02, 0.6, 0.03])
slider = Slider(axslider, 'Param', 0, 1, valinit=0.5)

# Button
axbutton = plt.axes([0.8, 0.02, 0.1, 0.03])
button = Button(axbutton, 'Reset')
```

### Lưu ý quan trọng:

1. Luôn gọi `plt.show()` để hiển thị plot
2. Sử dụng `plt.close()` để giải phóng bộ nhớ
3. Object-oriented interface (`ax.plot()`) thường linh hoạt hơn pyplot interface (`plt.plot()`)
4. Sử dụng `plt.style.use()` để áp dụng style nhất quán
5. `tight_layout()` giúp tự động điều chỉnh spacing
6. Sử dụng `figsize` để kiểm soát kích thước plot
7. Lưu ý về DPI khi lưu file
8. Sử dụng alpha để xử lý overlap
