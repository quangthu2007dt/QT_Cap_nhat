# QUY TẮC BẤT DI BẤT DỊCH CHO MỌI APP

Áp dụng cho tất cả dự án/app.

## 1. MAIN TRÊN GITHUB = NƠI DUY NHẤT GIỮ AN TOÀN APP

- `main` là mốc ổn định và là nguồn an toàn duy nhất của app.
- Không bao giờ xóa branch `main`, không force-push, không reset/rewrite lịch sử làm mất trạng thái ổn định của `main`.
- Không phát triển trực tiếp trên `main`.
- Mỗi đợt phát triển phải tạo hoặc dùng **nhánh phụ trên GitHub được sinh ra từ `main`**.
- Chỉ khi nhánh phụ đã hoàn thiện, đã test và chủ app xác nhận thì mới merge vào `main`.
- Sau khi merge, `main` lại trở thành mốc an toàn mới của app.
- Mọi bản phát hành chính thức phải lấy từ trạng thái đã được chốt trên `main`.

## 2. SOURCE LOCAL = NƠI PHÁT TRIỂN

- Local chỉ có **một thư mục source chuẩn** cho mỗi app.
- Source local phải lấy từ **nhánh phụ trên GitHub**, và nhánh phụ đó phải có gốc từ `main`.
- Source local là nơi sửa code, build thử, test và phát triển.
- Không dùng thư mục bản sử dụng làm source.
- Không làm việc trực tiếp trên `main` ở local, ngoại trừ thao tác quản trị ngắn để đọc/merge/chốt theo yêu cầu rõ ràng.
- Sau khi chốt `main`, tiếp tục phát triển trên nhánh phụ; nếu cần chu kỳ mới thì nhánh phụ phải được cập nhật/tạo lại từ `main` mới nhất.

### Local không tạo thư mục rác

- Không tạo clone source thứ hai, source backup, source test, source temp, thư mục vá tạm hoặc nhiều bản local song song.
- Không tạo các thư mục kiểu `*_OLD`, `*_NEW`, `*_TEST2`, `TEMP_SOURCE`, `COPY_SOURCE` để phát triển.
- Nếu build/test cần output, chỉ dùng đúng thư mục output chuẩn đã được dự án quy định; không nhân bản cả source.
- Dọn rác chỉ được dọn **file build tạm / output tạm / clone thừa đã xác định rõ**, tuyệt đối không được đụng `main`, bản sử dụng hoặc dữ liệu người dùng.

## 3. BẢN SỬ DỤNG = BẢN PHÁT HÀNH ĐỂ CHẠY THỰC TẾ

- Bản sử dụng là bản đã phát hành để người dùng chạy hằng ngày.
- Không bao giờ xóa thư mục bản sử dụng.
- Không dùng bản sử dụng để phát triển, test, thử code hoặc làm source.
- Chỉ cập nhật bản sử dụng khi có lệnh phát hành rõ ràng.
- Bản phát hành chính thức phải xuất phát từ `main` đã được chốt.
- Khi cập nhật bản sử dụng, chỉ thay phần chương trình cần thiết; không xóa cả thư mục rồi tạo lại.

## 4. DỮ LIỆU NGƯỜI DÙNG TRONG BẢN SỬ DỤNG = VÙNG BẢO VỆ TUYỆT ĐỐI

Không được tự ý xóa, di chuyển, ghi đè hoặc tạo lại các dữ liệu như:

- `data` / `Data`
- `AuthSessions`
- `Profiles`
- `Tokens`
- cookie, `Local State`, `Login Data`, `Web Data`
- file tài khoản như `accounts.xlsx`
- cấu hình, lịch sử, báo cáo, backup và dữ liệu phiên đăng nhập

Nếu không chắc một thư mục có phải dữ liệu người dùng hay không: **không xóa, phải kiểm tra trước**.

## 5. QUY TRÌNH DUY NHẤT ĐƯỢC PHÉP

`main` ổn định trên GitHub
→ tạo/cập nhật nhánh phụ từ `main`
→ source local checkout nhánh phụ
→ phát triển và test tại local
→ chủ app xác nhận
→ merge nhánh phụ vào `main`
→ build/phát hành từ `main`
→ cập nhật bản sử dụng nhưng giữ nguyên dữ liệu người dùng.

Không được đảo thứ tự này.

## 6. BA THỨ TUYỆT ĐỐI KHÔNG ĐƯỢC NHẦM

- `main` = **nơi giữ an toàn app**.
- source local trên nhánh phụ = **nơi phát triển app**.
- bản sử dụng = **bản phát hành để sử dụng thực tế**.

Không bao giờ được hiểu yêu cầu “dọn local”, “chỉ giữ một thư mục”, “đồng bộ source”, “build lại” hay “phát hành” thành quyền xóa `main` hoặc xóa bản sử dụng.

## 7. NGUYÊN TẮC CAO NHẤT

**KHÔNG BAO GIỜ XÓA MAIN. KHÔNG BAO GIỜ XÓA BẢN SỬ DỤNG. LOCAL CHỈ CÓ MỘT SOURCE PHÁT TRIỂN, KHÔNG TẠO THƯ MỤC RÁC.**
