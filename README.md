# Bài 1: Khảo sát FHS và Phân quyền File/Folder nâng cao

## 1. Tạo cấu trúc thư mục

Tạo thư mục `/var/www/my-app` gồm 2 thư mục con:

```bash
sudo mkdir -p /var/www/my-app/public
sudo mkdir -p /var/www/my-app/logs

Cấu trúc:

/var/www/my-app/
├── public/
└── logs/
2. Thiết lập Owner và Group

Sử dụng user hiện tại làm Owner và www-data làm Group:

sudo chown -R $USER:www-data /var/www/my-app
3. Phân quyền thư mục public

Yêu cầu:

Owner: đọc, ghi, thực thi
Group: đọc, thực thi
Others: không có quyền

Thiết lập quyền 750:

sudo chmod 750 /var/www/my-app/public

Kết quả mong muốn:

drwxr-x---
4. Phân quyền thư mục logs

Yêu cầu:

Owner: đọc, ghi, thực thi
Group: đọc, ghi, thực thi
Others: không có quyền

Thiết lập quyền 770:

sudo chmod 770 /var/www/my-app/logs

Kết quả mong muốn:

drwxrwx---
5. Kiểm tra kết quả
ls -la /var/www/my-app

Kết quả:

drwxr-x---  ... kien www-data ... logs
drwxr-x---  ... kien www-data ... public

Trong đó thư mục logs cần có quyền:

drwxrwx---

và thư mục public cần có quyền:

drwxr-x---
6. Kết luận

Đã hoàn thành việc tạo cấu trúc thư mục /var/www/my-app, thiết lập Owner là user thường kien, Group là www-data và phân quyền cho public và logs theo yêu cầu.


Sau khi copy đè, chạy:

```bash
git add README.md
git commit -m "update README bai 1"

Rồi kiểm tra:

git status

Lưu ý: trước khi commit, nhớ sửa logs thành 770:

sudo chmod 770 /var/www/my-app/logs
ls -la /var/www/my-app

Kết quả cần thấy:

drwxrwx--- ... kien www-data ... logs
drwxr-x--- ... kien www-data ... public