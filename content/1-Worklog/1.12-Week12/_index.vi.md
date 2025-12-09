---
title: "Tuần 12 Worklog"
date: ""
weight: 2
chapter: false
pre: " <b> 1.12 </b> "
---
### Mục tiêu tuần 12:

- **Bảo mật & Giám sát:** Quét lỗ hổng bảo mật và thiết lập Dashboard giám sát hệ thống.  
- **Hoàn thiện dự án:** Hoàn tất tài liệu, thực hiện tối ưu cuối cùng và chuẩn bị slide thuyết trình.  

### Nhiệm vụ thực hiện tuần này:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **2-3** | - Cấu hình CloudWatch Alarms và Dashboard.<br>- Thực hiện kiểm tra bảo mật bằng AWS Trusted Advisor và GuardDuty. | 24/11/2025 | 25/11/2025 | |
| **4-5** | **Tối ưu & Hoàn thiện:**<br>- Xem xét và xóa các tài nguyên thừa để tối ưu chi phí.<br>- Viết tài liệu vận hành (Runbook).<br>- Soạn thảo slide báo cáo cuối cùng (Kiến trúc, Thách thức, Bài học kinh nghiệm). | 26/11/2025 | 27/11/2025 | |

---

### Nhận xét tuần 12: Hoàn thiện hệ thống & Sẵn sàng bàn giao

#### 1. Đánh giá hiệu năng & Tối ưu

- **Giám sát:**  
  - Thiết lập **CloudWatch Dashboard** để trực quan hóa các chỉ số quan trọng: CPU Utilization, Request Count, Database Connections, Error Rate (4xx, 5xx).  
  - Cấu hình **SNS Alerts** để gửi email thông báo đến Admin khi hệ thống gặp sự cố.  

#### 2. Tối ưu & Bảo mật nâng cao

- **Bảo mật:**  
  - Kích hoạt **WAF (Web Application Firewall)** để chặn các cuộc tấn công phổ biến (SQL Injection, XSS).  
  - Rà soát các IAM Role và thu hồi quyền không cần thiết.  
- **Chi phí:** Dựa trên dữ liệu từ hai tuần chạy thử nghiệm, thay đổi kích thước Instances từ t3.medium sang t3.micro cho môi trường Dev để tiết kiệm chi phí mà không ảnh hưởng hiệu năng.  

#### 3. Hoàn tất dự án

- **Tài liệu:** Hoàn tất bộ tài liệu dự án bao gồm: Sơ đồ kiến trúc cập nhật, Hướng dẫn triển khai lại, Báo cáo chi phí.  
- **Bài học kinh nghiệm:** Rút ra hiểu biết về xử lý vấn đề "Cold Start" khi Auto Scaling và tầm quan trọng của cấu hình Health Check chính xác.


