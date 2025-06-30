# Báo cáo Thực hành Lab 3: Các Biến đổi hình học

## Sinh viên thực hiện
**Tên:** Bùi Lâm Chí Đạt
**Mã số sinh viên:** 207CT27720

## Giới thiệu
Lab này khám phá và triển khai các phép biến đổi hình học cơ bản trên ảnh số sử dụng thư viện `SciPy` (`scipy.ndimage`) và `NumPy` trong Python. Mục tiêu là hiểu rõ cách các phép biến đổi như tịnh tiến, xoay, phóng to/thu nhỏ (zoom) và biến đổi ánh xạ tọa độ (coordinate map) tác động lên dữ liệu hình ảnh.


#3 1. Chọn đối tượng trong ảnh
 
## Yêu cầu Hệ thống
Mục đích:

Cắt ảnh nhỏ trong ảnh gốc ban đầu
Cấu trúc code:

example = data[800:1200, 570:980]
800:1200: Chỉ định phạm vi cột dọc (từ 800 đến 1199).
570:980: Chỉ định phạm vi cột ngang (từ 570 đến 979).

## 2. Tịnh tiến đơn
Mục đích:

Để dịch chuyển ảnh
Cấu trúc code:

example = nd.shift(data, (100, 25))
nd.shift(): Là hàm từ scipy.ndimage để dịch chuyển dữ liệu
(100, 25): Đây là tham số dịch chuyển (dịch chuyển 100 pixel xuống dưới và 25 pixel sang phải)

## 3. Thay đổi kích thước ảnh
Mục đích:

Phóng to ảnh
Cấu trúc code:

example = nd.zoom(data, (5, 5, 1))
nd.zoom(): Đây là một hàm từ thư viện scipy.ndimage, được dùng để phóng to ảnh
(5, 5, 1): (tỷ lệ phóng to cho chiều thứ nhất, tỷ lệ phóng to cho chiều thứ 2, tỷ lệ phóng to cho chiều thứ 3)

## 4. Xoay ảnh
Mục đích:

Xoay ảnh theo góc mong muốn
Cấu trúc code:

example = nd.rotate(data, 30)
nd.rotate(): Đây là một hàm từ thư viện scipy.ndimage, dùng để xoay ảnh
30: là số góc muốn xoay
