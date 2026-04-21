# Đồ án Quản lý Sinh viên - Bảo mật Cơ sở dữ liệu (Lab 03)

Đây là dự án thực hành môn Bảo mật Cơ sở dữ liệu, tập trung vào việc áp dụng các kỹ thuật mã hóa dữ liệu thực tế trên hệ quản trị CSDL (SQL Server).

## 🎯 Mục tiêu dự án

*   **Tạo và quản lý khóa:** Quản lý khóa công khai/bí mật trong môi trường cơ sở dữ liệu.
*   **Mã hóa bất đối xứng (RSA):** Sử dụng thuật toán mã hóa công khai để bảo vệ dữ liệu nhạy cảm.
*   **Băm dữ liệu (Hashing):** Đảm bảo an toàn cho mật khẩu người dùng.
*   **Lập trình Stored Procedure:** Xử lý logic mã hóa và giải mã trực tiếp tại tầng CSDL.

## 🗄️ Cấu trúc Cơ sở dữ liệu (`QLSVNhom`)

Hệ thống bao gồm các thực thể chính phục vụ quản lý sinh viên đơn giản:

1.  **`NHANVIEN`**: Quản lý thông tin giảng viên và cán bộ.
2.  **`SINHVIEN`**: Hồ sơ chi tiết của sinh viên.
3.  **`LOP`**: Thông tin lớp học và giảng viên chủ nhiệm.
4.  **`HOCPHAN`**: Danh mục môn học.
5.  **`BANGDIEM`**: Quản lý điểm thi của sinh viên.

## 🛡️ Yêu cầu Bảo mật

Hệ thống áp dụng nghiêm ngặt các tiêu chuẩn bảo mật dữ liệu sau:

*   **Bảo mật Mật khẩu:** Cột `MATKHAU` của cả Sinh viên và Nhân viên đều được băm (hash) bằng thuật toán **SHA1**.
*   **Mã hóa Lương (RSA):** Cột `LUONG` của nhân viên được mã hóa bằng thuật toán **RSA_512**. Khóa bí mật (Private Key) được bảo vệ bằng chính mật khẩu của nhân viên đó.
*   **Mã hóa Điểm thi:** Cột `DIEMTHI` trong bảng điểm được mã hóa bằng Khóa công khai (Public Key) của nhân viên/giảng viên trực tiếp nhập điểm.
*   **Định danh Khóa:** Cột `PUBKEY` lưu trữ tên khóa công khai tương ứng với mã nhân viên (`MANV`).

## 💻 Ứng dụng Quản lý (App)

Phần mềm tương tác với CSDL (sử dụng Java/Python/C#) bao gồm các module chính:

*   **Authentication:** Màn hình đăng nhập dành cho Nhân viên (Yêu cầu `MANV` và `MATKHAU`).
*   **Quản lý Lớp học:** Xem và quản lý danh sách các lớp.
*   **Quản lý Sinh viên:** Xem thông tin sinh viên thuộc lớp do nhân viên quản lý.
*   **Nhập điểm:** Màn hình phân quyền nhập điểm (Điểm tự động được mã hóa bằng Public Key của nhân viên đang đăng nhập).

## 🚀 Hướng dẫn cài đặt CSDL

1.  Mở SQL Server Management Studio (SSMS).
2.  Mở file `lab03.sql` và thực thi (Execute) để khởi tạo toàn bộ cấu trúc bảng và Master Key.
3.  (Đang phát triển) Cài đặt ứng dụng client để tương tác.

---
*Khoa CNTT - Trường Đại học Khoa học Tự nhiên TP.HCM*
