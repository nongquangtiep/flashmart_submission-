# Giải trình: COUNT(o.order_id) vs COUNT(*)

Hàm COUNT(*) đếm toàn bộ số dòng được sinh ra trong mỗi nhóm GROUP BY. Khi thực hiện LEFT JOIN với bảng Orders, khách hàng chưa từng mua hàng (như Charlie) vẫn tạo ra 1 dòng với các trường của Orders mang giá trị NULL. Do đó, nếu dùng COUNT(*), kết quả sẽ trả về 1 dòng thay vì 0, dẫn tới sai lệch dữ liệu nghiệp vụ.

Ngược lại, hàm COUNT(o.order_id) chỉ đếm các giá trị khác NULL trên cột khóa chính của bảng phụ. Đối với khách hàng chưa có đơn hàng, giá trị o.order_id là NULL nên hàm trả về chính xác 0 đơn hàng.