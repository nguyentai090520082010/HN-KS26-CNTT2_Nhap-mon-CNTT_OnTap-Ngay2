# BÀI LÀM – ÔN TẬP NGÀY 2

- **Họ tên:** Nguyễn Đức Tài
- **Lớp:** Công nghệ thông tin 2
- **Link repository:**
- **Hệ điều hành (Windows/macOS):** Windows

## Bài 1. Lọc log thủ công

### Lệnh đã chạy

```shell
Get-Content logs/access.log | Select-String "ERROR" > logs/error_report.txt
Get-Content logs/error_report.txt

```

### 2 dòng lỗi đầu tiên trong error_report.txt

```text
2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)

```

## Bài 2. Đếm bằng pipeline

### Lệnh

```shell
Get-Content logs/access.log | Select-String "WARNING" | Measure-Object -Line
Get-Content logs/payment.log | Select-String "ERROR" | Measure-Object -Line

```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text
WARNING trong access.log: 4
ERROR trong payment.log: 6
```

## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\auto_warning.ps1

```

### Nội dung file logs/warning_report.txt

```text
=== CANH BAO THANH TOAN ===

2025-10-18 09:19:13 [WARNING] Cong thanh toan phan hoi cham
2025-10-18 09:28:16 [WARNING] Nhieu lan nhap sai ma OTP
2025-10-18 09:43:01 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:46:22 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:49:43 [WARNING] So du vi gan bang hoc phi

```

## Bài 4. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell
"=== TONG HOP ACCESS LOG ===" > logs/tong_hop_ngay2.txt
Get-Content logs/access.log | Select-String "ERROR" >> logs/tong_hop_ngay2.txt
Get-Content logs/payment.log | Select-String "WARNING" | Measure-Object -Line | Select-Object -ExpandProperty Lines >> logs/tong_hop_ngay2.txt

```

### Nội dung file logs/tong_hop_ngay2.txt

```text
=== TONG HOP ACCESS LOG ===
2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:33:51 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:37:19 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:49:43 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:53:11 [ERROR] Het thoi gian cho (timeout)
5

```

## Bài 5. Câu hỏi ngắn

- **a)** Lệnh > dùng để ghi đè, còn lệnh >> dùng để ghi nối tiếp.
- **b)** Ở Bài 4, nếu lệnh thứ hai dùng > thay cho >>, toàn bộ file sẽ bị ghi đè làm xóa mất dòng tiêu đề === TONG HOP ACCESS LOG === vừa tạo ở lệnh thứ nhất.
- **c)** Đường dẫn tương đối giúp script **chạy được trên mọi máy tính**; đường dẫn tuyệt đối bị cố định theo máy cá nhân nên sẽ báo lỗi khi đưa lên GitHub hoặc chạy trên máy khác.

## Tự chấm (điền sau khi có đáp án)

- **Điểm tự chấm:** ..../100
- **Lỗi mình đã mắc và cách sửa:**
