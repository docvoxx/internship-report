---
title: "Tuần 3 Worklog"
date: ""
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

* Thực hành các dịch vụ lưu trữ AWS, bao gồm:  
    - Amazon S3, Storage Gateway, AWS Backup, Amazon FSx.  
* Nâng cao kiến thức về bảo mật và quản lý truy cập AWS qua IAM (Users, Groups, Roles, Policies).  
* Thực hành vận hành dịch vụ thông qua AWS Console và CLI.  
* Ghi chép quan sát và tổ chức kiến thức để hỗ trợ các bài tập tuần tiếp theo.  

### Công việc trong tuần:

| Thứ | Công việc                                                                                                                                                                   | Ngày bắt đầu  | Ngày hoàn thành | Tài liệu tham khảo                                                                                          |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | --------------- | ---------------------------------------------------------------------------------------------------------- |
| 2   | - Khám phá các tùy chọn lưu trữ AWS: S3, thiết bị Snow Family, Storage Gateway và AWS Backup; tìm hiểu vai trò của chúng trong bảo vệ và phục hồi dữ liệu                         | 22/09/2025  | 22/09/2025      | [FCJ YT](https://www.youtube.com/watch?v=AQlsd0nWdZk&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i), [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 3   | - Tạo và cấu hình bucket Amazon S3; thiết lập kế hoạch AWS Backup và thử nghiệm workflow backup/restore                                                                      | 23/09/2025  | 23/09/2025      | [Ghi chú AWS của tôi](https://www.notion.so/i-n-to-n-m-m-y-26a4c2b6beb680beb5eaf9d9f48b8b00?source=copy_link) |
| 4   | - Triển khai File Storage Gateway để kết nối hybrid giữa hệ thống on-prem và lưu trữ trên AWS                                                                       | 24/09/2025  | 24/09/2025      | [Ghi chú AWS của tôi](https://www.notion.so/i-n-to-n-m-m-y-26a4c2b6beb680beb5eaf9d9f48b8b00?source=copy_link) |
| 5   | - Triển khai Amazon FSx cho Windows File Server và kiểm tra tính năng chia sẻ file, tích hợp Active Directory                                                                   | 25/09/2025  | 25/09/2025      | [Ghi chú AWS của tôi](https://www.notion.so/i-n-to-n-m-m-y-26a4c2b6beb680beb5eaf9d9f48b8b00?source=copy_link) |
| 6   | - Nghiên cứu IAM và cơ chế bảo mật AWS; ghi chép người dùng, role, policy và các best practice được khuyến nghị                                                                | 26/09/2025  | 26/09/2025      | [Video Security](https://www.youtube.com/watch?v=N_vlJGAqZxo&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=151) |

### Thành tựu tuần 3:

### Amazon S3
- Lưu trữ đối tượng với khả năng mở rộng gần như vô hạn; mỗi đối tượng tối đa 5 TB.  
- Hỗ trợ tải lên nhiều phần (multipart upload), thông báo sự kiện và quản lý vòng đời tự động.  
- Độ bền 99,999999999% và độ khả dụng 99,99%.  
- Cung cấp nhiều lớp lưu trữ: Standard, Standard-IA, One Zone-IA, Intelligent-Tiering, Glacier, Deep Archive.  
- Lifecycle rules có thể tự động chuyển dữ liệu giữa các lớp lưu trữ.  
- Hỗ trợ hosting website tĩnh và CORS cho các yêu cầu cross-origin.  
- Kiểm soát truy cập bằng ACL, bucket policies và IAM policies; có thể truy cập riêng tư qua VPC endpoints.  
- Versioning cho phép phục hồi dữ liệu khi bị xóa hoặc ghi đè.  
- Glacier cung cấp lưu trữ dài hạn chi phí thấp với ba tốc độ truy xuất: Expedited, Standard, Bulk.  

### Snow Family & Storage Gateway
- **Snowball:** thiết bị ~80 TB để chuyển dữ liệu từ on-prem lên AWS.  
- **Snowball Edge:** ~100 TB lưu trữ + khả năng tính toán tại chỗ để xử lý dữ liệu trước khi chuyển.  
- **Snowmobile:** thiết bị quy mô xe tải (~100 PB) cho dữ liệu cực lớn.  
- **Storage Gateway:** kết nối hệ thống on-prem với AWS:  
    - **File Gateway (NFS/SMB):** truy cập S3 dưới dạng file share.  
    - **Volume Gateway (iSCSI):** lưu trữ block với snapshot gửi tới EBS/S3.  
    - **Tape Gateway (VTL):** thư viện tape ảo lưu trữ lên S3/Glacier, thay thế tape vật lý.  

### Backup & Disaster Recovery
- **RTO (Recovery Time Objective):** thời gian downtime tối đa cho phép.  
- **RPO (Recovery Point Objective):** khoảng thời gian mất dữ liệu tối đa chấp nhận được.  
- Chiến lược DR phổ biến: Backup & Restore, Pilot Light, Low-capacity Active-Active, Full Active-Active.  
- **AWS Backup:** dịch vụ tập trung để quản lý và giám sát backup cho EBS, EC2, RDS, DynamoDB, EFS, Storage Gateway.  

### FSx
- Cấu hình Amazon FSx cho Windows File Server.  
- Cung cấp lưu trữ file native Windows có thể truy cập qua SMB.  
- Phù hợp với workloads cần tích hợp Active Directory hoặc ứng dụng Windows.  

### Security & IAM
- **Shared Responsibility Model:** AWS bảo mật hạ tầng; khách hàng bảo mật dữ liệu và cấu hình.  
- **Root Account:** quyền đầy đủ — best practice: hạn chế sử dụng, tạo IAM admin, bảo mật credentials.  
- **IAM User:** danh tính mặc định không có quyền, có thể nhóm để quản lý dễ hơn.  
- **IAM Policy:** định nghĩa JSON quyền; gồm identity-based và resource-based; deny ưu tiên over allow.  
- **IAM Role:** credential tạm thời qua STS, gồm quyền và trust policy.  
    - Dùng cho least-privilege access, cross-account access hoặc cấp quyền cho dịch vụ.
