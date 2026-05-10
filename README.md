# Create_a_website_with_WORDPRESS

1. Tạo 1 thư mục **wordpress_docker** (tên tuỳ ý).   
<img width="530" height="98" alt="image" src="https://github.com/user-attachments/assets/f6b6492a-a1c7-466e-bd37-7118a6c8beb0" />   

2. Tạo file dockercompose.yml trong thư mục vừa tạo với lệnh *nano docker-compose.yml*  
<img width="775" height="53" alt="image" src="https://github.com/user-attachments/assets/9f365783-7dc9-4e38-b6b2-aebf04d3ab0f" />  
<img width="779" height="92" alt="Untitled" src="https://github.com/user-attachments/assets/ef07e031-898c-43e9-b939-e6160e491579" />  

- Nội dung cấu hình trong file **.yml**   
<img width="1475" height="753" alt="Untitled3" src="https://github.com/user-attachments/assets/f9620aa6-3ab0-42aa-8d4e-65c6f184d233" />

- Chạy lệnh *docker compose up -d* để cài đặt   
<img width="1476" height="687" alt="image" src="https://github.com/user-attachments/assets/048bbdd1-cfb1-49ea-9bac-f69714c72eb4" />

- Sau đó :   
   1. phpMyAdmin sẽ truy cập được tại: **http://localhost:8081**<br> Đăng nhập bằng tài khoản and mật khẩu đã thiết lập trong file docker-compose.yml
  <img width="1903" height="581" alt="image" src="https://github.com/user-attachments/assets/527153e0-8974-4ab0-ae44-f90bcc0983db" />
   2. WordPress sẽ chạy tại: **http://localhost:8080** sau khi mở link thiết lập ngôn ngữ **VI**or **ENG** tuỳ ý
  <img width="1893" height="964" alt="image" src="https://github.com/user-attachments/assets/91b6beba-7db3-483e-af70-e6303048b504" />

 - Thiết lập tài khoản+mật khẩu cho wordpress   
   <img width="678" height="688" alt="Untitled0" src="https://github.com/user-attachments/assets/7b24f05c-509d-4c35-ac55-30360b7ea234" />

- Sử dụng Cloudflare Tunnel để public trang web lên subdomain:  
  <img width="1908" height="976" alt="Untitled2" src="https://github.com/user-attachments/assets/f14ddb19-beb2-417f-9797-fa138d718690" />

- Thiết lập url cho web của bạn :  
  <img width="1919" height="1031" alt="Untitled1" src="https://github.com/user-attachments/assets/b5fb62e3-6e57-4702-ac80-5f05af47d126" />

- Để viết bài mới: Bạn chọn Posts (Bài viết) -> Add Posts (Thêm bài mới).  
<img width="1886" height="870" alt="image" src="https://github.com/user-attachments/assets/5e0a196e-a8ad-42a8-b383-2eb86edeaab0" />

1. Chào mọi người , mình là Nguyễn Thế Dương!
<img width="1910" height="961" alt="image" src="https://github.com/user-attachments/assets/62a86d23-6517-441a-abe0-264ebc6b793c" />

---

2.Kỹ thuật Phần mềm tại TNUT – Nơi biến ý tưởng thành dòng code
<img width="1906" height="969" alt="image" src="https://github.com/user-attachments/assets/992fca9e-0deb-401f-9458-095cf9ac47e2" />


# Nhận xét việc sử dụng WordPress mã nguồn mở trên nền tảng Docker

## 1. Về công sức triển khai
- Việc kết hợp **WordPress** với **Docker** giúp tiết kiệm thời gian đáng kể.  
- Thay vì cài đặt thủ công từng thành phần (Apache/Nginx, PHP, MariaDB), mọi thứ đã được đóng gói sẵn thành các **image**.  
- Chỉ cần định nghĩa trong file `docker-compose.yml` và chạy một lệnh duy nhất, toàn bộ hệ thống (Web, Database, UI quản lý) khởi động và liên kết với nhau trong vài phút.

---

## 2. Mức độ dễ/khó sử dụng
- **Dashboard** của WordPress trực quan, thân thiện.  
- **Block Editor** hỗ trợ kéo thả văn bản, hình ảnh, âm thanh, video dễ dàng, không cần viết code frontend.  
- Tích hợp sẵn **phpMyAdmin** giúp quản trị cơ sở dữ liệu MariaDB qua giao diện web, loại bỏ sự phức tạp khi thao tác bằng SQL trên terminal.

---

## 3. Mức độ tiêu tốn tài nguyên máy chủ (RAM / CPU)
- Kiến trúc container hóa kiểm soát tài nguyên tốt.  
- Trung bình:
  - MariaDB: 150–300MB RAM  
  - WordPress: 150–250MB RAM  
  - phpMyAdmin: <50MB RAM  
- Tổng cộng: khoảng **500MB–1GB RAM** ở trạng thái bình thường.  
- Với máy chủ 12GB RAM, cụm container chỉ chiếm <10% bộ nhớ.  
- CPU duy trì mức thấp (1–2%) cho lưu lượng truy cập blog/website cá nhân.

---

## 4. Khía cạnh bảo mật mạng và kết nối (SSH / Network)
- Mã nguồn WordPress thường xuyên được cộng đồng cập nhật bản vá bảo mật.  
- Hạ tầng mạng an toàn nhờ **Cloudflare Tunnel**, không cần mở port trực tiếp trên router.  
- Máy chủ không phải công khai IP ra internet, giảm nguy cơ bị hacker rà quét hoặc brute-force vào SSH.

---

## ✅ Kết luận
Sử dụng **WordPress mã nguồn mở** kết hợp với **Docker** là giải pháp tối ưu:  
- Triển khai nhanh chóng  
- Quản trị nội dung dễ dàng  
- Tiêu thụ tài nguyên thấp  
- Đảm bảo bảo mật và hiện đại cho hệ thống
