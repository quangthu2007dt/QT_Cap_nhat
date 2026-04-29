# Ke hoach phuc hoi code va phat hanh tung giai doan

Ngay lap: 2026-04-30

## Muc tieu

Phuc hoi cac chuc nang da phat trien trong ban dang chay sai DLL sang ban nen dung DLL, giu lai he thong cap nhat tu dong va phat hanh thanh ban moi cho may khach.

Tai lieu nay chi la ke hoach thuc hien. Khong dua source code, key, database, profile, settings that, log that, token, cookie, file nguoi dung hoac DLL rieng tu len GitHub public.

## Quy tac bat buoc

1. Khong sua source goc dang dung sai DLL.
2. Khong sua source phuc hoi truc tiep neu chua co ban merge rieng.
3. Moi buoc co nguy co thay doi file phai bao truoc va chi lam sau khi duoc xac nhan.
4. Khong public full source.
5. Repo public chi dung cho manifest, goi cap nhat mong va tai lieu khong nhay cam.
6. Khong copy database/settings/profile/log/output that vao goi cap nhat.
7. Khong thay doi logic ngoai pham vi phuc hoi chuc nang va cap nhat.
8. Version hien tai su dung dang ngan gon dang `26.04.29`, khong tu y dat version dai hon.
9. Luon build va kiem tra sau tung cum thay doi lon.
10. Neu co khac biet khong chac la code moi hay code cu, dung lai bao cao truoc khi merge.

## Hien trang da doi chieu

Co 2 nguon can doi chieu:

- Nguon A: ban da phat trien nhieu chuc nang nhung dang dung sai DLL.
- Nguon B: ban nen dung DLL, da co version hien tren app va co ha tang auto update.

Ket qua doc so bo:

- Nguon A co nhieu file chuc nang ma Nguon B chua co.
- Nguon B co cac file ha tang update/version ma Nguon A chua co.
- Co nhieu file cung ten nhung khac noi dung, can merge co kiem soat, khong copy de nguyen cay.

Nhom chuc nang can phuc hoi tu Nguon A:

- Quan ly prompt AI va tao noi dung bang AI.
- Cau hinh API key cho AI.
- Cac control AI trong cac man hinh hanh dong.
- Backup du lieu ung dung theo co che moi.
- Cau hinh thu muc backup va thao tac backup trong man hinh cau hinh chung.
- An/hien Chrome khi chay tuong tac.
- Dong ho/trang thai tren giao dien chinh.
- Tuy chon ngon ngu Chrome Viet/Anh.
- Cai tien tao Page de nhan dien giao dien Viet/Anh va lay ket qua chac hon.
- Cai tien gui tin nhan UID co them tham so can thiet.
- Kiem tra file update tai ve va kiem tra file remote truoc khi cap nhat.

Nhom ha tang can giu tu Nguon B:

- Hien version tren title app.
- Doc version tu file version.
- Doc manifest cap nhat.
- Kiem tra ban moi va goi Updater.
- Goi cap nhat public dang mong, khong chua source va khong chua du lieu nguoi dung.

## Chien luoc phuc hoi

Khong chon cach copy de mot ben len ben con lai.

Cach dung:

1. Tao workspace merge rieng.
2. Lay Nguon B lam nen vi dung DLL va co auto update.
3. Dua cac chuc nang da phat trien tu Nguon A sang theo tung cum nho.
4. Sau moi cum, build kiem tra.
5. Sau khi build sach, tao ban runtime rieng de smoke test.
6. Chi khi smoke test dat moi dong goi release.

## Giai doan 0 - Dong bang va sao luu

Muc tieu: dam bao khong mat hien trang.

Viec lam:

- Kiem tra app dang chay hay khong truoc khi doc/copy runtime.
- Tao ban sao rieng cho Nguon A va Nguon B neu can thao tac merge.
- Ghi lai hash/so file cua 2 nguon.
- Khong xoa, khong reset git, khong clean thu muc cu.

Dieu kien hoan thanh:

- Co bang doi chieu file thieu/thua/khac nhau.
- Co workspace merge rieng.
- Source goc van giu nguyen.

Trang thai: Cho thuc hien.

## Giai doan 1 - Lap danh sach diff chi tiet

Muc tieu: biet ro file nao can copy, file nao can merge tay, file nao phai giu cua Nguon B.

Viec lam:

- Tach nhom file chi co trong Nguon A.
- Tach nhom file chi co trong Nguon B.
- Tach nhom file cung ten nhung khac noi dung.
- Ghi ro muc dich tung nhom.
- Danh dau file nguy co cao: form lon, file core browser, file common/helper, file project/version.

Dieu kien hoan thanh:

- Co bang file can merge.
- Co danh sach thu tu uu tien.
- Co nhan dinh ro file nao khong duoc copy de.

Trang thai: Dang chuan bi.

## Giai doan 2 - Dua module moi tu Nguon A sang workspace merge

Muc tieu: phuc hoi cac module moi ma Nguon B chua co.

Pham vi:

- Module quan ly prompt AI.
- Module cau hinh API key AI.
- Module backup app data.
- Form cau hinh prompt/API key lien quan.

Cach lam:

- Copy tung file module moi vao workspace merge.
- Khong copy thu muc backup/live/snapshot that.
- Build ngay sau khi them module.
- Neu loi compile do thieu reference hoac namespace, chi sua trong pham vi module lien quan.

Dieu kien hoan thanh:

- Workspace build qua sau khi them module.
- Khong co du lieu that bi them vao source.

Trang thai: Cho duyet.

## Giai doan 3 - Phuc hoi control AI trong cac man hinh hanh dong

Muc tieu: dua lai tuy chon tao noi dung bang AI vao cac man hinh da duoc phat trien.

Pham vi:

- Man hinh buff like/comment.
- Man hinh buff tin nhan profile.
- Man hinh dang bai.
- Man hinh tuong tac profile.

Cach lam:

- Merge control UI, load prompt, save lua chon prompt, nut mo cau hinh prompt.
- Kiem tra resx/designer neu co.
- Khong sua logic hanh dong khac neu khong lien quan den AI.

Dieu kien hoan thanh:

- Build qua.
- Cac form mo duoc.
- Control AI hien dung va khong lam hong cau hinh cu.

Trang thai: Cho duyet.

## Giai doan 4 - Phuc hoi backup va cau hinh chung

Muc tieu: dua lai co che backup da phat trien nhung khong lam mat co che backup/version hien tai.

Pham vi:

- Backup app data.
- Backup database/live/interact/settings neu co trong code da phat trien.
- Man hinh cau hinh chung va nut/chon thu muc backup.

Cach lam:

- So sanh ky voi chuc nang backup dang co o Nguon B.
- Neu 2 cach backup khac nhau, bao cao truoc khi hop nhat.
- Khong mac dinh ghi de database/settings that.
- Kiem tra duong dan backup mac dinh khong tro vao thu muc public/release.

Dieu kien hoan thanh:

- Build qua.
- Backup chay tren ban test.
- Khong dong goi backup that vao release.

Trang thai: Cho duyet.

## Giai doan 5 - Phuc hoi thay doi giao dien chinh va Chrome

Muc tieu: dua lai cac tien ich da phat trien tren giao dien chinh va dieu khien Chrome.

Pham vi:

- An/hien Chrome.
- Trang thai/dong ho tren giao dien chinh.
- Tuy chon ngon ngu Chrome Viet/Anh.
- Cac cai tien tao Page va gui tin nhan UID.

Cach lam:

- Merge tung cum nho trong file giao dien chinh va file browser core.
- Giu lai code hien version va auto update cua Nguon B.
- Voi cac ham da thay doi tham so, kiem tra tat ca noi goi.
- Build sau tung cum.

Dieu kien hoan thanh:

- Build qua.
- App mo len van hien version dung.
- Chrome mo duoc voi ngon ngu da chon.
- Chuc nang an/hien Chrome khong lam treo tien trinh.

Trang thai: Cho duyet.

## Giai doan 6 - Giu va kiem tra auto update

Muc tieu: dam bao sau khi phuc hoi code, may khach van cap nhat duoc nhu thiet ke.

Pham vi:

- Version hien tren app.
- File version local.
- Manifest public.
- Updater.
- Goi cap nhat mong.

Cach lam:

- Giu file ha tang update/version cua Nguon B.
- Neu file giao dien chinh duoc merge tu Nguon A, phai dua lai doan hien version tu Nguon B.
- Tao runtime test rieng, khong dung truc tiep thu muc may khach.
- Kiem tra app doc manifest va goi updater.

Dieu kien hoan thanh:

- App hien version ngan gon dung.
- Khong mat popup/luong update.
- Goi public chi chua file can thiet de cap nhat.

Trang thai: Cho duyet.

## Giai doan 7 - Build va smoke test

Muc tieu: xac nhan ban phuc hoi chay duoc truoc khi dong goi.

Viec lam:

- Build Debug de bat loi compile nhanh.
- Build Release/ban phat hanh neu can.
- Mo app tren thu muc runtime test.
- Kiem tra title version.
- Kiem tra mot so form da merge.
- Kiem tra khong crash khi mo cau hinh chung, cau hinh prompt, cac form hanh dong.
- Kiem tra khong dong goi file nhay cam.

Dieu kien hoan thanh:

- Build 0 error.
- Runtime test mo duoc.
- Khong co source/data that trong goi public.

Trang thai: Cho duyet.

## Giai doan 8 - Dong goi phat hanh

Muc tieu: tao ban phat hanh moi cho may khach cap nhat.

Viec lam:

- Cap nhat version theo dang ngan gon da thong nhat.
- Tao goi update public dang mong.
- Tao manifest tro dung file goi moi.
- Tinh hash goi cap nhat.
- Kiem tra zip khong chua source, database, settings, profile, log, output.
- Giu ban full/private rieng neu can luu tru, khong dua len public.

Dieu kien hoan thanh:

- Manifest truy cap duoc.
- File zip tai duoc.
- Hash local va remote khop.
- May test cap nhat duoc.

Trang thai: Cho duyet.

## Giai doan 9 - Phat hanh va theo doi

Muc tieu: dua ban moi ra may khach an toan.

Viec lam:

- Day manifest va goi cap nhat len repo public.
- Kiem tra raw URL.
- Chay thu tren mot may/test folder truoc.
- Theo doi loi cap nhat, loi mo app, loi form da merge.
- Neu co loi nghiem trong, dung cap nhat bang cach chua nang version tren manifest hoac thay goi da kiem tra.

Dieu kien hoan thanh:

- May khach cap nhat duoc.
- App mo lai khong mat phien dang nhap do khong ghi de du lieu nguoi dung.
- Chuc nang da phuc hoi hoat dong trong pham vi test.

Trang thai: Cho duyet.

## Tieu chi khong duoc vuot qua

- Khong dua full source len repo public.
- Khong dua DLL rieng tu/khong duoc phep neu chua xac dinh quyen phan phoi.
- Khong dua file co thong tin nguoi dung that.
- Khong thay doi co che dang nhap, token, cookie, profile neu khong nam trong pham vi phuc hoi.
- Khong dong goi database/settings/profile mac dinh vao update zip.
- Khong tu y doi ten app, ten version, ten repo, URL update khi chua duoc xac nhan.

## Cach lam viec tiep theo

Moi giai doan can co 3 buoc:

1. Bao cao viec sap lam.
2. Thuc hien trong workspace merge hoac runtime test rieng.
3. Bao cao ket qua, file da cham vao, lenh build/test da chay va loi con lai neu co.

Khi mot giai doan hoan thanh, cap nhat `Trang thai` trong tai lieu nay de tiep tuc giai doan sau.
