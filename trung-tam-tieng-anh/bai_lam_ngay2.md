# bai_lam_ngay2

# BÀI LÀM – ÔN TẬP NGÀY 2

- **Họ tên: Nguyễn Tiến Dũng**
- **Lớp: HN-KS26_CNTT3**
- **Link repository:** https://github.com/Tdun87/HN-KS26_CNTT3_Nhap-mon-CNTT_OnTap-Ngay2
- **Hệ điều hành (Windows/macOS): Windows**

## Bài 1. Lọc log thủ công

### Lệnh đã chạy

```bash
Get-Content .\logs\access.log | Select-String "error"
Get-Content .\logs\access.log | Select-String "error" > .\logs\error_report.txt
Get-Content logs/error_report.txt -TotalCount 2
```

### 2 dòng lỗi đầu tiên trong error_report.txt

```

2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
```

## Bài 2. Đếm bằng pipeline

### Lệnh

```bash
 (Get-Content .\logs\access.log | Select-String "warning").Count
 (Get-Content .\logs\payment.log | Select-String "error").Count
```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```
WARNING trong access.log: 4
ERROR trong payment.log: 3
```

## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```bash
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
.\auto_warning.ps1
```

### Nội dung file logs/warning_report.txt

```
=== CANH BAO THANH TOAN ===

2025-10-18 09:19:13 [WARNING] Cong thanh toan phan hoi cham
2025-10-18 09:28:16 [WARNING] Nhieu lan nhap sai ma OTP
2025-10-18 09:43:01 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:46:22 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:49:43 [WARNING] So du vi gan bang hoc phi

```

## Bài 4. Báo cáo tổng hợp

### Các lệnh đã chạy

```bash
 "=== TONG HOP ACCESS LOG ===" > .\logs\tong_hop_ngay_2.txt
 Get-Content .\logs\access.log | Select-String "error" >> .\logs\tong_hop_ngay_2.txt
 Get-Content .\logs\access.log | Select-String "warning" >> .\logs\tong_hop_ngay_2.txt
```

### Nội dung file logs/tong_hop_ngay2.txt

```
=== TONG HOP ACCESS LOG ===

2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:33:51 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:37:19 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:49:43 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:53:11 [ERROR] Het thoi gian cho (timeout)

2025-10-18 08:13:31 [WARNING] Lop GT01 sap du si so
2025-10-18 08:21:27 [WARNING] Lop GT01 sap du si so
2025-10-18 08:45:15 [WARNING] Thoi gian tai trang cham
2025-10-18 09:21:27 [WARNING] Video bai giang dung luong lon

```

## Bài 5. Câu hỏi ngắn

- **a)  Lệnh ‘… > file’ dùng để ghi đè ( xóa cũ, ghi mới) còn lệnh ‘… >> file’ dùng để ghi nối tiếp (chèn nội dung xuống cuối file)**
- **b) dòng ‘=== TONG HOP ACCESS LOG ===’ sẽ bị xóa mất và bị ghi đè các dòng ERROR vào file**
- **c) vì đường dẫn tương đối dùng được linh hoạt trên mọi máy, đường dẫn tuyệt đối chỉ có thể dùng trên chính máy của người viết code.**

## Tự chấm (điền sau khi có đáp án)

- **Điểm tự chấm:** …./100
- **Lỗi mình đã mắc và cách sửa:**
