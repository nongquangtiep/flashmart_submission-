# AI Prompt Log - Phân tích truy vấn SQL

## Prompt 1: Cơ chế mặc định của từ khóa JOIN
- **Câu hỏi:** Trong MySQL, mặc định từ khóa JOIN khi không ghi rõ LEFT hay RIGHT sẽ hoạt động như thế nào?
- **Tóm tắt trả lời:** Mặc định là INNER JOIN (phép giao). Chỉ giữ lại các bản ghi có khóa khớp ở cả hai bảng, loại bỏ các bản ghi không có liên kết ở bảng còn lại.

## Prompt 2: Bẫy hàm COUNT() khi kết hợp với LEFT JOIN
- **Câu hỏi:** Tại sao dùng LEFT JOIN để đếm đơn hàng của khách hàng lại phải dùng COUNT(order_id) thay vì COUNT(*)?
- **Tóm tắt trả lời:** COUNT(*) đếm cả dòng chứa NULL do LEFT JOIN sinh ra (ra kết quả 1). COUNT(order_id) bỏ qua NULL và trả về 0 cho khách hàng chưa có đơn.

## Prompt 3: Cơ chế Optimizer của MySQL cho lệnh JOIN
- **Câu hỏi:** MySQL tối ưu hóa các lệnh JOIN như thế nào qua thuật toán Nested-Loop Join và Hash Join?
- **Tóm tắt trả lời:** Với bảng có đánh index, MySQL dùng Index Nested-Loop Join (INLJ). Với bảng không có index hoặc từ MySQL 8.0.18 trở đi, optimizer ưu tiên Hash Join để quét nhanh trong bộ nhớ thay vì Block Nested-Loop (BNL).