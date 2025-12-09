---
title: "Tuần 5 Worklog"
date: ""
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

* Nắm vững các nguyên tắc cơ bản về cơ sở dữ liệu và phân biệt giữa **OLTP** và **OLAP**.  
* Khám phá và thực hành với các dịch vụ cơ sở dữ liệu AWS: **Amazon RDS**, **Amazon Redshift**, và **Amazon ElastiCache**.  
* Nâng cao kỹ năng **SQL**, từ các lệnh cơ bản đến các kỹ thuật truy vấn nâng cao.  
* Tìm hiểu các best practice cho việc triển khai, quản lý và tối ưu cơ sở dữ liệu trên AWS.  
* Kết hợp kiến thức lý thuyết về cơ sở dữ liệu với thực tiễn triển khai trên cloud.

### Công việc trong tuần:

| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                            |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ------------------------------------------- |
| 2   | - Ôn tập các khái niệm cơ bản về **cơ sở dữ liệu**: <br> &emsp; + Thành phần chính: Database, Session, Primary/Foreign Keys <br> &emsp; + Indexing, Partitioning, Execution Plans, Buffer, Logs <br> - So sánh **RDBMS** và **NoSQL** <br> - Hiểu sự khác biệt và ứng dụng của **OLTP vs OLAP** | 06/10/2025 | 06/10/2025      | [YouTube - Database Concepts](https://www.youtube.com/watch?v=OOD2RwWuLRw&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=217) |
| 3   | - Khám phá **Amazon Redshift** và **Amazon ElastiCache**: <br> &emsp; + Redshift: lưu trữ theo cột, kiến trúc MPP, leader & compute nodes, Redshift Spectrum, transient clusters, tối ưu chi phí <br> &emsp; + ElastiCache: Redis & Memcached, caching patterns, auto-failover <br> - Thực hành lab: **Lab 5 – RDS**, **Lab 43 – DMS & SCT** (thử nghiệm workflow di chuyển dữ liệu) | 07/10/2025 | 07/10/2025      | [W3Schools SQL](https://www.w3schools.com/sql/default.asp) <br> [Amazon Redshift Docs](https://docs.aws.amazon.com/redshift/) <br> [Database Internals (book)](https://www.amazon.com/Database-Internals-Deep-Distributed-Systems/dp/1492040347) |
| 4   | - Củng cố kỹ năng **SQL cơ bản**: <br> &emsp; + SELECT, INSERT, UPDATE, DELETE <br> &emsp; + JOIN, GROUP BY, ORDER BY <br> &emsp; + Thực hành truy vấn trên môi trường sandbox/test | 08/10/2025 | 08/10/2025      | [W3Schools SQL](https://www.w3schools.com/sql/default.asp) |
| 5   | - Thực hành SQL nâng cao: <br> &emsp; + Subqueries, Aggregate Functions, Constraints <br> &emsp; + Kỹ thuật tối ưu truy vấn và sử dụng hiệu quả primary/foreign keys | 09/10/2025 | 09/10/2025      | [W3Schools SQL](https://www.w3schools.com/sql/default.asp) |
| 6   | - Áp dụng kiến thức trên **Amazon RDS**: <br> &emsp; + Tạo và cấu hình RDS instances <br> &emsp; + Kết nối cơ sở dữ liệu, thực hiện truy vấn, quản lý dữ liệu <br> &emsp; + Thực hiện backup, snapshot, restore <br> - Tổng hợp kiến thức về dịch vụ cơ sở dữ liệu AWS và tích hợp trong các kịch bản thực tế | 10/10/2025 | 10/10/2025      | [Amazon RDS Doc](https://docs.aws.amazon.com/rds/) |

### Thành tựu tuần 5:

* Kiến thức cơ bản về cơ sở dữ liệu:  
  - Các thành phần: Database, Session, Index, Partition, Execution Plan, Buffer, Logs  
  - Phân biệt **RDBMS** và **NoSQL**  
  - Hiểu rõ sự khác biệt và ứng dụng của **OLTP** và **OLAP**

* Kinh nghiệm thực hành với các dịch vụ cơ sở dữ liệu AWS:  
  - **Amazon RDS** – dịch vụ quản lý cơ sở dữ liệu quan hệ  
  - **Amazon Redshift** – kho dữ liệu MPP dạng cột cho workloads OLAP  
  - **Amazon ElastiCache** – lớp caching giảm tải cho cơ sở dữ liệu  

* Hoàn thành các lab:  
  - **Lab 5 – RDS**: tạo instance, kết nối, thao tác cơ sở dữ liệu, backup/restore  
  - **Redshift lab**: khám phá tổ chức dữ liệu và lưu trữ theo cột  
  - **Lab 43 – DMS & SCT**: thử nghiệm workflow di chuyển dữ liệu và xử lý lỗi  

* Nâng cao kỹ năng SQL:  
  - CRUD: SELECT, INSERT, UPDATE, DELETE  
  - Truy vấn phức tạp: JOIN, GROUP BY, ORDER BY, Subqueries, Aggregate Functions, Constraints  
  - Tối ưu truy vấn và sử dụng key hiệu quả  

* Kết hợp kiến thức lý thuyết với triển khai thực tế trên AWS, lên kế hoạch kiến trúc cơ sở dữ liệu với RDS, Redshift và ElastiCache.  

* Nâng cao khả năng tổng hợp, áp dụng kiến thức cơ sở dữ liệu vào các dự án thực tế trên AWS.
