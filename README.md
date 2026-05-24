# BÁO CÁO ĐỒ ÁN THUẬT TOÁN SORT

## THÔNG TIN CHUNG
- **Tên môn học:** Cấu trúc Dữ liệu và Giải thuật
- **Thời gian học:** Học kỳ 2 - 2025-2026
- **Giáo viên giảng dạy, hướng dẫn:**
  1. Phạm Trọng Nghĩa
  2. Nguyễn Thanh Tình
  3. Huỳnh Lâm Hải Đăng
  4. Nguyễn Ngọc Đức
- **Danh sách sinh viên nhóm thực hiện đồ án:**
  1. Nguyễn An Thạch MSSV: 25120435
  2. Trương Công Nhật MSSV: 25120405
  3. Trần Nhất Phong MSSV: 25120

---

## 1. PHÂN TÍCH LẦN CHẠY ĐẦU TIÊN (LẦN 1)

### 1.1. Bài A - Integer Sort

### 1.2. Bài B - Lexicographic Sort

### 1.3. Bài C - Length-aware Lexicographic String Sort 
- **Đặc điểm bài toán:** Ưu tiên sắp xếp theo độ dài chuỗi trước, nếu độ dài bằng nhau mới xét thứ tự từ điển. Giới hạn  (1s, 256 MB).
- **Thuật toán cài đặt tốt nhất ở lần 1:**Bài C sử dụng thuật toán Randomized QuickSort kết hợp sử dụng mảng con trỏ.
- **Các phương thức tối ưu hóa:**
  - Tối ưu hoá việc chọn pivot: Sử dụng hàm rand() để tiến hành chọn pivot 1 cách ngẫu nhiên, theo mặt xác suất toán học gần như loại bỏ hoàn toàn rơi vào trường hợp tệ nhất.
  - Tối ưu hoán vị: Đổi địa chỉ con trỏ (chi phí O(1)) thay vì sao chép từng ký tự của chuỗi (chi phí O(L)).
  - Kỹ thuật Thoát sớm: Hàm so sánh trả về kết quả ngay khi thấy độ dài chuỗi khác nhau, không cần duyệt tiếp các ký tự.
  - Fast I/O: Sử dụng ios_base::sync_with_stdio(false); và cin.tie(NULL); để tăng tốc độ đọc/ghi dữ liệu tối đa.
- **Lý giải sự lựa chọn:** [Giải thích cách Custom Comparator hoạt động. Ví dụ: "Thuật toán này chỉ đánh giá các ký tự bên trong khi hai chuỗi có cùng độ dài, giúp cắt giảm đáng kể số lần gọi hàm so sánh chuỗi tốn kém, từ đó đáp ứng được Time Limit 1s."]

---

## 2. CÁCH THỨC SINH TEST CASE (`test_gen.cpp`)

### 2.1. Cấu trúc và logic sinh test case
[Mô tả cách bạn viết mã trong `test_gen.cpp` để tạo ra dữ liệu. Ví dụ: Dữ liệu được sinh ngẫu nhiên hay có quy luật? Mảng giảm dần, đồ thị dầy đặc (dense graph), v.v.]

### 2.2. Thuật toán mục tiêu
- **Các thuật toán mục tiêu:** [Liệt kê các thuật toán mà bộ test này nhắm tới để làm tăng thời gian chạy, ví dụ: QuickSort với pivot cố định, thuật toán ngây thơ (Naive) có độ phức tạp O(N^2)...]

### 2.3. Lý giải việc chọn thuật toán và tác dụng của Test
- **Lý do chọn thuật toán mục tiêu:** [Tại sao lại nhắm vào thuật toán này? (Ví dụ: Thuật toán này có điểm yếu dễ bị khai thác ở Worst-case).]
- **Tại sao test case lại làm tăng thời gian chạy:** [Giải thích cơ chế. Ví dụ: "Vì test case cố tình tạo ra mảng đã được sắp xếp ngược, khiến cho QuickSort (chọn pivot là phần tử cuối) liên tục chia mảng thành 1 và N-1 phần tử, đẩy độ phức tạp lên O(N^2) làm tăng thời gian chạy đáng kể."]

---

## 3. PHÂN TÍCH LẦN CHẠY THỨ HAI (LẦN 2)

### 3.1. Thuật toán và phương thức tối ưu hóa
- **Thuật toán cài đặt tốt nhất:** [Tên thuật toán được dùng ở lần 2]
- **Các phương thức tối ưu hóa liên quan:** - [Liệt kê các kỹ thuật tối ưu mới được áp dụng]

### 3.2. Cách thức tiếp tục tối ưu so với Lần 1
[Giải thích quá trình nâng cấp. Ở lần 1 thuật toán bị nghẽn (bottleneck) ở đâu? Bạn đã làm thế nào để khắc phục nó ở lần 2? (Ví dụ: Thay vì dùng mảng 2 chiều tốn bộ nhớ, đã chuyển sang dùng danh sách kề; hoặc áp dụng Bitwise operations, thêm pragma GCC optimize...)]
