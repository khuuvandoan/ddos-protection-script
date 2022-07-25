# DDoS Protection for Linux Machines
CẢNH BÁO! Tập lệnh này thường không hoạt động đúng với LXD / LXC Containers, vui lòng chỉ sử dụng trên KVM-based VPS hoặc Máy chủ kim loại trần.


## For CentOS/RHEL/AlmaLinux
```
wget https://raw.githubusercontent.com/khuuvandoan/ddos-protection-script/main/script-rhel.sh && chmod +x antiddos-rhel.sh && ./antiddos-rhel.sh
```

## For Ubuntu/Debian
```
wget https://raw.githubusercontent.com/khuuvandoan/ddos-protection-script/main/antiddos-debian.sh && chmod +x antiddos-debian.sh && ./antiddos-debian.sh
```


Sau khi chạy tập lệnh, cấu hình tùy chỉnh IPTables đã được áp dụng. Nếu IPTables không được cài đặt trên hệ điều hành của bạn, nó sẽ được cài đặt khi chạy tập lệnh.

### What does this script do?
Tập lệnh này sử dụng IPtables. Nó sẽ làm tốt công việc bảo vệ máy của bạn chống lại các cuộc tấn công DDoS, nhưng không bao giờ là một ý tưởng tồi nếu có thêm tính năng bảo vệ DDoS từ các nhà cung cấp như PATH.NET, OVH, Cloudflare (chỉ khi thực sự cần thiết), v.v. Nó bổ sung cấu hình để loại bỏ gói không hợp lệ, thả gói là gói TCP mới và không phải là SYN, chặn gói có cờ TCP kỳ lạ / đáng ngờ, chặn gói có giá trị MSS đáng ngờ, chặn tất cả các gói giả mạo, vô hiệu hóa giao thức ICMP (máy của bạn sẽ không phản hồi với ping , khiến mọi người không thể gửi một cuộc tấn công đến VPS của bạn bằng cách sử dụng ping chết hoặc tấn công Lớp 4), giới hạn số lượng kết nối trên mỗi IP được kết nối, thả các đoạn trong tất cả các chuỗi, giới hạn tất cả các gói RST, thêm bảo vệ bruteforce cho SSH và cuối cùng, thêm bảo vệ chống lại quá trình quét cổng.
