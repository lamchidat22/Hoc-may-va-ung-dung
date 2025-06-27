## Lab 4 - Phân Vùng Ảnh

* Sinh viên thực hiện: Bùi Lâm Chí Đạt
* MSSV: 207CT27720
* Môn học: Nhập môn Xử lý ảnh số
* Giảng viên: Đỗ Hữu Quân

## Giới thiệu

Bài Lab 4 này tập trung vào việc thực hiện các thao tác xử lý ảnh cơ bản trong lĩnh vực phân đoạn ảnh (Image Segmentation) và biến đổi hình học (Geometric Transformation). Các kỹ thuật này đóng vai trò quan trọng trong việc trích xuất thông tin, nhận dạng đối tượng và chuẩn bị dữ liệu ảnh cho các tác vụ phân tích chuyên sâu.

## Công nghệ sử dụng

* **Python:** Ngôn ngữ lập trình chính.
* **Pillow (PIL):** Để đọc và xử lý ảnh 
* **NumPy:** Xử lý dữ liệu ảnh dưới dạng mảng số hiệu quả.
* **OpenCV:** Thư viện mạnh mẽ cho các phép biến đổi hình học và phân đoạn ảnh (Otsu, Adaptive Thresholding, các hàm liên quan đến xoay, dịch chuyển).
* **Scikit-image :** Cung cấp các thuật toán xử lý ảnh, ví dụ 
* **Scipy :** Hỗ trợ các phép toán hình thái học
* **Matplotlib:** Để hiển thị ảnh trực quan các bước xử lý và kết quả.

## Chi tiết các Bài Tập & Công thức

Các bài tập được thực hiện trên ảnh "Đà Lạt" ('dalat.jpg'), với các vùng ảnh cụ thể được chọn để áp dụng các phép biến đổi.

## Chi tiết các Bài Tập & Công thức

Các bài tập được thực hiện trên ảnh "Đà Lạt" (giả định là `dalat.jpg`), với các vùng ảnh cụ thể được chọn để áp dụng các phép biến đổi.

### Bài 1: Phân vùng LangBiang - Dịch chuyển & Otsu Thresholding
* **Mục đích:** Trích xuất và phân đoạn vùng núi LangBiang.
* **Tịnh tiến vùng chọn:** Dịch chuyển vùng LangBiang sang phải 100px.
    * **Công thức dịch chuyển:** $(x', y') = (x + T_x, y + T_y)$ với $T_x = 100$, $T_y = 0$.
* **Phân vùng bằng Otsu:** Tự động tìm ngưỡng phân chia tiền cảnh/hậu cảnh trên vùng đã dịch chuyển.
    * **Nguyên lý Otsu:** Tối đa hóa phương sai giữa hai lớp (ảnh nền và đối tượng).
* **Lưu ảnh:** `lang_biang.jpg`

### Bài 2: Phân vùng Hồ Xuân Hương - Xoay & Adaptive Thresholding
* **Mục đích:** Xoay vùng ảnh và áp dụng ngưỡng thích nghi để phân đoạn.
* **Xoay đối tượng:** Xoay vùng Hồ Xuân Hương 45 độ quanh tâm.
    * **Công thức xoay:**
        $x' = x_c + (x - x_c)\cos\theta - (y - y_c)\sin\theta$
        $y' = y_c + (x - x_c)\sin\theta + (y - y_c)\cos\theta$
        Với $(x_c, y_c)$ là tâm xoay và $\theta = 45^\circ$.
* **Adaptive Thresholding:** Áp dụng ngưỡng cục bộ với hằng số $C = 60$.
    * **Công thức Adaptive Threshold:** $T(x,y) = \text{Mean}(N(x,y)) - C$.
* **Lưu ảnh:** `ho_xuan_huong.jpg`

### Bài 3: Phân vùng Quảng trường Lâm Viên - Coordinate Mapping & Binary Closing
* **Mục đích:** Trích xuất vùng và làm mịn bằng phép toán hình thái học.
* **Coordinate Mapping:** Tạo mặt nạ nhị phân cho vùng Quảng trường Lâm Viên dựa trên tọa độ.
    * **Nguyên lý:** Đánh dấu pixel trong vùng là 1 (hoặc 255), còn lại là 0.
* **Binary Closing:** Áp dụng phép toán đóng nhị phân trên mặt nạ.
    * **Công thức Binary Closing:** $A \bullet B = (A \oplus B) \ominus B$.
* **Lưu ảnh:** `quan_truong_lam_vien.jpg`

### Bài 4: Tạo Menu tương tác
* **Mục đích:** Xây dựng chương trình tương tác cho phép người dùng lựa chọn chức năng xử lý ảnh.
* **Menu:** Gồm `geometric_transformation` (coordinate_mapping, Rotate, Scale, Shift) và `segment` (Adaptive_thresholding, Binary_dilation, Binary_erosion, Otsu).
* **Lựa chọn:** Chọn 1 chức năng duy nhất hoặc kết hợp 1 từ `geometric_transformation` và 1 từ `segment`.
* **Hiển thị:** Kết quả của mỗi phép xử lý được hiển thị.

   ## Hướng dẫn sử dụng

### 1. Cài đặt môi trường
pip install opencv-python

### 2. Chạy Notebook
Mở Jupyter Notebook (hoặc JupyterLab, VSCode với extension Jupyter) từ thư mục chứa file main.ipynb.

Chạy từng cell trong notebook để xem từng bước xử lý và kết quả của các thuật toán.

Đối với Bài 4 (Menu tương tác), bạn sẽ cần chạy cell chứa hàm main() và làm theo hướng dẫn trên cửa sổ console/output của notebook.

### 3. Tùy chỉnh tham số
Bạn có thể thay đổi các giá trị tham số trong các cell tương ứng (ví dụ: góc xoay, hệ số co giãn, số lần lặp cho các phép toán hình thái học, block size và C value cho Adaptive Thresholding) để quan sát tác động khác nhau lên ảnh.
