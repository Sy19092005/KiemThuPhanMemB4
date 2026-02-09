# Kiểm thử hiệu năng bằng Apache JMeter

## 1. Website được kiểm thử
- Website: https://en.wikipedia.org
- Mục đích: Đánh giá hiệu năng và độ ổn định của website khi có nhiều người dùng truy cập đồng thời.

## 2. Công cụ sử dụng
- Apache JMeter 5.6.3
- Java JDK

## 3. Các kịch bản kiểm thử

### Thread Group 1 – Tải nhẹ (Basic Load)
- Số lượng người dùng (Users): 10
- Số vòng lặp (Loop Count): 5
- Thao tác: Gửi yêu cầu HTTP GET đến trang chủ (/)

### Thread Group 2 – Tải nặng (Heavy Load)
- Số lượng người dùng (Users): 50
- Thời gian tăng tải (Ramp-up Period): 30 giây
- Các yêu cầu:
  - HTTP GET đến trang chủ (/)
  - HTTP GET đến trang bài viết (/wiki/Software_testing)

### Thread Group 3 – Kịch bản tuỳ chỉnh
- Số lượng người dùng: 20
- Thời gian chạy: 60 giây
- Thao tác:
  - Gửi yêu cầu HTTP GET đến hai trang khác nhau trên Wikipedia

## 4. Cấu hình kiểm thử
- Sử dụng HTTP Request Defaults để thiết lập URL cơ sở cho các request.
- Cấu hình HTTP Header Manager với User-Agent nhằm mô phỏng hành vi của trình duyệt thật và tránh bị chặn request.

## 5. Kết quả kiểm thử (Thread Group 2)
- Tổng số mẫu (Total Samples): 100
- Thời gian phản hồi trung bình (Average Response Time): khoảng 1600 ms
- Tỷ lệ lỗi (Error Rate): 0%
- Thông lượng (Throughput): khoảng 3.2 request/giây

## 6. Kết luận
Website hoạt động ổn định khi chịu tải đồng thời với số lượng lớn người dùng. Mặc dù thời gian phản hồi tăng khi tải nặng, hệ thống vẫn không phát sinh lỗi. Việc cấu hình đầy đủ HTTP Header là yếu tố quan trọng giúp các request được xử lý thành công.
