---
title: "Tuần 11 Worklog"
date: ""
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---
### Mục tiêu tuần 11:

- **Triển khai dịch vụ cốt lõi:** Cấu hình các tài nguyên compute và database nền tảng để hỗ trợ ứng dụng.  
- **Tự động hóa & DevOps:** Thiết lập pipeline CI/CD nhằm tối ưu hóa quá trình build và triển khai trong môi trường đám mây.  

### Hoạt động thực hiện tuần này:

| Ngày     | Hoạt động                                                                                                                                                                                                                                                           | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| :------ | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :---------------- |
| **2-3** | **Thiết lập Compute & Database:**<br>- Provision RDS instance (ban đầu Single-AZ, sau đó nâng cấp Multi-AZ để tăng khả năng chịu lỗi).<br>- Thiết lập kết nối giữa application server và cơ sở dữ liệu MySQL.                                                      | 17/11/2025 | 18/11/2025      |                   |
| **4-5** | **Triển khai CI/CD Pipeline:**<br>- Cấu hình source repository (CodeCommit/GitHub).<br>- Tự động hóa quá trình build qua CodeBuild.<br>- Tích hợp CodeDeploy và CodePipeline để triển khai tự động lên EC2 instances.<br>- Kiểm tra luồng triển khai end-to-end từ code cục bộ đến môi trường đám mây. | 19/11/2025 | 20/11/2025      |                   |

---

### Nhận xét tuần 11: Môi trường vận hành & Tự động hóa

#### 1. Ổn định ứng dụng & Kết nối cơ sở dữ liệu

- **Độ ổn định RDS:** Cơ sở dữ liệu hiện chạy ở chế độ Multi-AZ, cải thiện khả năng chịu lỗi và độ bền dữ liệu.  
- **Tích hợp ứng dụng:** Application servers kết nối thành công với database, cho phép các chức năng dựa trên dữ liệu hoạt động ổn định.  

#### 2. DevOps & Triển khai liên tục

- **Pipeline hoàn chỉnh:** Thiết lập thành công workflow CI/CD tự động:  
  - **Quản lý source:** Commit đẩy lên GitHub hoặc CodeCommit tự động kích hoạt build.  
  - **Quá trình build:** Tự động cài đặt dependencies, đóng gói artifacts và kiểm thử.  
  - **Triển khai:** Phiên bản mới được rollout lên EC2 instances với gián đoạn tối thiểu, áp dụng các chiến lược zero-downtime như rolling updates.  

Tuần này đã thiết lập nền tảng vận hành vững chắc, kết hợp giữa RDS chịu lỗi và pipeline triển khai tự động, sẵn sàng cho việc mở rộng và duy trì ứng dụng trên cloud.
