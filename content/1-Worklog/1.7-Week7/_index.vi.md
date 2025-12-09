---
title: "Tuần 7 Worklog"
date: ""
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

- Tổ chức và củng cố kiến thức đã học trong nửa đầu kỳ thực tập.  
- Nâng cao hiểu biết về **Bảo mật (Security)** và **Khả năng phục hồi (Resiliency)** trên AWS.  
- Xây dựng nền tảng vững chắc cho kỳ thi Midterm.

### Công việc trong tuần:

| Ngày   | Công việc                                                                                                                                                                                                                                                                                                                                 | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                              |
| :---- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :---------------------------------------------------------------------------- |
| **2** | **Ôn tập Midterm:**<br><br>**Phần 1: Kiến thức cơ bản về bảo mật**<br>- IAM (Quản lý người dùng và quyền truy cập)<br>- KMS (Quản lý khóa) <br>- Security Groups & NACLs <br>- Secrets Manager <br>- GuardDuty (Phát hiện mối đe dọa) <br>- Shield & WAF (Bảo vệ DDoS và ứng dụng web) <br><br>**Phần 2: Kiến trúc có khả năng phục hồi**<br>- Chỉ số cốt lõi: RTO/RPO <br>- Multi-AZ RDS <br>- Chiến lược Disaster Recovery <br>- Auto Scaling & Load Balancing <br>- Route 53 & DNS <br>- AWS Backup | 20/10/2025 | 20/10/2025      | [Review Link](https://ruskicoder.github.io/fcj-midterm-2025/)                 |
| **3** | Tự học: Hệ thống hóa kiến thức các dịch vụ bảo mật và thực hành lab mô phỏng                                                                                                                                                                                                                                                   | 21/10/2025 | 21/10/2025      |                                                                               |
| **4** | Tự học: Vẽ lại sơ đồ kiến trúc High Availability (HA) và Disaster Recovery (DR) để củng cố hiểu biết                                                                                                                                                                                                                  | 22/10/2025 | 22/10/2025      |                                                                               |
| **5** | Làm bài kiểm tra thử để đánh giá kiến thức và xác định điểm yếu cần cải thiện                                                                                                                                                                                                                                                                   | 23/10/2025 | 23/10/2025      | [Practice Exams](https://ezse.net/aws/certified-cloud-practitioner/examtopics.html) |
| **6** | Tổng hợp câu hỏi và ghi chú quan trọng để ôn tập cuối cùng                                                                                                                                                                                                                                                                        | 24/10/2025 | 24/10/2025      | [Additional Resources](https://ruskicoder.github.io/fcj-midterm-2025/6-additional-resources/) |

---

### Thành tựu tuần 7: Nâng cao nhận thức về bảo mật và kiến trúc có khả năng phục hồi

- **Tư duy Defense in Depth:**  
  - Phân biệt rõ **Security Groups** (stateful, cấp instance) và **NACLs** (stateless, cấp subnet).  
  - Hiểu cơ chế bảo vệ đa tầng: **WAF** cho tầng ứng dụng (L7), **Shield** cho tầng hạ tầng (L3/L4), và **GuardDuty** để phát hiện mối đe dọa thông minh.  
  - Nắm vững vai trò của **KMS** và **Secrets Manager** trong bảo vệ dữ liệu nhạy cảm khi lưu trữ và truyền tải.

- **Khả năng phục hồi & Phục hồi sau sự cố:**  
  - Hiểu rõ **RTO (Recovery Time Objective)** và **RPO (Recovery Point Objective)** để lựa chọn chiến lược DR phù hợp (Backup & Restore, Pilot Light, Warm Standby, Multi-site Active/Active).  
  - Nắm được cách sử dụng **Multi-AZ RDS** để đảm bảo High Availability so với Read Replicas cho việc mở rộng đọc.  
  - Hiểu cách **Route 53, ELB, và Auto Scaling** phối hợp để xây dựng kiến trúc linh hoạt, tự phục hồi và có khả năng mở rộng.
