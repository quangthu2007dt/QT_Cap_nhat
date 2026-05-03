# CÁC BƯỚC CẦN LÀM CHO MAXCARE

## Chốt tình hình đã kiểm tra

Source MaxCare hiện tại:

```text
D:\MAXCARE_CAPNHAT
```

Repo source:

```text
https://github.com/quangthu2007dt/Maxcare.git
```

Nhánh chuẩn đang dùng:

```text
MAXCARE_PHUC_HOI
```

Trạng thái Git hiện tại:

```text
Sạch, chưa có file sửa dở.
```

Project chính:

```text
D:\MAXCARE_CAPNHAT\MaxCare
```

Solution chính:

```text
D:\MAXCARE_CAPNHAT\MaxCare.sln
```

Bộ chạy sau build:

```text
D:\MAXCARE_CAPNHAT\MaxCare\bin\Debug\net48
```

Repo public phát hành chung:

```text
E:\QT_Cap_nhat
```

Thư mục public chuẩn cho app này:

```text
E:\QT_Cap_nhat\MaxCare
```

Legacy cũ giữ nguyên:

```text
D:\MAXCARE_CAPNHAT\release\stable
E:\QT_Cap_nhat\release\stable
```

Không xóa, không đổi tên, không di chuyển legacy cho đến khi xác minh app cũ không còn dùng.

---

## Phần 1 — Chuẩn hóa source sửa chữa

Cần làm:

1. Giữ `D:\MAXCARE_CAPNHAT` làm source sửa chữa chính.
2. Giữ nhánh làm việc là `MAXCARE_PHUC_HOI`.
3. Không tạo thêm thư mục source mới nếu chưa cần.
4. Thêm file quy ước vào repo source:

```text
D:\MAXCARE_CAPNHAT\QUY_UOC_MAXCARE_PHAT_HANH.md
```

5. Tất cả sửa code đều làm trong repo này.
6. Mỗi lần sửa xong phải build trước khi push.

Quy tắc:

```text
Build lỗi = không push source.
Build lỗi = không phát hành.
```

---

## Phần 2 — Chuẩn hóa public release

Cần tạo cấu trúc public mới:

```text
E:\QT_Cap_nhat\MaxCare
│
├─ manifest.json
├─ releases
│  └─ yy.MM.dd
│     └─ MaxCare_yy.MM.dd.qtpkg
└─ docs
   └─ QUY_UOC_MAXCARE_PHAT_HANH.md
```

Version phát hành lấy theo ngày hiện tại khi chạy script.

Quy ước version:

```text
yy.MM.dd
```

Ví dụ nếu chạy script ngày 2026-05-02:

```text
26.05.02
```

Tên gói phát hành:

```text
MaxCare_26.05.02.qtpkg
```

Thư mục chứa gói:

```text
E:\QT_Cap_nhat\MaxCare\releases\26.05.02
```

Manifest public:

```text
E:\QT_Cap_nhat\MaxCare\manifest.json
```

Manifest phải trỏ đúng gói mới nhất:

```json
{
  "appName": "MaxCare",
  "channel": "stable",
  "latestVersion": "26.05.02",
  "releaseDate": "2026-05-02",
  "packageFileName": "MaxCare_26.05.02.qtpkg",
  "packageUrl": "https://raw.githubusercontent.com/quangthu2007dt/QT_Cap_nhat/main/MaxCare/releases/26.05.02/MaxCare_26.05.02.qtpkg",
  "notes": "Phat hanh MaxCare 26.05.02. Goi cap nhat co mat khau giai nen."
}
```

Mật khẩu gói phát hành:

* Nhập thủ công khi chạy script phát hành.
* Không lưu trong script.
* Không lưu trong manifest.
* Không lưu trong repo.
* Không ghi ra log.

---

## Phần 3 — Tạo các file 1-click

### 1. File build kiểm tra

Tên file:

```text
D:\MAXCARE_CAPNHAT\BUILD_MAXCARE_1_CLICK.ps1
```

Việc cần làm:

1. Vào `D:\MAXCARE_CAPNHAT`.
2. Kiểm tra branch là `MAXCARE_PHUC_HOI`.
3. Build `MaxCare.sln`.
4. Nếu build lỗi thì dừng.
5. Nếu build OK thì báo vị trí `MaxCare\bin\Debug\net48`.

---

### 2. File đẩy source GitHub

Tên file:

```text
D:\MAXCARE_CAPNHAT\GIT_DAY_SOURCE_MAXCARE_1_CLICK.ps1
```

Việc cần làm:

1. Vào `D:\MAXCARE_CAPNHAT`.
2. Kiểm tra branch là `MAXCARE_PHUC_HOI`.
3. Chạy build trước.
4. Build lỗi thì dừng.
5. Build OK thì `git add`.
6. Tạo commit.
7. Push lên repo source `Maxcare.git`.

Quy tắc:

```text
Build lỗi = không git push.
```

---

### 3. File phát hành public

Tên file:

```text
D:\MAXCARE_CAPNHAT\PHAT_HANH_MAXCARE_1_CLICK.ps1
```

Việc cần làm:

1. Vào `D:\MAXCARE_CAPNHAT`.
2. Kiểm tra branch là `MAXCARE_PHUC_HOI`.
3. Chạy build `MaxCare.sln`.
4. Build lỗi thì dừng.
5. Lấy ngày hiện tại để tạo version.
6. Ví dụ ngày 2026-05-02 thì version là `26.05.02`.
7. Copy bộ chạy từ:

```text
D:\MAXCARE_CAPNHAT\MaxCare\bin\Debug\net48
```

sang thư mục tạm để đóng gói.

8. Xóa dữ liệu thật/file nhạy cảm khỏi thư mục tạm trước khi đóng gói:

```text
account
configs chứa dữ liệu thật
data thật
database thật
profiles
settings
log
log_capture
*.sqlite dữ liệu thật
*.db dữ liệu thật
update.ini nếu chứa đường dẫn/máy cá nhân
```

9. Giữ các file runtime cần thiết để app chạy.
10. Hỏi nhập mật khẩu đóng gói.
11. Dùng mật khẩu vừa nhập để khóa file `.qtpkg`.
12. Không lưu mật khẩu ở bất kỳ đâu.
13. Copy gói sang:

```text
E:\QT_Cap_nhat\MaxCare\releases\yy.MM.dd
```

14. Cập nhật:

```text
E:\QT_Cap_nhat\MaxCare\manifest.json
```

15. Copy file quy ước sang:

```text
E:\QT_Cap_nhat\MaxCare\docs\QUY_UOC_MAXCARE_PHAT_HANH.md
```

16. Git add / commit / push repo public `QT_Cap_nhat`.

Quy tắc:

```text
Build lỗi = không phát hành.
Thiếu mật khẩu = không đóng gói khóa.
Không có gói hợp lệ = không push public.
Không có manifest hợp lệ = không push public.
```

---

## Thứ tự làm thực tế

Làm theo đúng thứ tự này:

1. Tạo/cập nhật file `QUY_UOC_MAXCARE_PHAT_HANH.md` trong source.
2. Tạo thư mục public `E:\QT_Cap_nhat\MaxCare`.
3. Tạo file `BUILD_MAXCARE_1_CLICK.ps1`.
4. Test build 1-click.
5. Tạo file `GIT_DAY_SOURCE_MAXCARE_1_CLICK.ps1`.
6. Test đẩy source 1-click.
7. Tạo file `PHAT_HANH_MAXCARE_1_CLICK.ps1`.
8. Test phát hành ra `E:\QT_Cap_nhat\MaxCare`.
9. Kiểm tra gói `.qtpkg` mở bằng mật khẩu thủ công.
10. Kiểm tra manifest public trỏ đúng gói mới.
11. Giữ nguyên legacy `release\stable`.

---

## Chốt nguyên tắc sống còn

```text
1. Source chính: D:\MAXCARE_CAPNHAT
2. Branch chính: MAXCARE_PHUC_HOI
3. App public name: MaxCare
4. Public release mới: E:\QT_Cap_nhat\MaxCare
5. Version phát hành lấy theo ngày hiện tại khi chạy script
6. Gói phát hành có mật khẩu nhập thủ công
7. Không lưu mật khẩu trong bất kỳ file nào
8. Không public dữ liệu thật/file nhạy cảm
9. Build lỗi thì không push và không phát hành
10. Legacy release/stable giữ nguyên
```
