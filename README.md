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

- Public website bằng Cloudflare Tunnel
   > - Cài cloudflared: wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c18dd863-1ee9-4222-a19d-ca1708f00c3a" />
- rồi: sudo dpkg -i cloudflared-linux-amd64.deb
- Sau đó kiểm tra: cloudflared --version
<img width="1041" height="257" alt="image" src="https://github.com/user-attachments/assets/b70db69c-4bba-424c-a74b-5721f3c78d21" />

- login Cloudflare Tunnel : cloudflared tunnel login
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b6b57ea1-70b5-45ae-a38e-00f89f0af08e" />

- Copy link này: https://dash.cloudflare.com/argotunnel?...
- rồi: Mở browser -> Dán link vào -> Đăng nhập Cloudflare nếu được yêu cầu -> Chọn domain: -> hoangthixuantrang.id.vn  Bấm:Authorize
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/ef84d4d6-71d5-456c-8068-d58ed138929a" />
<img width="862" height="395" alt="image" src="https://github.com/user-attachments/assets/35098862-3d82-45f6-b31d-bf147e7ff6a2" />

- quay lại terminal Ubuntu và làm bước tiếp theo.

  > - Chạy: cloudflared tunnel create wordpress-tunnel
  <img width="1220" height="140" alt="image" src="https://github.com/user-attachments/assets/105ea8c7-c740-4b04-8a6c-399fbad1cf6c" />

- Tạo file config: nano ~/.cloudflared/config.yml
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a2b6511d-f363-4277-a3f7-23badc8c3f2e" />

- Tạo DNS route: cloudflared tunnel route dns wordpress-tunnel wp.hoangthixuantrang.id.vn
<img width="1348" height="77" alt="image" src="https://github.com/user-attachments/assets/e8240cb0-e5a0-4981-a3a1-f62ba8082d0c" />

- vào Wordpress -> cài đặt -> tổng quan và sửa URL
<img width="690" height="815" alt="image" src="https://github.com/user-attachments/assets/d3cefaab-da54-42ea-8c25-035eb1616e47" />

- Chạy tunnel: cloudflared tunnel run wordpress-tunnel sau đó truy cập https://wp.hoangthixuantrang.id.vn
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5ff53529-73b6-4a43-8ac4-6a271e6969e3" />

- Bây giờ làm nội dung bài tập
   > - Đăng nhập admin
      > - Mở:https://wp.hoangthixuantrang.id.vn/wp-admin
- Tạo bài viết gồm  thông tin cá nhân, sở thích, ... bài viết có thể chứa hình ảnh, âm thanh, video, ...
- - sau khi tạo bài viết xong: 
<img width="1179" height="2556" alt="image" src="https://github.com/user-attachments/assets/07693b00-0a49-40d4-a45a-f4fd502c2cdf" />
<img width="1179" height="2556" alt="image" src="https://github.com/user-attachments/assets/7f848afd-2ca5-47a3-a7e2-17b81feb3d8b" />
<img width="1179" height="2556" alt="image" src="https://github.com/user-attachments/assets/b92fd85d-bacb-41df-bcba-4594ebd11bbc" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f4ba87aa-9fe2-473c-b99f-2b5ebdab86f6" />

-  Tạo 1 bài viết trong wordpress giới thiệu về ngành học mà em yêu thích trong trường TNUT. bài viết phải chứa hình ảnh, video, ...
-  sau khi tạo bài viết xong:
<img width="1179" height="2556" alt="image" src="https://github.com/user-attachments/assets/02b9198c-f95b-4ca7-b9cf-ab833b5ff70a" />
<img width="1179" height="2556" alt="image" src="https://github.com/user-attachments/assets/cabf073e-8fea-4388-82e2-fd1db9154626" />
<img width="1179" height="2556" alt="image" src="https://github.com/user-attachments/assets/ce9cc083-53c1-4596-be1e-c0fc24ed90be" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/01ce5cc6-b244-4fd5-853c-a736cec544b8" />


- Nhận xét việc sử dụng mã nguồn mở wordpress để tạo website (tốn công sức thế nào, dễ/khó dùng ra sao, tốn kém tài nguyên(ssh/ram) của máy chủ ra sao,....)
  # Nhận xét về việc sử dụng WordPress để tạo website

- WordPress là một hệ quản trị nội dung mã nguồn mở phổ biến và dễ sử dụng để xây dựng website. Trong quá trình thực hiện bài tập, em nhận thấy WordPress có nhiều ưu điểm nổi bật như giao diện quản trị trực quan, dễ thao tác và không yêu cầu phải biết quá nhiều về lập trình.

- Việc triển khai WordPress bằng Docker giúp cài đặt nhanh chóng, dễ quản lý và thuận tiện khi cấu hình các dịch vụ như MariaDB và phpMyAdmin. Chỉ cần sử dụng file `docker-compose.yml` là có thể khởi động toàn bộ hệ thống website.

- Ngoài ra, WordPress hỗ trợ rất nhiều giao diện và plugin miễn phí, giúp người dùng dễ dàng tạo website cá nhân, blog hoặc website doanh nghiệp. Việc tạo bài viết, chèn hình ảnh, video hay chỉnh sửa giao diện đều khá đơn giản.

- Tuy nhiên, WordPress cũng có một số nhược điểm như sử dụng khá nhiều tài nguyên RAM khi chạy đồng thời với MariaDB, phpMyAdmin và các plugin mở rộng. Nếu cài đặt nhiều plugin hoặc theme nặng thì website có thể hoạt động chậm hơn và tiêu tốn thêm tài nguyên máy chủ.

- Trong quá trình thực hành, em cũng gặp một số khó khăn khi cấu hình Docker và Cloudflare Tunnel để public website lên Internet. Tuy nhiên sau khi hoàn thành, em hiểu rõ hơn về cách triển khai website bằng công nghệ mã nguồn mở trên môi trường Linux.

=> Nhìn chung, WordPress là một nền tảng mạnh, dễ sử dụng và phù hợp cho cả người mới bắt đầu lẫn những người phát triển website chuyên nghiệp.

