---
title: "Tuần 9 Worklog"
date: ""
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:

- Tiếp tục phát triển hệ thống gợi ý cá nhân hóa.  
- Liên tục tinh chỉnh dữ liệu đầu vào và xử lý các vấn đề phát sinh trong quá trình huấn luyện.

### Trọng tâm trong tuần:

| Ngày   | Trọng tâm                                                                                                                                                        | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo            |
| :---- | :----------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :------------------- |
| **2** | **Thiết lập mô hình ban đầu:**<br>- Cấu hình khung thuật toán<br>- Tải bộ dữ liệu ban đầu để xử lý<br>- Bắt đầu các quy trình huấn luyện sơ bộ | 10/11/2025 | 11/11/2025      | [AWS Personalize Docs](https://docs.aws.amazon.com/personalize/) |
| **3** | Xem xét kết quả đầu ra ban đầu và điều tra các bất thường hoặc hành vi không mong đợi | 12/11/2025 | 12/11/2025      |                      |
| **4** | **Tinh chỉnh dữ liệu:**<br>- Thêm các trường dữ liệu bổ sung<br>- Làm sạch và đồng bộ dữ liệu<br>- Lặp lại quy trình huấn luyện với dữ liệu đã chỉnh sửa | 12/11/2025 | 13/11/2025      |                      |
| **5** | Đánh giá hiệu suất mô hình sau khi cập nhật và phân tích các biến đổi trong chỉ số | 14/11/2025 | 14/11/2025      |                      |
| **6** | Quan sát lặp lại và lên kế hoạch cho các bước tinh chỉnh tiếp theo |            |                 |                      |

---

### Nhận xét tuần 9: Đối mặt với thách thức dữ liệu và huấn luyện

Tuần này nhấn mạnh các thách thức thực tế khi xây dựng hệ thống gợi ý và làm việc trong môi trường dữ liệu hạn chế:

- **Tín hiệu tương tác hạn chế:**  
  Bộ dữ liệu chủ yếu theo dõi các hành động hoàn tất ("Bookings"), thiếu các tín hiệu trung gian như "Views" hay "Clicks". Sự hạn chế này giới hạn khả năng hệ thống suy luận sở thích người dùng, thể hiện qua các điểm đánh giá chỉ ở mức vừa phải.

- **Giới hạn xác thực:**  
  Thiếu giao diện front-end hoàn chỉnh, việc xác thực thực tế vẫn mang tính lý thuyết. Hiện tại đánh giá dựa trên các chỉ số định lượng thay vì kiểm tra trực quan, trực giác.

- **Độ nhạy của pipeline với thay đổi schema:**  
  Khi thêm thuộc tính dữ liệu mới, cần điều chỉnh lại pipeline tiền xử lý. Mỗi thay đổi yêu cầu làm sạch, ánh xạ lại và huấn luyện lại, cho thấy tính nhạy cảm của workflow đầu-cuối.

- **Bài học chính:**  
  Dù các công cụ đám mây hỗ trợ quản lý dữ liệu và huấn luyện mô hình, những bài học quan trọng là về **quy trình**: đảm bảo dữ liệu đầy đủ, duy trì pipeline linh hoạt, và quản lý cẩn thận các vòng huấn luyện lặp lại.
