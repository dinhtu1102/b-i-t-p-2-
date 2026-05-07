# Môn: Phát triển ứng dụng với mã nguồn mở-TEE0421
# Lớp: 58KTPM
# Bài tập 02:
# SỬ DỤNG DJANGO ĐỂ TẠO WEB QUẢN LÝ TIỆM CẦM ĐỒ

# BÀI LÀM

1 TỔ CHỨC CSDL CHO HỆ THỐNG QUẢN LÝ TIỆM CẦM ĐỒ: viết tay ra giấy, lấy điện thoại chụp lại, upload ảnh lên github (đã nói về các nghiệp vụ trên lớp, ghi bảng)

2 SỬ DỤNG DOCKER TRÊN UBUNTU ĐỂ:

*  PHẦN 1 — CHUẨN BỊ UBUNTU
  
Cập nhật Ubuntu

  sudo apt update && sudo apt upgrade -y

<img width="1919" height="571" alt="image" src="https://github.com/user-attachments/assets/54c3ec76-f8b6-403d-95d5-c7f96875b72e" />

PHẦN 2 — CÀI DOCKER

Cài Docker

  sudo apt install docker.io -y

<img width="1919" height="347" alt="image" src="https://github.com/user-attachments/assets/7c4f1342-43c2-4d22-9386-73eded1ce0bb" />

Khởi động:

  sudo systemctl enable docker

<img width="1919" height="285" alt="image" src="https://github.com/user-attachments/assets/30005a29-052e-45af-9737-7be80a59a3fc" />

  sudo systemctl start docker

Kiểm tra:

  docker --version

<img width="1918" height="188" alt="image" src="https://github.com/user-attachments/assets/69e2aa04-3a09-4006-a41a-a9903625e2fb" />

Cài Docker Compose

  sudo apt install docker-compose -y

<img width="1919" height="213" alt="image" src="https://github.com/user-attachments/assets/f6ee2972-4f54-4ec3-86a7-6230a2d96a57" />

Kiểm tra:

  docker-compose --version

<img width="1919" height="350" alt="image" src="https://github.com/user-attachments/assets/3aee34b7-ed9c-497e-ac16-255db74e450d" />

PHẦN 3 — TẠO THƯ MỤC PROJECT

  mkdir camdo_project
  cd camdo_project

<img width="1294" height="439" alt="image" src="https://github.com/user-attachments/assets/63348fd9-3520-4b43-9950-12a17d00fe94" />

PHẦN 4 — TẠO THƯ MỤC DJANGO

  mkdir django_app

<img width="1919" height="159" alt="image" src="https://github.com/user-attachments/assets/fb9fd25d-2b70-45d7-b174-b46be362990c" />

PHẦN 5 — TẠO Dockerfile

Đi vào thư mục django_app:

  cd django_app
  
<img width="1915" height="543" alt="image" src="https://github.com/user-attachments/assets/f71e7b65-2e8d-4a2b-850b-f0b0bc2c617a" />

Tạo file:

  sudo nano Dockerfile

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/2276971d-554e-4580-b095-d4892efab60d" />

PHẦN 6 — TẠO requirements.txt

  sudo nano requirements.txt

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/11b07ac4-b161-4710-a287-795aa9ae7528" />

PHẦN 7 — TẠO docker-compose.yml

Quay lại thư mục gốc:

  cd ..

Tạo file:

  sudo nano docker-compose.yml

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/ee83016a-5df1-4700-8d49-2a074cbf5172" />

PHẦN 8 — BUILD HỆ THỐNG

  docker compose up -d --build

<img width="1919" height="751" alt="image" src="https://github.com/user-attachments/assets/5d6ce7d6-0d9a-4957-b54b-fec7af20a496" />

Kiểm tra:

  docker ps

<img width="1917" height="295" alt="image" src="https://github.com/user-attachments/assets/b4b3691f-7e96-4bf8-8f75-97c94c65c9bc" />

PHẦN 9 — TẠO DJANGO PROJECT

Vào container Django:

  docker compose exec django bash

<img width="1919" height="291" alt="image" src="https://github.com/user-attachments/assets/27d08d0e-5b4f-439d-938d-8172a76f6849" />

Tạo project

  django-admin startproject config .

<img width="1919" height="265" alt="image" src="https://github.com/user-attachments/assets/8c36590e-3755-47f3-8496-01b92302df69" />

Tạo project

  django-admin startproject config .

Tạo app

  python manage.py startapp camdo

<img width="1919" height="338" alt="image" src="https://github.com/user-attachments/assets/859c6267-4963-468f-b66c-50df4b153132" />

PHẦN 10 — CẤU HÌNH DATABASE

Mở file:

  nano config/settings.py

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/97c44ace-bab8-4890-9f71-1583797071a9" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/bce9a0d9-fa2a-4cfc-869e-93ab44659791" />

Thêm app

Tìm:

  INSTALLED_APPS

Thêm:

  'comdo'

<img width="645" height="467" alt="image" src="https://github.com/user-attachments/assets/ae5ab1a4-7333-4d4b-b005-a9b16261d272" />

Cho phép truy cập

Tìm:

  ALLOWED_HOSTS

Sửa:

  ALLOWED_HOSTS = ['*']

<img width="605" height="276" alt="image" src="https://github.com/user-attachments/assets/d0a43af6-ceb2-43d6-9271-fada20c760a2" />

PHẦN 11 — TẠO BẢNG models.py

Mở:

  nano camdo/models.py

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/8585095f-3cb2-43d0-b275-042940a99850" />

PHẦN 12 — MIGRATE DATABASE

  python manage.py makemigrations

  python manage.py migrate

<img width="1918" height="269" alt="image" src="https://github.com/user-attachments/assets/df20adaa-b602-46f2-be6f-01cc6fd13404" />

PHẦN 13 — TẠO USER ADMIN

python manage.py createsuperuser

Nhập:

username

email

password

<img width="1919" height="657" alt="image" src="https://github.com/user-attachments/assets/80d5a8d6-4936-4b09-9339-5efcf7b7caa7" />

PHẦN 14 — ĐĂNG KÝ ADMIN

Mở:

  nano camdo/admin.py

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/8bc0e830-7946-4f4c-bf99-1415ef02e3ac" />

PHẦN 15 — KHỞI ĐỘNG LẠI

Thoát container:

  exit

Restart:

  docker compose restart  

PHẦN 16 — TRUY CẬP WEBSITE

Django Admin

  http://IP_MAY_AO:8000/admin

Đăng nhập bằng tài khoản admin.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/9ea353ae-83a2-4bc7-b05d-62f7949182f1" />

PHẦN 17 — KIỂM TRA FK

Trong admin:

tạo khách hàng

tạo tài sản

tạo hợp đồng

👉 Trường FK sẽ hiện dropdown chọn text.

PHẦN 18 — KIỂM TRA TRONG phpMyAdmin

Mở:

  http://IP_MAY_AO:8081

Login:
  
  user: root
  
  pass: root123

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/725a0c33-ca33-4d74-9275-5c82a929ba64" />

👉 Mở bảng:

  camdo_hopdongcamdo

<img width="1919" height="1040" alt="image" src="https://github.com/user-attachments/assets/f01d7a77-5caf-405d-b2c5-54e5ada53c1f" />

Bạn sẽ thấy:

  khach_hang_id
  
  tai_san_id

=> FK thực tế lưu ID.

PHẦN 19 — TEMPLATE HTML

Tạo thư mục templates

  mkdir django_app/templates

Tạo home.html

  nano django_app/templates/home.html

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/3fcb6e54-7755-48d7-b08d-c0108c273a75" />

PHẦN 20 — TẠO VIEW

Mở:

  nano django_app/camdo/views.py

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/42a78a0b-c08a-46d7-802f-e57ac3ba37de" />

PHẦN 21 — URLS

Mở:
  
  nano django_app/config/urls.py

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/757f4886-6fea-4b7a-bf19-bf1197ecfc77" />

PHẦN 22 — CLOUDFLARE TUNNEL

Cài:

  Cloudflare Tunnel

  curl -L https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb -o cloudflared.deb

  sudo dpkg -i cloudflared.deb

<img width="1917" height="338" alt="image" src="https://github.com/user-attachments/assets/68af03d2-e57a-478f-89d3-14cc43c49eb3" />

Login

  cloudflared tunnel login

<img width="1919" height="451" alt="image" src="https://github.com/user-attachments/assets/df0c90e1-fabd-4c0f-9b83-688b5c27f1a1" />

Tạo tunnel

  cloudflared tunnel create django

<img width="1919" height="246" alt="image" src="https://github.com/user-attachments/assets/dd857602-5af7-4fd5-bb99-dbfbb4357a84" />

Gắn subdomain

  cloudflared tunnel route dns django camdo.dinhtu.id.vn

<img width="1919" height="170" alt="image" src="https://github.com/user-attachments/assets/6cc5a46b-b863-4e5e-b096-75f21526a744" />

Run tunnel

  cloudflared tunnel run --url http://localhost:8000 django

<img width="1919" height="690" alt="image" src="https://github.com/user-attachments/assets/80767aea-bc3f-4938-89b6-4510422f172a" />

Mariadb : chứa csdl của hệ thống này

Phpmyadmin: để soi được csdl (chỉ để xem, ko cần tạo bảng từ đây, django sẽ làm hết)

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/a4a15c2a-9c02-400f-9e01-330403b4def6" />

Django: build 1 docker container (dùng Dockerfile): trên nền python, sử dụng django, nhớ mount thư mục để dễ edit, edit dùng: sudo nano ten_file

<img width="1919" height="1065" alt="image" src="https://github.com/user-attachments/assets/7042180e-20de-4252-8891-afa5ad91cc25" />

sau khi có 3 service này trong file docker-compose.yml :

run nó, cấu hình để Django nhận csdl mariadb (sửa file settings.py), cấu hình user login ban đầu, mô tả các bảng trong models.py, .... (đc phép sử dụng AI để làm) => KQ được trang admin, y/c đăng nhập, vào trang admin: cho phép thêm sửa xoá dữ liệu các bảng. các trường là khoá ngoại chỉ việc chọn text (mặc dù là csdl tại trường FK đó lưu ID của PK mà nó tham chiếu : sử dụng phpmyadmin để kiểm chứng)
chú ý kết hợp ssh để chạy lệnh tác động vào django và sudo nano để edit file.
sử dụng template (file html, sử dụng cú pháp jinja2), lấy context từ 1 view home_page, để tạo trang liệt kê các con nợ đến hạn mà chưa trả tiền!
sử dụng cloudflare tunnel để public kết quả lên 1 sub-domain => chụp kết quả

* Thành quả chạy

<img width="1919" height="1078" alt="image" src="https://github.com/user-attachments/assets/a8950234-4e86-496f-8404-99116bb8695a" />

* Vào trang quản trị.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/2ab7595c-2f23-47b0-affd-effd86d183e2" />



