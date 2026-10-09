# Báo cáo: Quản trị Tường lửa UFW cho Cụm Dịch vụ Multi-port

## 1. Các bước cấu hình đã thực hiện

Khai báo các chính sách mặc định:
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

Cho phép các cổng dịch vụ theo yêu cầu (SSH, HTTP, Spring Boot):
```bash
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 8082/tcp
```

Kích hoạt UFW:
```bash
sudo ufw enable
```

*Lưu ý: Cổng MySQL (3306/tcp) không được thêm luật `allow`, do đó sẽ bị chặn mặc định bởi chính sách `deny incoming` từ Internet.*

## 2. Kết quả kiểm tra trạng thái tường lửa

Đầu ra của lệnh `sudo ufw status verbose`:

```text
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    Anywhere                  
80/tcp                     ALLOW IN    Anywhere                  
8082/tcp                   ALLOW IN    Anywhere                  
22/tcp (v6)                ALLOW IN    Anywhere (v6)             
80/tcp (v6)                ALLOW IN    Anywhere (v6)             
8082/tcp (v6)              ALLOW IN    Anywhere (v6)             
```