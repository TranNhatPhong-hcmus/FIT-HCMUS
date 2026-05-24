# BÁO CÁO ĐỒ ÁN THUẬT TOÁN SORT

## THÔNG TIN CHUNG
- **Tên môn học:** Cấu trúc Dữ liệu và Giải thuật
- **Thời gian học:** Học kỳ 2 - 2025-2026
- **Họ và tên sinh viên:** Nguyễn An Thạch
- **MSSV:** 25120435

---

## 1. PHÂN TÍCH LẦN CHẠY ĐẦU TIÊN (LẦN 1)

### 1.1. Thuật toán và phương thức tối ưu hóa
- **Thuật toán cài đặt tốt nhất:** [Tên thuật toán, ví dụ: Merge Sort, Dijkstra...]
- **Các phương thức tối ưu hóa liên quan:** - [Liệt kê phương thức 1, ví dụ: Sử dụng mảng phụ thay vì cấp phát động liên tục]
  - [Liệt kê phương thức 2]

### 1.2. Lý giải sự lựa chọn
[Giải thích chi tiết tại sao phương pháp này lại mang lại kết quả tốt nhất trong TẤT CẢ các cách bạn đã thử cài đặt ở lần 1. Có thể đề cập đến độ phức tạp thời gian/không gian (Time/Space Complexity), hoặc cách nó xử lý tốt dữ liệu đầu vào cụ thể.]

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
