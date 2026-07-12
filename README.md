
# ElectroShop - Hướng dẫn cài đặt và chạy dự án Laravel trên XAMPP

## 1. Yêu cầu hệ thống

- Windows
- XAMPP (Apache + MySQL)
- PHP 8.2 trở lên
- Laravel 10
- Visual Studio Code
- Trình duyệt (Chrome, Edge,...)

> Lưu ý: Nếu dự án đã có thư mục `vendor` thì không cần cài Composer để chạy.

---

# 2. Giải nén dự án

Giải nén file:

```
electroshop.rar
```

Copy thư mục dự án vào:

```
C:\xampp\htdocs\
```

Sau khi giải nén, cấu trúc sẽ như sau (tùy theo thư mục nén):

```
C:\xampp\htdocs\
└── electroshop
    └── electroshop
        └── electroshop
            ├── app
            ├── bootstrap
            ├── config
            ├── database
            ├── public
            ├── resources
            ├── routes
            ├── storage
            ├── vendor
            ├── artisan
            ├── composer.json
            ├── .env
            └── ecletroshop.sql
```

Thư mục gốc của Laravel là nơi có file:

```
artisan
```

---

# 3. Mở dự án bằng VS Code

Mở đúng thư mục Laravel:

```
C:\xampp\htdocs\electroshop\electroshop\electroshop
```

Kiểm tra bằng Terminal:

```bash
dir
```

Phải thấy:

```
artisan
composer.json
vendor
routes
storage
public
...
```

---

# 4. Khởi động XAMPP

Mở XAMPP Control Panel.

Khởi động:

- Apache
- MySQL

Nếu MySQL sử dụng cổng khác mặc định (ví dụ 3307) thì cần chỉnh lại file `.env`.

---

# 5. Tạo Database

Mở trình duyệt:

```
http://localhost/phpmyadmin
```

Chọn:

```
New
```

Tạo database:

```
ecletroshop
```

---

# 6. Import Database

Chọn database:

```
ecletroshop
```

Chọn tab:

```
Import
```

Chọn file:

```
ecletroshop.sql
```

trong thư mục dự án.

Sau đó nhấn:

```
Import
```

Nếu thành công sẽ xuất hiện thông báo màu xanh.

---

# 7. Cấu hình file .env

Mở file:

```
.env
```

Sửa cấu hình database:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3307
DB_DATABASE=ecletroshop
DB_USERNAME=root
DB_PASSWORD=
```

> Lưu ý:

Nếu MySQL của XAMPP chạy ở cổng mặc định thì dùng:

```env
DB_PORT=3306
```

Nếu MySQL chạy ở:

```
3307
```

thì phải sửa:

```env
DB_PORT=3307
```

Có thể kiểm tra cổng MySQL trong XAMPP Control Panel.

---

# 8. Xóa cache cấu hình

Mở Terminal tại thư mục dự án:

```bash
php artisan optimize:clear
```

---

# 9. Chạy dự án

Chạy:

```bash
php artisan serve
```

Nếu thành công sẽ xuất hiện:

```
INFO  Server running on [http://127.0.0.1:8000]
```

Mở trình duyệt:

```
http://127.0.0.1:8000
```

---

# 10. Kiểm tra phiên bản

Kiểm tra PHP:

```bash
php -v
```

Kiểm tra Laravel:

```bash
php artisan --version
```

---

# 11. Một số lỗi thường gặp

## Lỗi

```
SQLSTATE[HY000] [1045]
Access denied for user 'root'@'localhost'
```

### Nguyên nhân

Sai cấu hình Database trong file `.env`.

### Cách khắc phục

Kiểm tra:

```env
DB_HOST
DB_PORT
DB_DATABASE
DB_USERNAME
DB_PASSWORD
```

Đặc biệt:

```
DB_PORT
```

phải đúng với cổng MySQL của XAMPP.

Sau đó chạy:

```bash
php artisan optimize:clear
```

và chạy lại:

```bash
php artisan serve
```

---

## Lỗi

```
Unknown database 'ecletroshop'
```

### Nguyên nhân

Chưa tạo hoặc chưa import database.

### Cách khắc phục

- Tạo database:

```
ecletroshop
```

- Import file:

```
ecletroshop.sql
```

---

## Lỗi

```
composer is not recognized
```

### Nguyên nhân

Chưa cài Composer.

### Khắc phục

Tải Composer:

https://getcomposer.org/download/

---

# 12. Dừng Server

Trong Terminal:

```
Ctrl + C
```

---

# 13. Thông tin dự án

Framework:

- Laravel 10.37.3

PHP:

- 8.2.12

Database:

- MariaDB / MySQL

Web Server:

- Apache (XAMPP)

---

# 14. Quy trình chạy nhanh

```text
Giải nén project
        │
        ▼
Copy vào htdocs
        │
        ▼
Mở VS Code
        │
        ▼
Start Apache + MySQL
        │
        ▼
Tạo database ecletroshop
        │
        ▼
Import ecletroshop.sql
        │
        ▼
Chỉnh file .env
(DB_PORT đúng với MySQL)
        │
        ▼
php artisan optimize:clear
        │
        ▼
php artisan serve
        │
        ▼
Mở http://127.0.0.1:8000
```

---

# 15. Ghi chú

- Đảm bảo thư mục `vendor` đã tồn tại.
- Nếu thiếu thư mục `vendor`, cài Composer và chạy:

```bash
composer install
```

- Nếu thay đổi cấu hình `.env`, luôn chạy:

```bash
php artisan optimize:clear
```

để Laravel cập nhật cấu hình mới.
