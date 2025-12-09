---
title: "Blog 2"
date: ""
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

## [Blog Tin tức AWS](https://aws.amazon.com/blogs/aws/)

## **AWS Weekly Roundup: Kỷ niệm 10 năm Amazon Aurora, Amazon EC2 R8 instances, Amazon Bedrock và nhiều hơn nữa (25 tháng 8, 2025\)**

Bởi Betty Zheng (郑予彬) | vào 25/08/2025 trong | [Amazon Aurora](https://aws.amazon.com/blogs/aws/category/database/amazon-aurora/), [Amazon Bedrock](https://aws.amazon.com/blogs/aws/category/artificial-intelligence/amazon-machine-learning/amazon-bedrock/), [Amazon EC2](https://aws.amazon.com/blogs/aws/category/compute/amazon-ec2/), [Amazon OpenSearch Service](https://aws.amazon.com/blogs/aws/category/analytics/amazon-elasticsearch-service/), [Launch](https://aws.amazon.com/blogs/aws/category/news/launch/), [News](https://aws.amazon.com/blogs/aws/category/news/) | [Liên kết cố định](https://aws.amazon.com/blogs/aws/aws-weekly-roundup-amazon-aurora-10th-anniversary-amazon-ec2-r8-instances-amazon-bedrock-and-more-august-25-2025/) | [Bình luận](https://aws.amazon.com/blogs/aws/aws-weekly-roundup-amazon-aurora-10th-anniversary-amazon-ec2-r8-instances-amazon-bedrock-and-more-august-25-2025/#Comments) | [Chia sẻ](https://aws.amazon.com/blogs/aws/aws-weekly-roundup-amazon-aurora-10th-anniversary-amazon-ec2-r8-instances-amazon-bedrock-and-more-august-25-2025/#)

Khi tôi chuẩn bị cho bản tổng hợp tuần này, tôi không khỏi suy ngẫm về cách công nghệ cơ sở dữ liệu đã phát triển trong thập kỷ qua. Thật thú vị khi thấy những quyết định kiến trúc được đưa ra nhiều năm trước vẫn tiếp tục định hình cách chúng ta xây dựng các ứng dụng hiện đại. Tuần này mang đến một cột mốc đặc biệt, minh chứng hoàn hảo cho sự phát triển trong đổi mới cơ sở dữ liệu đám mây khi Amazon Aurora [kỷ niệm 10 năm đổi mới cơ sở dữ liệu](https://aws.amazon.com/blogs/aws/celebrating-10-years-of-amazon-aurora-innovation/?trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=el) .

Phó Chủ tịch Amazon Web Services (AWS) Swami Sivasubramanian đã chia sẻ trên LinkedIn về hành trình của ông với Amazon Aurora, gọi đây là “một trong những sản phẩm thú vị nhất” mà ông từng làm việc. Khi Aurora ra mắt vào năm 2015, nó đã thay đổi bối cảnh cơ sở dữ liệu bằng cách tách biệt phần tính toán và phần lưu trữ. Giờ đây, được hàng trăm nghìn khách hàng trên nhiều ngành tin tưởng, Aurora đã phát triển từ một cơ sở dữ liệu tương thích MySQL thành một nền tảng toàn diện với nhiều đổi mới như Aurora DSQL, khả năng serverless, mô hình giá I/O-Optimized, tích hợp zero-ETL, và hỗ trợ [AI tạo sinh](https://aws.amazon.com/generative-ai/?trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=el). Sự kiện kỷ niệm vào ngày 21 tháng 8 tuần trước đã nhấn mạnh quá trình chuyển đổi kéo dài cả thập kỷ này, tiếp tục đơn giản hóa việc mở rộng cơ sở dữ liệu cho khách hàng.

### **Các bản phát hành tuần trước**

Ngoài những lễ kỷ niệm truyền cảm hứng, đây là một số bản phát hành AWS đáng chú ý:

* [AWS Billing and Cost Management ra mắt Dashboards tùy chỉnh](https://aws.amazon.com/about-aws/whats-new/2025/08/aws-billing-cost-management-customizable-dashboards/?trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=el) — Tính năng mới này hợp nhất dữ liệu chi phí vào các bảng điều khiển trực quan với nhiều loại widget và tùy chọn trực quan hóa, kết hợp thông tin từ Cost Explorer, Savings Plans và báo cáo Reserved Instance, giúp các tổ chức theo dõi mô hình chi tiêu và chia sẻ báo cáo chi phí chuẩn hóa trên nhiều tài khoản.

* [Amazon Bedrock đơn giản hóa truy cập các mô hình open weight của OpenAI](https://aws.amazon.com/about-aws/whats-new/2025/08/amazon-bedrock-automatic-access-openai-open-weight-models/?trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=el) — AWS đã tinh gọn việc truy cập các mô hình open weight của OpenAI (gpt-oss-120b và gpt-oss-20b), khiến chúng tự động khả dụng cho tất cả người dùng mà không cần kích hoạt thủ công, đồng thời vẫn duy trì kiểm soát của quản trị viên thông qua chính sách IAM và service control policies.

* [Amazon Bedrock bổ sung hỗ trợ batch inference cho Claude Sonnet 4 và các mô hình GPT-OSS](https://aws.amazon.com/about-aws/whats-new/2025/08/amazon-bedrock-batch-inference-anthropic-claude-sonnet-4-openai-gpt-oss-models/?trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=el) — Tính năng này cung cấp xử lý bất đồng bộ cho nhiều yêu cầu suy luận với mức giá thấp hơn 50% so với suy luận on-demand, tối ưu hóa các tác vụ AI khối lượng lớn như phân tích tài liệu, tạo nội dung và trích xuất dữ liệu, đồng thời hỗ trợ theo dõi tiến độ qua Amazon CloudWatch metrics.

* [AWS ra mắt Amazon EC2 R8i và R8i-flex memory-optimized instances](https://aws.amazon.com/blogs/aws/best-performance-and-fastest-memory-with-the-new-amazon-ec2-r8i-and-r8i-flex-instances/) — Được trang bị bộ xử lý tùy chỉnh Intel Xeon 6, các instance mới này mang lại hiệu suất cao hơn đến 20% và băng thông bộ nhớ gấp 2,5 lần so với R7i, lý tưởng cho khối lượng công việc yêu cầu nhiều bộ nhớ như cơ sở dữ liệu và phân tích dữ liệu lớn. R8i-flex cung cấp thêm lợi ích tiết kiệm chi phí cho các ứng dụng không tận dụng tối đa tài nguyên tính toán.

* [Amazon S3 giới thiệu tính năng batch data verification](https://aws.amazon.com/about-aws/whats-new/2025/08/amazon-s3-verify-content-stored-datasets/) — Một khả năng mới trong S3 Batch Operations, cho phép xác minh hiệu quả hàng tỷ đối tượng bằng nhiều thuật toán checksum mà không cần tải xuống hay khôi phục dữ liệu, tạo báo cáo chi tiết về tính toàn vẹn để phục vụ tuân thủ và kiểm toán, bất kể lớp lưu trữ hay kích thước đối tượng.

### **Tin tức AWS khác**

Dưới đây là một số dự án và bài viết blog khác có thể bạn quan tâm:

* [Amazon ra mắt mô hình nền tảng DeepFleet dành cho phối hợp đa robot](https://www.amazon.science/blog/amazon-builds-first-foundation-model-for-multirobot-coordination/?trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=el) — Được huấn luyện trên hàng triệu giờ dữ liệu từ các trung tâm hoàn thiện và phân loại của Amazon, các mô hình tiên phong này dự đoán mô hình giao thông trong tương lai của đội robot, đại diện cho những mô hình nền tảng đầu tiên được thiết kế riêng cho việc phối hợp nhiều robot trong môi trường phức tạp.

* [Xây dựng Strands Agents chỉ với vài dòng code](https://builder.aws.com/content/310WYq1aRDMif9UgksR4drnHOh1/building-strands-agents-with-a-few-lines-of-code-agent-to-agent-a2a-communication/?trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=el) — Một bài blog mới trình bày cách xây dựng hệ thống AI đa tác tử với vài dòng code, cho phép các agent chuyên biệt cộng tác mượt mà, xử lý các quy trình phức tạp và chia sẻ thông tin qua các giao thức tiêu chuẩn, tạo ra hệ thống AI phân tán vượt ra ngoài khả năng của từng agent riêng lẻ.

* [AWS Security Incident Response giới thiệu tích hợp ITSM](https://aws.amazon.com/about-aws/whats-new/2025/08/aws-security-incident-response-itsm-integrations/?trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=el) — Các tích hợp mới với Jira và ServiceNow cung cấp khả năng đồng bộ hai chiều cho sự cố bảo mật, bình luận và tệp đính kèm, hợp lý hóa phản ứng sự cố đồng thời duy trì quy trình hiện có, với mã nguồn mở có sẵn trên GitHub để tùy chỉnh và mở rộng sang các nền tảng ITSM khác.

* [Tìm nguyên nhân gốc rễ bằng digital twin mạng và agentic AI](https://aws.amazon.com/blogs/database/beyond-correlation-finding-root-causes-using-a-network-digital-twin-graph-and-agentic-ai/?trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=el) — Một bài viết chi tiết cho thấy cách AWS hợp tác với NTT DOCOMO để xây dựng một network digital twin sử dụng cơ sở dữ liệu đồ thị và AI tự động, giúp nhà mạng vượt ra ngoài mức tương quan để xác định nguyên nhân thực sự của các sự cố mạng phức tạp, dự đoán sự cố tương lai và cải thiện độ tin cậy dịch vụ tổng thể.

### **Sự kiện AWS sắp tới**

Hãy đánh dấu lịch và đăng ký tham gia các sự kiện AWS sắp tới:

* [**AWS Summits**](https://aws.amazon.com/events/summits/?trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=el) — Tham gia các sự kiện trực tuyến và trực tiếp miễn phí, nơi cộng đồng điện toán đám mây gặp gỡ, kết nối và tìm hiểu về AWS. Đăng ký tại thành phố gần bạn: [Toronto](https://aws.amazon.com/events/summits/toronto/?trk=a0051fdc-5b89-46a6-acfd-4881a84205f8&utm_custom=a0051fdc-5b89-46a6-acfd-4881a84205f8&sc_channel=el) (4/9), [Los Angeles](https://aws.amazon.com/events/summits/los-angeles/?trk=94c10076-a44d-4e29-a4a2-9a2f8d5e0238&utm_custom=94c10076-a44d-4e29-a4a2-9a2f8d5e0238&sc_channel=el) (17/9), và [Bogotá](https://aws.amazon.com/es/events/summits/bogota/?utm_custom=258165ef-0951-435c-9dd0-3de2cde89563) (9/10).

* [AWS re:Invent 2025](https://reinvent.awsevents.com/?trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=ell) — Hội nghị thường niên lớn nhất sẽ diễn ra tại Las Vegas từ ngày 1–5/12. [Danh mục sự kiện](https://registration.awsevents.com/flow/awsevents/reinvent2025/eventcatalog/page/eventcatalog??trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=el) hiện đã có sẵn. Hãy đánh dấu lịch cho sự kiện không thể bỏ lỡ này của cộng đồng AWS.  
   	  
* [AWS Community Days](https://aws.amazon.com/events/community-day/?trk=e61dee65-4ce8-4738-84db-75305c9cd4fe&sc_channel=el&?trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=el) — Tham gia các hội nghị do cộng đồng tổ chức với các thảo luận kỹ thuật, workshop và phòng lab thực hành do các chuyên gia AWS và lãnh đạo ngành dẫn dắt: [Adria](https://awscommunityadria.com/) (5/9), [Baltic](https://awsbaltic.eu/) (10/9), [Aotearoa](https://aws-community-day.nz/inperson.html) (18/9), [Nam Phi](https://www.awscommunityday.co.za/) (20/9), [Bolivia](https://www.facebook.com/awscommunitydaybolivia/) (20/9), [Bồ Đào Nha](https://awscommunityday.pt/) (27/9).

Hãy tham gia [AWS Builder Center](https://builder.aws.com/) để học hỏi, xây dựng và kết nối với cộng đồng builder AWS. Xem tại đây để biết thêm các sự kiện dành cho nhà phát triển ([trực tiếp](https://aws.amazon.com/events/explore-aws-events/?trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=el) và [trực tuyến](https://aws.amazon.com/developer/events/?trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=el)).

Đó là tất cả cho tuần này. Hãy quay lại vào thứ Hai tuần sau để đọc thêm một bản [Weekly Roundup](https://aws.amazon.com/blogs/aws/tag/week-in-review/?trk=ba8b32c9-8088-419f-9258-82e9375ad130&sc_channel=el) khác\!

– [Betty](http://www.linkedin.com/in/zhengyubin714)

**Cập nhật ngày 9/9/2025** — Đã chỉnh sửa hai liên kết tin tức liên quan đến EC2 R8i và tính năng xác minh dữ liệu hàng loạt Amazon S3.

## **THẺ: [Review trong tuần](https://aws.amazon.com/blogs/aws/tag/week-in-review/)**

| Betty Zheng (郑予彬) Betty Zheng là Senior Developer Advocate tại AWS, tập trung vào việc tạo nội dung hướng đến nhà phát triển trong các lĩnh vực Cloud Native, Cloud Security và Generative AI. Với hơn 20 năm kinh nghiệm trong ngành CNTT-TT và 18 năm làm kiến trúc sư ứng dụng cũng như chuyên gia hạ tầng đám mây, cô tích cực tham gia vào cộng đồng nhà phát triển Trung Quốc và luôn tận tâm giúp các nhà phát triển hiểu rõ công nghệ, đồng thời biến ý tưởng của họ thành hiện thực.  |
| :---- |

## 

