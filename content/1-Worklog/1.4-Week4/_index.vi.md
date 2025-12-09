---
title: "Tuần 4 Worklog"
date: ""
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Nâng cao kiến thức thực hành về các dịch vụ **AWS Identity & Security**:  
    - Khám phá **IAM**, **Cognito**, **AWS Identity Center (SSO)** và **Organizations** để quản lý quyền truy cập và governance.  
    - Thực hành **AWS KMS** để bảo vệ dữ liệu lưu trữ (at rest).  

* Thực hành với **AWS Security Hub** để tổng hợp thông tin bảo mật và đánh giá tiêu chuẩn tuân thủ.  

* Hiểu các cơ chế IAM nâng cao, bao gồm **Roles, Condition Keys, Permission Boundaries** để kiểm soát và giới hạn quyền truy cập.  

* Phân tích các tùy chọn compute và tối ưu chi phí bằng việc so sánh **EC2** và **Lambda** cho các kịch bản khác nhau.  

* Củng cố kỹ năng đọc, phân tích và chuyển hóa tài liệu AWS sang nội dung nội bộ dễ hiểu.

### Công việc trong tuần:

| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                            |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ------------------------------------- |
| 2   | - Làm quen các dịch vụ danh tính và bảo mật AWS: <br> &emsp; + Thử nghiệm **Cognito** với **User Pools** và **Identity Pools**. <br> &emsp; + Khám phá **AWS Organizations** quản lý multi-account: OU, SCP, billing. <br> &emsp; + Hiểu **AWS Identity Center (SSO)** cho truy cập đa tài khoản và ứng dụng bên ngoài. <br> &emsp; + Thực hành **AWS KMS**: mã hóa dữ liệu với CMK và Data Key. <br> - Thực hành: IAM Roles, Permission Boundaries, resource tagging, Security Hub, KMS workflows. | 29/09/2025 | 29/09/2025      | [AWS Study Group YouTube Playlist](https://www.youtube.com/watch?v=pZ2fgEFK3Vs&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=152) |
| 3   | - Khám phá **AWS Security Hub**: bật dịch vụ, tích hợp với GuardDuty/Config/Inspector, đánh giá compliance frameworks, quan sát cảnh báo. <br> - So sánh chi phí **EC2 vs Lambda** theo các pattern sử dụng. <br> - Áp dụng tag-based policies để kiểm soát quyền EC2, đánh giá hiệu quả qua IAM. | 30/09/2025 | 30/09/2025      | [AWS Security Hub Overview](https://www.notion.so/i-n-to-n-m-m-y-26a4c2b6beb680beb5eaf9d9f48b8b00?source=copy_link) <br> [EC2 vs Lambda Cost Optimization](https://www.notion.so/i-n-to-n-m-m-y-26a4c2b6beb680beb5eaf9d9f48b8b00?source=copy_link) <br> [RTA Management](https://www.notion.so/i-n-to-n-m-m-y-26a4c2b6beb680beb5eaf9d9f48b8b00?source=copy_link) |
| 4   | - Khám phá **IAM Roles và Conditions**: gán role cho EC2/Lambda, phân biệt **Trust Policies** và **Permission Policies**, thử nghiệm conditional access (IP, region, tags). <br> - Thực hành **mã hóa dữ liệu at rest** với KMS, so sánh với encryption in transit. | 01/10/2025 | 01/10/2025      | [IAM Role Document](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) <br> [KMS Encrypt Doc](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html) |
| 5   | - Nghiên cứu **Permission Boundaries**: giới hạn quyền cho user/role, so sánh với IAM policies thông thường. Lab: tạo user với boundary hạn chế EC2 trong một region, kiểm tra hiệu quả qua CLI và Console. | 02/10/2025 | 02/10/2025      | [IAM Permission](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) |
| 6   | - Khám phá các dịch vụ giám sát và kiểm toán của AWS: <br> &emsp; + Xem xét **AWS CloudTrail** để theo dõi hoạt động API trên các tài khoản AWS. <br> &emsp; + Tìm hiểu **AWS Config** để quan sát tuân thủ và thay đổi cấu hình của tài nguyên. <br> &emsp; + Sử dụng **Amazon CloudWatch** để theo dõi các chỉ số, tạo dashboard và thiết lập cảnh báo cho các tài nguyên quan trọng. <br> - Thực hành tạo cảnh báo và phân tích log để nắm được hoạt động hệ thống và các vấn đề bảo mật tiềm ẩn. | 03/10/2025 | 03/10/2025      | [AWS CloudTrail Overview](https://docs.aws.amazon.com/cloudtrail/index.html) <br> [AWS Config Overview](https://docs.aws.amazon.com/config/index.html) <br> [Amazon CloudWatch Overview](https://docs.aws.amazon.com/cloudwatch/index.html) |

### Thành tựu & nhận xét tuần 4:

* Nâng cao hiểu biết về **AWS Identity & Security**:  
  - Áp dụng **Cognito** để quản lý xác thực người dùng và quyền truy cập ứng dụng.  
  - Khám phá **AWS Organizations** cho quản trị multi-account với OU, SCP và billing tổng hợp.  
  - Cấu hình **AWS Identity Center (SSO)** cho truy cập đa tài khoản và ứng dụng.  
  - Thực hành mã hóa dữ liệu với **AWS KMS**, triển khai giải pháp encrypt-at-rest.  
  - Quan sát dashboard **AWS Security Hub** để nắm posture compliance và xử lý cảnh báo.  
  - Thử nghiệm **IAM Permission Boundaries** để giới hạn tối đa quyền của user và role.  

* Thực hành lab giúp củng cố các khái niệm: IAM Role & Condition, Permission Boundary, Security Hub, tag-based EC2 control, KMS encryption.  

* Áp dụng các khái niệm IAM nâng cao: **Trust Policies**, **Permission Policies**, **Condition Keys** để kiểm soát truy cập tinh vi.  

* Thực hiện phân tích chi phí compute, xác định khi nào **EC2** hoặc **Lambda** phù hợp với workload và giá cả.  

* Biên soạn và tổng hợp nội dung AWS/Cloud giúp nâng cao khả năng đọc hiểu, tổng hợp và truyền đạt kiến thức bảo mật đám mây.  


