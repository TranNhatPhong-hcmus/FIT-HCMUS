# BÁO CÁO ĐỒ ÁN THUẬT TOÁN SORT

## THÔNG TIN CHUNG
- **Tên môn học:** Cấu trúc Dữ liệu và Giải thuật
- **Thời gian học:** Học kỳ 2 - 2025-2026
- **Giáo viên giảng dạy, hướng dẫn:**
  1. Huỳnh Lâm Hải Đăng
  2. Phạm Trọng Nghĩa
  3. Nguyễn Thanh Tình 
  4. Nguyễn Ngọc Đức
- **Danh sách sinh viên nhóm thực hiện đồ án:**
  1. Nguyễn An Thạch MSSV: 25120435
  2. Trương Công Nhật MSSV: 25120405
  3. Trần Nhất Phong MSSV: 25120413

---

## 1. PHÂN TÍCH LẦN CHẠY ĐẦU TIÊN (LẦN 1)

### 1.1. Bài A - Integer Sort

### 1.2. Bài B - Lexicographic Sort

- **Đặc điểm bài toán:** Sắp xếp chuỗi đơn thuần theo thứ tự từ điển.
  Giới hạn thời gian rộng (10s), bộ nhớ lớn (1024 MB), số lượng chuỗi lớn N <= 10000, độ dài 10 - 100.
- **Thuật toán cài đặt:** Kết hợp Bucket Sort (phân nhóm theo 2 ký tự đầu) và Iterative
  QuickSort (sắp xếp không đệ quy) có kết hợp với Insertion Sort. Quản lý hoàn toàn thông qua mảng chỉ số (idx).
- **Các phương thức tối ưu hóa:**
  - Phân nhóm (Bucket Sort): Tiền xử lý bằng cách chia các chuỗi vào 676 bucket dựa trên giá trị của 2 ký tự đầu tiên. Điều này giúp chia nhỏ mảng $10^5$ phần tử thành các mảng rất nhỏ để xử lý độc lập, giảm thiểu đáng kể số lần gọi hàm sắp xếp
  - Quản lý bộ nhớ gián tiếp: Thuật toán không bao giờ hoán vị trực tiếp các chuỗi string. Thay vào đó, nó hoán đổi các số nguyên trong mảng idx có chi phí $O(1)$. Các thao tác chèn cũng chỉ làm việc trên mảng idx
  - Khử đệ quy (Iterative QuickSort): Sử dụng hai mảng stack_left và stack_right giả lập bộ nhớ stack để khử đệ quy. Kỹ thuật này loại bỏ chi phí gọi hàm (overhead) và rủi ro tràn bộ nhớ stack.
  - Tối ưu chọn Pivot (Median-of-three): Chốt (pivot) được chọn ở vị trí giữa và được sắp xếp trước với hai phần tử đầu/cuối của mảng con. Điều này triệt tiêu rủi ro mảng bị phân hoạch mất cân bằng.
  - Tối ưu mảng nhỏ: Khi mảng con có kích thước $\le 15$, thuật toán tự động ngắt QuickSort và chuyển sang Insertion Sort  vì thuật toán này chạy nhanh hơn rất nhiều do chi phí hằng số thấp trên các mảng nhỏ.
  - Fast I/O: Tăng tốc I/O qua ios::sync_with_stdio(false) và cin.tie(nullptr).

- **Lý giải lựa chọn thuật toán:**
  - Việc phân nhóm 2 ký tự đầu hoạt động như một bước radix sort, triệt tiêu việc phải so sánh sâu toàn bộ $10^5$ chuỗi. Thao tác hoán vị gián tiếp bằng mảng chỉ số idx loại bỏ hoàn toàn "nút thắt cổ chai" do việc cấp phát và di chuyển bộ nhớ của thư viện <string>. Việc tự triển khai hệ thống quản lý stack cho QuickSort đẩy tốc độ và sự ổn định của chương trình lên mức tối đa để vượt qua các bộ test hiệu năng khắt khe.

### 1.3. Bài C - Length-aware Lexicographic String Sort 
- **Đặc điểm bài toán:** Ưu tiên sắp xếp theo độ dài chuỗi trước, nếu độ dài bằng nhau mới xét thứ tự từ điển. Giới hạn  (1s, 256 MB).
- **Thuật toán cài đặt tốt nhất ở lần 1:** Bài C sử dụng thuật toán Randomized QuickSort kết hợp sử dụng mảng con trỏ.
- **Các phương thức tối ưu hóa:**
  - Tối ưu hoá việc chọn pivot: Sử dụng hàm rand() để tiến hành chọn pivot 1 cách ngẫu nhiên, theo mặt xác suất toán học gần như loại bỏ hoàn toàn rơi vào trường hợp tệ nhất.
  - Tối ưu hoán vị: Đổi địa chỉ con trỏ (chi phí O(1)) thay vì sao chép từng ký tự của chuỗi (chi phí O(L)).
  - Kỹ thuật Thoát sớm: Hàm so sánh trả về kết quả ngay khi thấy độ dài chuỗi khác nhau, không cần duyệt tiếp các ký tự.
  - Fast I/O: Sử dụng ios_base::sync_with_stdio(false); và cin.tie(NULL); để tăng tốc độ đọc/ghi dữ liệu tối đa.
- **Lý giải lựa chọn thuật toán:**
  - Về việc chọn thuật toán Randomize QuickSort: Bằng cách dùng hàm rand() để chọn một vị trí ngẫu nhiên làm chốt, bạn dựa vào xác suất toán học để chia đều mảng. Xác suất để rand() liên tục bốc trúng phần tử tệ nhất trong hàng chục ngàn lần lặp là vô cùng nhỏ (gần như bằng 0). Nhờ đó, thời gian chạy thực tế luôn được giữ ổn định ở mức $O(N \log N)$.

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
