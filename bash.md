Dưới đây là tổng hợp các lệnh Bash Script phổ biến cho automation:

### 1. Cấu trúc Cơ bản của Script

```bash
#!/bin/bash

# Khai báo các biến môi trường
export PATH="/usr/local/bin:$PATH"

# Khai báo biến
NAME="John"
AGE=25

# In ra màn hình
echo "Hello, $NAME"
echo "Your age is: $AGE"
```

### 2. Điều kiện và So sánh

```bash
#!/bin/bash

# If-else condition
if [ $AGE -gt 18 ]; then
    echo "You are an adult"
elif [ $AGE -eq 18 ]; then
    echo "You just turned 18"
else
    echo "You are under 18"
fi

# So sánh số
# -eq : bằng
# -ne : không bằng
# -gt : lớn hơn
# -ge : lớn hơn hoặc bằng
# -lt : nhỏ hơn
# -le : nhỏ hơn hoặc bằng

# So sánh chuỗi
if [ "$STRING1" = "$STRING2" ]; then
    echo "Strings are equal"
fi

# Kiểm tra file/thư mục
if [ -f "file.txt" ]; then
    echo "File exists"
fi
if [ -d "directory" ]; then
    echo "Directory exists"
fi
```

### 3. Vòng lặp

```bash
#!/bin/bash

# For loop
for i in {1..5}; do
    echo $i
done

# While loop
counter=1
while [ $counter -le 5 ]; do
    echo $counter
    ((counter++))
done

# Loop through files
for file in *.txt; do
    echo "Processing $file"
done

# Loop through lines in file
while read line; do
    echo $line
done < input.txt
```

### 4. Xử lý File và Thư mục

```bash
#!/bin/bash

# Tạo thư mục
mkdir -p folder/subfolder

# Copy files
cp source.txt destination.txt
cp -r source_dir destination_dir

# Di chuyển/đổi tên
mv old.txt new.txt

# Xóa
rm file.txt
rm -r directory
rm -rf directory  # Force delete

# Tạo file
touch newfile.txt

# Phân quyền
chmod 755 script.sh
chown user:group file.txt
```

### 5. Xử lý Text

```bash
#!/bin/bash

# Grep - tìm kiếm
grep "pattern" file.txt
grep -r "pattern" directory/
grep -i "pattern" file.txt  # Case insensitive

# Sed - thay thế text
sed 's/old/new/g' file.txt
sed -i 's/old/new/g' file.txt  # Thay đổi trực tiếp file

# Awk - xử lý text theo cột
awk '{print $1}' file.txt  # In cột đầu tiên
awk -F"," '{print $1}' file.csv  # Với file CSV
```

### 6. Network và System

```bash
#!/bin/bash

# Kiểm tra kết nối
ping -c 4 google.com

# Curl requests
curl -X GET "http://api.example.com"
curl -X POST -d "data" "http://api.example.com"

# System info
df -h  # Disk usage
free -m  # Memory usage
top -n 1  # Process info
```

### 7. Xử lý Process

```bash
#!/bin/bash

# Chạy process trong background
command &

# Kiểm tra process
ps aux | grep "process_name"

# Kill process
kill PID
killall process_name

# Đợi process hoàn thành
wait $PID
```

### 8. Logging và Error Handling

```bash
#!/bin/bash

# Redirect output
command > output.log 2>&1

# Append output
command >> output.log 2>&1

# Error handling
set -e  # Exit on error
trap 'echo Error at line $LINENO' ERR

# Custom logging
log() {
    echo "[$(date '+%Y-%m-%d %H:%M:%S')] $1" >> app.log
}
```

### 9. Arguments và Options

```bash
#!/bin/bash

# Lấy arguments
echo "First argument: $1"
echo "All arguments: $@"
echo "Number of arguments: $#"

# Getopts
while getopts "a:b:" opt; do
    case $opt in
        a) ARG_A="$OPTARG";;
        b) ARG_B="$OPTARG";;
        *) echo "Invalid option";;
    esac
done
```

### 10. Functions

```bash
#!/bin/bash

# Định nghĩa function
function_name() {
    echo "Argument 1: $1"
    return 0
}

# Gọi function
function_name "arg1"

# Function với return value
get_status() {
    if [ "$1" -eq 0 ]; then
        echo "Success"
    else
        echo "Failed"
    fi
}
```

### 11. Automation Tasks

```bash
#!/bin/bash

# Backup script
backup_dir="/backup"
source_dir="/data"

timestamp=$(date +%Y%m%d_%H%M%S)
backup_file="backup_$timestamp.tar.gz"

tar -czf "$backup_dir/$backup_file" "$source_dir"

# Cleanup old backups
find "$backup_dir" -name "backup_*.tar.gz" -mtime +7 -delete

# Cron job (thêm vào crontab)
# 0 2 * * * /path/to/backup.sh
```

### Lưu ý quan trọng:

1. Luôn thêm shebang (`#!/bin/bash`) ở đầu script
2. Đặt quyền thực thi cho script: `chmod +x script.sh`
3. Sử dụng `set -e` để dừng khi có lỗi
4. Test script trên môi trường nhỏ trước
5. Backup dữ liệu quan trọng trước khi chạy script
6. Comment code để dễ bảo trì
7. Sử dụng logging để debug
8. Xử lý lỗi một cách phù hợp
