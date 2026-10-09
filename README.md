DevOps Hackathon - Đề

1. Thông tin sinh viên

- **Họ và tên:** Nguyễn Hoàng Minh Nhật
- **Mã sinh viên:** [Điền mã sinh viên của bạn]
- **Lớp:** HCM-K24-CNTT1
- **Tài khoản Server (User):** `mnhat`

2. Mô tả dự án
   **Nginx** trên máy chủ ảo **Ubuntu 24.04 LTS (Microsoft Azure)**.

3. Cấu trúc thư mục nộp bài

- `nginx/`: Chứa file cấu hình Nginx (`mnhat-k24cntt1.conf`).
- `screenshots/`: Chứa các ảnh minh chứng quá trình làm bài.
  - `01-user.png`: Minh chứng tạo user `mnhat` và cấp quyền sudo.
  - `02-nginx.png`: Minh chứng file cấu hình Nginx trỏ đúng đường dẫn web.
  - `03-ufw.png`: Minh chứng cấu hình tường lửa UFW (mở port 22, 80, 443).
  - `05-git-log.png`: Minh chứng lịch sử commit trên GitHub.
- `src/`: Chứa file `index.html` mã nguồn của trang web.

4. Các bước thực hiện chi tiết

### Bước 1: Khởi tạo tài khoản

- Đăng nhập vào Azure VM qua SSH bằng tài khoản đám mây mặc định.
- Tạo tài khoản cá nhân: `sudo adduser mnhat`
- Cấp quyền quản trị (sudo) cho tài khoản mới để thực thi các lệnh hệ thống: `sudo usermod -aG sudo mnhat`

### Bước 2: UFW

- Chặn kết nối chiều vào và cho phép kết nối chiều ra mặc định.
- Mở cổng 22 (SSH) để duy trì điều khiển máy chủ.
- Mở cổng 80 (HTTP) và 443 (HTTPS) để public trang web.
- Kích hoạt UFW: `sudo ufw enable`

### Bước 3: Nginx

- Cài đặt Nginx: `sudo apt install nginx -y`
- Tạo thư mục lưu trữ web hệ thống: `sudo mkdir -p /var/www/devops-hackathon-de005-mnhat`
- Sao chép file `index.html` từ mã nguồn vào thư mục lưu trữ web.
- Chỉnh sửa cấu hình tại `/etc/nginx/sites-available/default`:
  - Thay đổi `root` trỏ về `/var/www/devops-hackathon-de005-mnhat`.
  - Khai báo `index index.html`.
- Áp dụng cấu hình và khởi động lại Nginx: `sudo systemctl restart nginx`

### Bước 4: nộp bài

- Thu thập ảnh chụp màn hình vào thư mục `screenshots/`.
- Xuất file cấu hình Nginx lưu vào thư mục `nginx/`.
- Thực hiện `git add .`, `git commit` và `git push` để đẩy toàn bộ bài làm lên kho lưu trữ GitHub.

<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DevOps Hackathon</title>>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #f4f6f9; margin: 0; padding: 20px; color: #333; }
    </style>

</head>
<body>
<div class="container">
    <h1>Xin chào đến với Ptit Rikkei DevOps Lab </h1>
    <h2>Thông tin sinh viên</h2>
    <table>
        <tr><th>Họ và tên</th><td>Nguyễn Hoàng Minh Nhật</td></tr>
        <tr><th>Mã sinh viên</th><td></td></tr>
        <tr><th>Lớp</th><td>K24</td></tr>
        <tr><th>Email</th><td></td></tr>
        <tr><th>Tài khoản Linux</th><td></td></tr>
        <tr><th>GitHub</th><td><a href="" target="_blank"></a></td></tr>
    </table>
    <h2>Thông tin bài thi</h2>
    <table>
        <tr><th>Đề thi</th><td>Đề số </td></tr>
        <tr><th>Chủ đề</th><td>Quản lý kho hàng (Inventory)</td></tr>
        <tr><th>Cổng Nginx</th><td>8082</td></tr>
        <tr><th>IP máy chủ</th><td>221.121.4.90</td></tr>
        <tr><th>Ngày thi</th><td>08/10/2026</td></tr>
        <tr><th>Repository</th><td><a href="" target="_blank"></a></td></tr>
        <p style="color: #2e7d32; font-weight: bold;"></p>
    </table>
    <h2>Giới thiệu hệ thống</h2>
    <div class="desc-box">
        Hệ thống Quản lý kho hàng (Inventory) được xây dựng nhằm tối ưu hóa quy trình quản lý hàng hóa, theo dõi tồn kho và xử lý đơn hàng nhanh chóng. Giải pháp giúp doanh nghiệp dễ dàng kiểm soát danh mục sản phẩm, giá cả và chương trình khuyến mãi theo thời gian thực. Nền tảng được thiết kế với kiến trúc hiện đại, đảm bảo tính sẵn sàng cao, bảo mật và vận hành ổn định trên nền tảng Nginx.
    </div>
</div>
</body>
</html>

tải file zip về, mở file sau đó mở terminal trong file:
git init
git add .
git commit -m "init source code"
git branch -M main
git remote add origin https://github.com/Taikhoancuaban/devops-hackathon-de005-mnhat.git
git push -u origin main

mở file trong vs code:
kéo README.md vào sau đó gõ ở terminal:
ssh azureuser@85.211.197.124

1.Tạo tài khoản thi và cấp quyền:Tương đương ảnh 01-user.png.
sudo usermod -aG sudo mnhat
su - mnhat
Cách xác nhận: Terminal chuyển sang mnhat@.... Hãy chụp màn hình bước này để lưu làm minh chứng 01-user.png.2.Thiết lập Tường lửa (UFW):Tương đương ảnh 03-ufw.png.Bảo mật máy chủ và mở các port cần thiết cho Web.Bashsudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
sudo ufw status
Cách xác nhận: Kết quả trả về Status: active kèm các port 22, 80, 443. Hãy chụp màn hình bước này để lưu thành 03-ufw.png.3.Clone dự án và đưa web vào thư mục hệ thống:Triển khai source code.Giả sử bạn đã fork đề thi về GitHub của bạn. Tải code về và copy file index.html vào đúng thư mục chuẩn của Nginx (/var/www/).Bash# Clone code về (thay link bằng repo thi thật của bạn ngày mai)
git clone https://github.com/Taikhoancuaban/devops-hackathon-de005-mnhat.git
cd devops-hackathon-de005-mnhat

# Tạo thư mục chứa web giống đề 004

sudo mkdir -p /var/www/devops-hackathon-de005-mnhat

# Copy file index.html từ thư mục src/ vào thư mục web vừa tạo

sudo cp src/index.html /var/www/devops-hackathon-de005-mnhat/

4.Cấu hình Nginx Web Tĩnh:Tương đương ảnh 02-nginx.png.Xóa cấu hình cũ và tạo cấu hình mới. Điểm khác biệt lớn nhất so với bài hôm trước là ta dùng root để trỏ tới file html, không dùng proxy*pass.Bashsudo truncate -s 0 /etc/nginx/sites-available/default
sudo nano /etc/nginx/sites-available/default
Dán cấu hình này vào (lưu ý đường dẫn root):Nginxserver {
listen 80;
server_name *;

    root /var/www/devops-hackathon-de005-mnhat;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }

}
Lưu file (Ctrl + O, Enter, Ctrl + X). Kích hoạt và kiểm tra:Bashsudo systemctl restart nginx
sudo systemctl status nginx
Cách xác nhận: Mở IP trên trình duyệt web, trang index.html của bạn sẽ hiện ra. Hãy chụp màn hình file cấu hình Nginx để làm 02-nginx.png[cite: 4, 5].

5.Lưu ảnh, Commit và Push bài thi:Tương đương ảnh 05-git-log.png.Đưa các ảnh đã chụp vào thư mục screenshots/ (tạo ra nếu chưa có)[cite: 4, 5], thêm cấu hình Nginx vào thư mục nginx/[cite: 4, 5], sau đó commit lên GitHub.Bash# (Giả định bạn đã dùng công cụ SFTP hoặc VS Code kéo thả ảnh vào thư mục screenshots/)

terminal macbook

# Copy file cấu hình Nginx để nộp

mkdir -p nginx
cp /etc/nginx/sites-available/default nginx/mnhat-k24cntt1.conf

terminal macbook

# Commit và Push

git add .
git commit -m "Hoan thanh bai thi Hackathon DevOps"
git push

# Xem log

git log --oneline
Cách xác nhận: Lệnh log hiện ra lịch sử commit. Hãy chụp màn hình lệnh này để làm 05-git-log.png
