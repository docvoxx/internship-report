---
title: "Tuần 1 Worklog"
date: ""
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu Tuần 1:
* Làm quen với các thành viên của chương trình **First Cloud Journey (FCJ)** và nắm rõ nội quy, quy định của đơn vị thực tập.
* Hiểu vững các khái niệm cốt lõi về điện toán đám mây và hệ sinh thái dịch vụ AWS, bao gồm Compute, Storage, Networking, Databases và Security.
* Thực hành tạo và quản lý tài khoản AWS Free Tier theo best practices: thiết lập IAM Users, Groups, Roles; hạn chế sử dụng tài khoản root; cấu hình Budgets để theo dõi chi phí.
* Làm việc song song với AWS Management Console và AWS CLI để quản lý tài nguyên, đồng thời xây dựng kỹ năng scripting cơ bản để tự động hóa.
* Học các chiến lược tối ưu chi phí như Spot Instances, AWS Pricing Calculator, AWS Budgets/Cost Explorer.
* Khám phá kiến trúc Serverless qua AWS Lambda, DynamoDB và sử dụng Hugo để build & deploy website tĩnh phục vụ workshop.
* Nghiên cứu và thực hành các thành phần mạng cơ bản của AWS bao gồm VPC, Subnets, Route Tables, Security Groups, NACLs, Internet Gateway, NAT Gateway, VPC Endpoints, VPC Flow Logs, VPN, Direct Connect và Elastic Load Balancing.

### Các nhiệm vụ thực hiện trong tuần:
| Thứ | Nhiệm vụ |Ngày bắt đầu |Ngày hoàn thành | Tài liệu tham khảo |
| --- | -------- | -------- | ------------ | ------------------- |
| 2 | - Học cách vẽ luồng hệ thống cloud bằng AWS architecture icons <br> - Học Module 01 về Cloud Computing: AWS overview, policies, services, AWS Support <br> - Tạo AWS Free Tier account, tạo Admin Group và Admin User <br> - Cài đặt & cấu hình AWS CLI <br> - Học cách gửi yêu cầu hỗ trợ AWS Support | 08/11/2025 | 08/11/2025 | <https://000001.awsstudygroup.com/> <br> https://000009.awsstudygroup.com/ |
| 3 | - Học viết Markdown và tạo website bằng Hugo <br> - Hoàn thành các bài thực hành Module 1 <br> - Nghiên cứu Spot Instances để tối ưu chi phí (~90% rẻ hơn nhưng có thể bị gián đoạn) <br> - Hiểu serverless (Lambda, DynamoDB) <br> - Dùng AWS Pricing Calculator để ước tính chi phí theo Region <br> - Ôn lại các dịch vụ mạng: VPC, Subnets, Route Tables, SG, NACLs, VPC Peering, Transit Gateway, VPN, Direct Connect, ELB | 08/12/2025 | 08/12/2025 | https://van-hoang-kha.github.io/ |
| 4 | - Thiết lập IAM User, Policies, Group và Role thay vì dùng root <br> - Cấu hình Budget/Cost Budget để theo dõi credits hàng tháng <br> - Ôn lại VPC: public/private subnets, Route Tables, IGW, NAT Gateway <br> - Học ENI và Elastic IP <br> - Nghiên cứu VPC Endpoints (Gateway vs Interface) <br> - So sánh Security Groups (stateful) và NACLs (stateless) <br> - Bật & xem VPC Flow Logs (CloudWatch / S3) <br> - Hiểu VPC Peering và các giới hạn thường gặp <br> - Học Transit Gateway và cách Attachments kết nối mạng <br> - Hoàn thành Module 02 — 01 | 10/09/2025 | 10/09/2025 | https://cloudjourney.awsstudygroup.com/ |
| 5 | - Tìm hiểu AWS Direct Connect (Dedicated & Hosted) <br>&emsp; + Use cases và mô hình kết nối <br> - Hiểu Site-to-Site VPN với Virtual Private Gateway & Customer Gateway <br> - Ôn lại Client VPN <br> - Nghiên cứu Elastic Load Balancing (ALB, NLB, CLB, Global LB) <br>&emsp; + Health checks, sticky sessions, access logs <br>&emsp; + Routing rules và target types <br> - Hoàn thành Module 02 - 03 | 11/09/2025 | 11/09/2025 | https://cloudjourney.awsstudygroup.com/ |
| 6 | - Tổng hợp các chủ đề chính: IAM, VPC, Subnets, Security, ELB, v.v. <br>&emsp; + Review kiến trúc và flow các dịch vụ <br> - Làm lab nâng cao về VPC networking <br>- Học Route 53 Resolver cho môi trường Hybrid DNS <br> - Cấu hình và kiểm thử VPC Peering | 12/09/2025 | 14/09/2025 | [My Notes on AWS Services](https://www.notion.so/i-n-to-n-m-m-y-26a4c2b6beb680beb5eaf9d9f48b8b00?source=copy_link) |

### Tuần 1 – Tổng kết học tập AWS

### 1. Kiến thức AWS Cốt lõi
- Nắm tổng quan về AWS và các nhóm dịch vụ chính:
  - Compute, Storage, Networking, Databases, Security…
- Hiểu sự khác nhau giữa:
  - **AWS Management Console** (giao diện web)
  - **AWS CLI** (command-line)
  - **AWS SDK** (truy cập lập trình)

### 2. Thiết lập tài khoản & Free Tier
- Tạo và cấu hình tài khoản AWS Free Tier.
- Cài đặt và thiết lập AWS CLI:
  - Access Key  
  - Secret Key  
  - Default Region  
- Thực hành quản lý tài nguyên qua **Console** và **CLI**.

### 3. Kinh nghiệm CLI
- Kiểm tra thông tin tài khoản và cấu hình CLI.
- Liệt kê các AWS Regions.
- Làm việc với EC2:
  - Xem danh sách instances
  - Tạo & quản lý key pairs
  - Kiểm tra các dịch vụ đang chạy
- Bắt đầu viết các script tự động hóa đơn giản.

### 4. IAM (Identity & Access Management)
- Tạo IAM Users, Groups và Roles.
- Gán Managed Policies hoặc Inline Policies.
- Thực hành đăng nhập bằng IAM User và chuyển Role.
- Hiểu lý do không nên dùng tài khoản root hàng ngày.

### 5. Quản lý chi phí & tối ưu
- Hiểu cách hoạt động của **Spot Instances**.
- Tạo Budgets và theo dõi Free Tier usage.
- Dùng AWS Pricing Calculator để so sánh chi phí giữa các Region.

### 6. Serverless & Công cụ Workshop
- Nắm cơ bản về Lambda, DynamoDB và Serverless.
- Thực hành dùng **Hugo** để build website tĩnh.

### 7. Networking Fundamentals
- Hiểu cấu trúc VPC.
- Phân biệt public/private subnets và học:
  - Route Tables  
  - Internet Gateway (IGW)  
  - NAT Gateway  
  - Elastic IP  
  - ENI  
- Tìm hiểu:
  - VPC Endpoints  
  - VPC Flow Logs  
  - Security Groups (stateful) vs NACLs (stateless)  
  - VPC Peering & Transit Gateway  
  - Site-to-Site VPN, Client VPN, Direct Connect  
  - Load Balancers: ALB, NLB, CLB, Global LB  

###Tự đánh giá – Tiến độ, Khó khăn và Kế hoạch tiếp theo
### Thế mạnh đã phát triển
  - Hiểu rõ các dịch vụ cơ bản của AWS.
  - Tự tin cấu hình tài khoản theo best practice của IAM.
  - Tăng khả năng hiểu và xử lý các thành phần mạng AWS.

### Khó khăn gặp phải
  - Ban đầu nhầm lẫn giữa CLI và SDK.
  - VPC (CIDR, subnets, NACLs, SG) gây khó hiểu lúc đầu.
  - Metric “EC2:Running Hours” không xuất hiện khi tạo Budget do chưa có dữ liệu sử dụng.
  - Tính toán chi phí mất thời gian vì chưa quen dịch vụ.
  - Các lab nâng cao (Peering, Hybrid DNS, Route 53 Resolver) phải làm nhiều lần mới hiểu.

### Kế hoạch cải thiện
  - Tiếp tục luyện CLI và networking labs.
  - Làm thêm bài tập liên quan đến chi phí và Spot Instances.
  - Đọc thêm tài liệu AWS để giảm nhầm lẫn.
  - Tự vẽ diagram và ghi chú sau mỗi lab phức tạp để ghi nhớ lâu hơn.
