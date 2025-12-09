---
title: "Tuần 10 Worklog"
date: ""
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

#### Mục tiêu tuần 10:

- **Kiến trúc giải pháp:** Tinh chỉnh sơ đồ **High-Level (HLD)** và **Low-Level (LLD)** phù hợp với AWS Well-Architected Framework.  
- **Lập kế hoạch tài nguyên & ước tính chi phí:** Hiểu về **TCO (Total Cost of Ownership)** và đánh giá các lựa chọn dịch vụ để tối ưu hiệu quả.  
- **Nền tảng mạng:** Thiết lập môi trường mạng ban đầu bao gồm **VPC**, subnets và các cơ chế bảo mật cơ bản.  

### Hoạt động thực hiện trong tuần:

| Ngày     | Hoạt động                                                                                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| :------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :---------------- |
| **2-3** | **Kiến trúc & Lập kế hoạch:**<br>- Xem xét yêu cầu kinh doanh và xác định các thành phần quan trọng.<br>- Phác thảo sơ đồ kiến trúc hệ thống thể hiện luồng dữ liệu và bố trí tài nguyên.<br>- Ước tính chi phí bằng **AWS Pricing Calculator** và xem xét các biện pháp tiết kiệm.<br>- Kiểm tra sự phù hợp với 5 trụ cột của **Well-Architected Framework**. | 10/11/2025 | 11/11/2025      |                   |
| **4-5** | **Khởi tạo hạ tầng (IaC):**<br>- Phát triển scripts Terraform/CloudFormation để provision **VPC**, Public/Private Subnets, NAT Gateway và Route Tables.<br>- Cấu hình Security Groups cho Bastion Hosts, Application Servers và Databases theo best practices. | 12/11/2025 | 13/11/2025      |                   |

---

### Nhận xét tuần 10: Kiến trúc & Nền tảng mạng

#### 1. Hiểu biết về Thiết kế Kiến trúc

- **Biểu diễn sơ đồ:** Hoàn thành sơ đồ luồng dữ liệu và bố trí tài nguyên, sử dụng **Single-AZ** để đơn giản hóa giai đoạn đầu.  
- **Quyết định dịch vụ:**  
  - **Cơ sở dữ liệu quan hệ:** Chọn RDS MySQL với Multi-AZ để tăng tính chịu lỗi.  
  - **Lưu trữ:** Sử dụng S3 cho tệp tĩnh và backup.  
- **Nhận thức về chi phí:** Phát triển ước tính chi phí hàng tháng sơ bộ và xác định các chiến lược tối ưu, như sử dụng **Spot Instances** trong môi trường phát triển và áp dụng **Savings Plans** trong sản xuất.

#### 2. Nền tảng mạng & Bảo mật

- **Thiết lập VPC:** Xây dựng VPC cấu trúc rõ ràng với phân tách giữa **Public** và **Private subnets** cho ứng dụng và cơ sở dữ liệu.  
- **Triển khai bảo mật:** Áp dụng nguyên tắc **least privilege** trong cấu hình Security Groups để bảo vệ các lớp bastion, web và database.  

Tổng kết, tuần này đã đặt nền móng cho **sự rõ ràng kiến trúc** và **một môi trường mạng bảo mật, vận hành ổn định**, chuẩn bị cho các bước triển khai và tích hợp dịch vụ tiếp theo.
