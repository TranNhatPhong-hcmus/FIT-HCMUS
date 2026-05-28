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
- **Đặc điểm bài toán:** Yêu cầu sắp xếp một dãy gồm N số nguyên. Giới hạn (10s,1024MB) , 1 <= N <= 1e5 , giá trị −2^31≤ x ≤ 2^31−1 .
- **Thuật toán cài đặt tốt nhất ở lần 1:** Thuật toán Quick Sort phiên bản Đệ quy kết hợp kỹ thuật Median-of-Three và Insertion Sort.
- **Các phương thức tối ưu hóa:**
  - Tối ưu hóa việc chọn pivot : Lấy trung vị của 3 phần tử (Đầu, Giữa, Cuối) để làm chốt. Kỹ thuật này giúp thuật toán né được trường hợp xấu nhất O(N^2) khi đối mặt với các test case mảng đã được sắp xếp sẵn hoặc sắp xếp giảm dần.
  - Kỹ thuật Ngưỡng giới hạn : Thiết lập một ngưỡng an toàn (`right - left <= 15`). Khi mảng được chẻ nhỏ xuống dưới 15 phần tử, thuật toán tự động dừng gọi đệ quy và chuyển sang dùng Insertion Sort. Với các mảng nhỏ, Insertion Sort vượt trội hơn hẳn Quick Sort do hằng số tính toán cực kỳ thấp.
  - Fast I/O: Sử dụng `ios::sync_with_stdio(false);` và `cin.tie(nullptr);` để mở khóa tốc độ đọc/ghi dữ liệu tối đa của C++.
- **Lý giải lựa chọn thuật toán:**
  - Về việc chọn Quick Sort Đệ quy kết hợp Threshold: Bản code này ưu tiên sự cân bằng giữa tính dễ đọc và hiệu năng. Thay vì để cây đệ quy đâm rễ quá sâu gây tốn bộ nhớ Stack, thuật toán đã chủ động cắt tỉa toàn bộ các nhánh lá (những mảng con có kích thước <= 15). Việc kết hợp giữa khả năng phân hoạch mảng lớn xuất sắc của Quick Sort và tốc độ "vét đáy" nhanh gọn của Insertion Sort tạo ra một phiên bản lai ổn định, giúp giữ vững thời gian chạy thực tế ở mức O(N log N).
### 1.2. Bài B - Lexicographic Sort

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
  - 

---

## 2. CÁCH THỨC SINH TEST CASE (`test_gen.cpp`)

### 2.1. Cấu trúc và logic sinh test case


**Bài A**
1.  **Test 1 :** Mảng ngẫu nhiên hoàn toàn, các giá trị được phân phối đều từ âm vô cùng `-2147483648` đến dương vô cùng `2147483647`.
2.  **Test 2 :** Mảng có cấu trúc tăng dần các số chẵn từ đầu đến giữa mảng, và giảm dần từ giữa về cuối mảng.
3.  **Test 3 :** Mảng được sinh thông qua hàm đệ quy `generate_anti_merge()`, cố tình sắp xếp đan xen các phần tử chẵn/lẻ ở mọi phân đoạn để tối đa hóa số lần hoán đổi chéo.
4.  **Test 4 :** Mảng đã được sắp xếp tăng dần tuyệt đối .
5.  **Test 5 :** Mảng chứa cực kỳ nhiều giá trị trùng lặp, chỉ xoay vòng lặp lại ngẫu nhiên đúng 3 giá trị: `INT_MIN`, `0`, và `INT_MAX`.

### 2.2. Thuật toán mục tiêu
**Bài A**
-   **Quick Sort cơ bản :** Sử dụng chốt là phần tử đầu, phần tử cuối, hoặc phần tử ở chính giữa.
-   **Quick Sort thiếu tối ưu:** Các phiên bản không có cơ chế phân hoạch 3 ngã .
-   **Merge Sort:** Thuật toán nổi tiếng với sự ổn định.
-   **Heap Sort:** Thuật toán dựa trên cấu trúc cây nhị phân.

### 2.3. Lý giải việc chọn thuật toán và tác dụng của Test

**Bài A**
-   **Tác dụng của Test 1 :** Không mang tính chất gài bẫy. Test này đóng vai trò làm thước đo chuẩn để đánh giá tốc độ thực tế  của mọi thuật toán trong điều kiện dữ liệu lý tưởng nhất.
-   **Tác dụng của Test 2 :** Nhắm vào các phiên bản **Quick Sort chọn chốt ở giữa** hoặc các chiến lược chọn chốt thiếu ổn định. Cấu trúc mảng tăng dần rồi giảm dần tạo ra các phân hoạch mất cân bằng đáng kể trong nhiều bước đệ quy, khiến Quick Sort khó chia mảng thành hai nửa đều nhau như trên dữ liệu ngẫu nhiên. Điều này làm số lần gọi đệ quy và chi phí phân hoạch tăng lên rõ rệt, từ đó làm suy giảm hiệu năng thực tế của thuật toán.
-   **Tác dụng của Test 3 :** Nhắm vào **Merge Sort**. Mảng được sinh bằng hàm đệ quy `generate_anti_merge()`, chia xen kẽ các phần tử vào hai nửa con ở mọi tầng đệ quy. Cấu trúc này khiến quá trình `merge` ở mỗi mức phải thực hiện gần như tối đa số phép so sánh giữa hai mảng con, làm tăng đáng kể hằng số thời gian thực thi của Merge Sort.

-   **Tác dụng của Test 4 :**
    -   Nhắm vào **Quick Sort chọn chốt ở đầu hoặc cuối**: Với mảng đã được sắp xếp tăng dần hoàn toàn, các phiên bản Quick Sort kiểu này sẽ liên tục chia mảng thành hai phần có kích thước `0` và `N-1`, khiến cây đệ quy trở nên cực kỳ mất cân bằng và đẩy độ phức tạp lên gần `O(N^2)`.
    -   Đồng thời tạo áp lực lên **Heap Sort**: Khi xây dựng Max-Heap từ mảng tăng dần, nhiều phần tử nhỏ nằm gần phía trên cây sẽ phải thực hiện các thao tác `sift-down` dài để khôi phục cấu trúc Heap, làm tăng chi phí thực thi thực tế.

-   **Tác dụng của Test 5 :** Nhắm vào các phiên bản **Quick Sort không sử dụng phân hoạch 3 ngã **. Khi mảng chứa số lượng cực lớn các giá trị trùng lặp, thuật toán sẽ liên tục thực hiện nhiều phép so sánh và hoán đổi không cần thiết giữa các phần tử bằng nhau. Điều này làm giảm hiệu quả phân hoạch, gia tăng độ sâu đệ quy và khiến thời gian thực thi suy giảm đáng kể.
---

## 3. PHÂN TÍCH LẦN CHẠY THỨ HAI (LẦN 2)

### 3.1. Thuật toán và phương thức tối ưu hóa
**Bài A**

- **Thuật toán cài đặt tốt nhất:** IntroSort tối ưu hóa thủ công .

- **Các phương thức tối ưu hóa liên quan:**
    - Chuyển từ Quick Sort thuần sang **IntroSort** để tránh trường hợp xấu `O(N^2)`.
    - Áp dụng **Heap Sort fallback** khi độ sâu đệ quy vượt giới hạn.
    - Sử dụng **Median-of-Three Pivot Selection** để chọn chốt ổn định hơn.
    - Thay phân hoạch kiểu cũ bằng **Hoare Partition** nhằm giảm số phép hoán đổi.
    - Áp dụng **Tail Recursion Optimization**: luôn đệ quy vào đoạn nhỏ hơn trước để giảm số lời gọi hàm và độ sâu stack.
    - Tăng ngưỡng chuyển sang **Insertion Sort** từ `15` lên `24` để tối ưu cho các đoạn nhỏ.
    - Thực hiện **Final Insertion Sort** trên toàn mảng sau khi phân hoạch gần hoàn tất nhằm tận dụng tính chất “gần được sắp xếp”.
    - Sử dụng `inline` cho các hàm nhỏ (`swap_`, `insertion_sort`, `sift_down`) để giảm chi phí gọi hàm.
    - Dùng `__lg(n)` thay cho `log2(n)` để tính giới hạn độ sâu nhanh hơn.

### 3.2. Cách thức tiếp tục tối ưu so với Lần 1
**Bài A**

Ở lần chạy đầu tiên, thuật toán sử dụng Quick Sort kết hợp Insertion Sort cho các đoạn nhỏ. Dù đã dùng Median-of-Three để chọn chốt, thuật toán vẫn tồn tại một số điểm nghẽn hiệu năng:

- Đệ quy trên cả hai nhánh làm tăng số lượng function call và gây áp lực lên stack.
- Partition kiểu cũ tạo ra nhiều phép hoán đổi không cần thiết.
- Quick Sort thuần vẫn có nguy cơ gặp trường hợp phân hoạch xấu trên các test được thiết kế đặc biệt.
- Insertion Sort được gọi nhiều lần trên các đoạn nhỏ riêng lẻ, chưa tận dụng được tính chất “gần sorted” của toàn bộ mảng ở giai đoạn cuối.

Ở lần tối ưu thứ hai, các điểm nghẽn trên được xử lý bằng cách chuyển sang mô hình IntroSort:

- Khi độ sâu đệ quy vượt ngưỡng `2 * __lg(n)`, thuật toán tự động chuyển sang Heap Sort để bảo đảm độ phức tạp xấu nhất chỉ còn `O(N log N)`.
- Tail Recursion Optimization giúp giảm mạnh số lời gọi hàm đệ quy.
- Hoare Partition giảm số lần swap và cải thiện locality của cache CPU.
- Final Insertion Sort được thực hiện đúng một lần ở cuối, giúp tối ưu mạnh trên các đoạn đã gần có thứ tự.
- Các hàm nhỏ được `inline` để giảm overhead ở mức instruction-level.


