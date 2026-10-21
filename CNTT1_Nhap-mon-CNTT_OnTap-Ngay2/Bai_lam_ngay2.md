# BÀI LÀM – ÔN TẬP NGÀY 2

- **Họ tên: Phạm Quang Vinh**
- **Lớp: CNTT1**
- **Link repository:**
- **Hệ điều hành Windows**

## Bài 1. Lọc log thủ công

### Lệnh đã chạy

```shell
get-content logs/access.log
select-string "ERROR" access.log > error_report.txt
```

### 2 dòng lỗi đầu tiên trong error_report.txt

```text
access.log:4:2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
access.log:6:2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
```

## Bài 2. Đếm bằng pipeline

### Lệnh

```shell
Get-Content logs/access.log | Select-String "WARNING" | Measure-Object -Line
```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text
WARNING trong access.log: 4
ERROR trong payment.log: 6
```

## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
.\auto_warning.ps1
```

### Nội dung file logs/warning_report.txt

```text
2025-10-18 09:19:13 [WARNING] Cong thanh toan phan hoi cham
2025-10-18 09:28:16 [WARNING] Nhieu lan nhap sai ma OTP
2025-10-18 09:43:01 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:46:22 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:49:43 [WARNING] So du vi gan bang hoc phi
```

## Bài 4. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell
get-content logs/access.log
select-string "ERROR" access.log > error_report.txt
select-string "WARNING" access.log > warning_report.txt
Get-Content logs/access.log | Select-String "WARNING" | Measure-Object -Line
```

### Nội dung file logs/tong_hop_ngay2.txt

```text
2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:33:51 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:37:19 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:49:43 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:53:11 [ERROR] Het thoi gian cho (timeout)
```

## Bài 5. Câu hỏi ngắn

- **a)** > là để ghi đè lên nội dung cũ, >> là để chèn thêm nội dung vào mà không làm mất nội dung cũ.
- **b)** Sẽ bị ghi đè và mất file 
- **c)**giúp script hoạt động linh hoạt và chính xác trên bất kỳ máy tính nào khi mở đúng thư mục dự án