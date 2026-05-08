# phat_trien_ung_dung_voi_ma_nguon_mo_3
# Môn: Phát triển ứng dụng với mã nguồn mở-TEE0421

Lớp: 58KTPM

**Bài tập 03:**  

# SỬ DỤNG WORDPRESS ĐỂ TẠO WEB SITE
## deadline : 23h59 ngày 12 tháng 5 năm 2026.
   
1. SỬ DỤNG DOCKER TRÊN UBUNTU ĐỂ TẠO docker compose chứa: 
- Mariadb: sử dụng **image: mariadb:latest** để làm hệ quản trị csdl cho wordpress
- Phpmyadmin: sư dụng **image: phpmyadmin:latest** để đăng nhập vào mariadb rồi tạo csdl trống (chỉ để xem, ko cần tạo bảng từ đây, wordpress sẽ làm hết)
- WordPress: Sử dụng **image: wordpress:latest**, truyền các tham số môi trường cho wordpress là các thông tin truy cập csdl mariadb, tạo bởi Phpmyadmin

2. Yêu cầu: sau khi có 3 service này trong file docker-compose.yml :
- Cấu hình để hệ thống chạy
- Sử dụng cloudflare tunnel để public web này lên 1 sub-domain
- Tạo 1 bài viết trong wordpress giới thiệu về bản thân sinh viên: thông tin cá nhân, sở thích, ... bài viết có thể chứa hình ảnh, âm thanh, video, ...
- Tạo 1 bài viết trong wordpress giới thiệu về ngành học mà em yêu thích trong trường TNUT. bài viết phải chứa hình ảnh, video, ...
- Nhận xét việc sử dụng mã nguồn mở wordpress để tạo website (tốn công sức thế nào, dễ/khó dùng ra sao, tốn kém tài nguyên(ssh/ram) của máy chủ ra sao,....)

## BÀI LÀM
# 1. SỬ DỤNG DOCKER TRÊN UBUNTU ĐỂ TẠO docker compose chứa: 
- Mariadb: sử dụng **image: mariadb:latest** để làm hệ quản trị csdl cho wordpress
- Phpmyadmin: sư dụng **image: phpmyadmin:latest** để đăng nhập vào mariadb rồi tạo csdl trống (chỉ để xem, ko cần tạo bảng từ đây, wordpress sẽ làm hết)
- WordPress: Sử dụng **image: wordpress:latest**, truyền các tham số môi trường cho wordpress là các thông tin truy cập csdl mariadb, tạo bởi Phpmyadmin

- khởi động docker
   > - sudo systemctl enable docker
   > - sudo systemctl start docker
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1390ca42-1d2c-426e-9158-2bf0310c50b3" />
- Tạo thư mục project WordPress
   > - mkdir wordpress-lab
   > - cd wordpress-lab
<img width="1197" height="292" alt="image" src="https://github.com/user-attachments/assets/c3f2fe9d-0e5b-4f9f-8d9c-160ff7621390" />

- Tạo file: nano docker-compose.yml
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bab464c9-03d2-4500-a119-7af63a0ec029" />

- Chạy Docker Compose: sudo docker compose up -d
- <img width="888" height="137" alt="image" src="https://github.com/user-attachments/assets/c15b4f10-fa5f-4f2f-8559-3bda3fac9a79" />
- Kiểm tra container: sudo docker ps
<img width="1633" height="491" alt="image" src="https://github.com/user-attachments/assets/74353d43-1a2c-44b3-bad0-8b4af7afb728" />

- Truy cập WordPress
   > - Mở: http://IP_Ubuntu:8080
      > - Tiến hành:
   >    -    Chọn ngôn ngữ
   >     -    Tạo tài khoản admin
   >      -    Đặt tên website
<img width="748" height="888" alt="image" src="https://github.com/user-attachments/assets/6abc84b5-5c13-438a-9b85-cb53a2b1761c" />
<img width="1727" height="1007" alt="image" src="https://github.com/user-attachments/assets/a83beaf0-71b9-48e1-9ba3-50d40d7f00d3" />

- phpMyAdmin
   > - Mở: http://IP_Ubuntu:8081
<img width="1648" height="836" alt="image" src="https://github.com/user-attachments/assets/a44a0314-6921-414a-993e-945248db1ae6" />
