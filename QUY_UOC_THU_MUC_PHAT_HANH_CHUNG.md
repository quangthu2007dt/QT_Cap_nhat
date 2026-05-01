# QUY ƯỚC THƯ MỤC PHÁT HÀNH CHUNG / PUBLIC REPO CLONE

## 1. Mục đích

Thư mục phát hành chung là bản clone của repo public dùng để chứa file update cho nhiều app.

Ví dụ repo public:

```text
QT_Cap_nhat
```

Ví dụ thư mục clone trên máy:

```text
E:\QT_Cap_nhat
```

Thư mục này không phải nơi sửa source code chính của từng app.

Nó là kho phát hành chung.

---

## 2. Vai trò chính

Thư mục phát hành chung dùng để:

```text
- Chứa file zip bản phát hành
- Chứa manifest/latest.json
- Chứa metadata version
- Push bản phát hành lên GitHub public
- Tạo link raw.githubusercontent.com để app tải update
```

Ví dụ link update:

```text
https://raw.githubusercontent.com/quangthu2007dt/QT_Cap_nhat/main/DANG_NHAP_FB/releases/V2.80/DANG_NHAP_FACEBOOK_V2_80.zip
```

---

## 3. Cấu trúc chuẩn

Repo public phát hành nên chia theo từng app:

```text
QT_Cap_nhat
│
├─ DANG_NHAP_FB
│  ├─ latest.json
│  └─ releases
│     ├─ V2.79
│     └─ V2.80
│
├─ QUAN_LY_MAIL
│  ├─ latest.json
│  └─ releases
│
├─ MAXCARE
│  ├─ latest.json
│  └─ releases
│
└─ HOTMAIL_OTP
   ├─ latest.json
   └─ releases
```

Mỗi app có một thư mục riêng.

Không trộn file phát hành của app này vào thư mục app khác.

---

## 4. Nhiệm vụ của script phát hành

Script phát hành nằm ở thư mục source app, nhưng khi chạy sẽ đẩy file sang thư mục public repo clone.

Ví dụ:

```text
Source:
E:\DANG_NHAP_FB_SOURCE

Public release repo:
E:\QT_Cap_nhat
```

Quy trình script phát hành nên làm:

```text
1. Lấy bản build/publish mới từ source app
2. Đóng gói thành file zip
3. Copy zip vào E:\QT_Cap_nhat\DANG_NHAP_FB\releases\Vx.xx
4. Cập nhật latest.json
5. Git add/commit/push repo public
```

---

## 5. Phân biệt source repo và public release repo

| Loại repo | Vai trò |
|---|---|
| Source repo | Lưu code, sửa app, build app |
| Public release repo | Lưu file zip, manifest, bản update cho app tải |

Không sửa logic code app trong public release repo.

Không đặt source code chính của app vào public release repo.

---

## 6. Quy trình phát hành chuẩn cho mọi app

```text
1. Sửa code trong thư mục source của app
2. Build/Rebuild bằng Visual Studio
3. Nếu build lỗi → dừng
4. Nếu build OK → đẩy source lên GitHub source
5. Chạy script phát hành
6. Script copy zip/manifest sang repo public clone
7. Repo public clone push lên GitHub public
8. App người dùng tải bản mới từ GitHub public
```

---

## 7. Khi nào dùng repo public clone

Chỉ dùng repo public clone khi:

```text
- Cần cập nhật file zip phát hành
- Cần cập nhật latest.json
- Cần kiểm tra cấu trúc bản release
- Cần push bản update công khai
```

Không dùng repo public clone để sửa Form1.cs, service, class, Designer hoặc code chính của app.

---

## 8. Quy tắc version

Mỗi lần phát hành bản mới phải tăng version.

Ví dụ:

```text
V2.79 → V2.80 → V2.81
```

Không phát hành đè cùng một version nếu bản đó đã public, trừ khi đang sửa ngay tại giai đoạn test nội bộ và chưa cho app người dùng dùng.

Khuyến nghị:

```text
Có lỗi logic sau phát hành → sửa ở source → build OK → phát hành version mới tiếp theo
```

---

## 9. Quy tắc an toàn

Không được phát hành nếu build lỗi.

Không được để public repo clone trở thành nơi sửa code chính.

Không được để nhiều app ghi chung một thư mục release.

Không được xóa bản release cũ nếu chưa chắc chắn không cần rollback.

---

## 10. Kết luận ngắn

```text
Thư mục source = nơi sửa code.
Thư mục public repo clone = nơi chứa file update cho app tải.
Một app có một source riêng.
Nhiều app có thể dùng chung một repo public phát hành.
```
