# SDH — Quản lý Thu Chi

Web app một file (`index.html`) quản lý **phiếu thu, phiếu chi, quỹ tiền mặt** cho công ty,
mô phỏng theo phần mềm kế toán quỹ. Chạy hoàn toàn trong trình duyệt, dữ liệu lưu bằng
`localStorage` — không cần server, không cần cài đặt, phù hợp chạy trên **GitHub Pages**.

## Tính năng

- **Đăng nhập** người dùng (mặc định `admin` / `admin`), quản lý nhiều người dùng.
- **Phiếu Thu / Phiếu Chi**: tạo mới, sửa, xóa, lưu vào hệ thống; tự sinh số phiếu
  (RVO/PVO-MMYYnnn); lọc xem theo Ngày / Tuần / Tháng / Năm / Tất cả.
- **In phiếu A4** theo mẫu 01-TT / 02-TT (Bộ Tài chính), 2 liên trên một trang, có
  **đọc số tiền thành chữ** tiếng Việt.
- **Đối tượng Thu/Chi** (người nhận/nộp tiền): thêm, sửa, xóa; thêm nhanh ngay khi lập phiếu.
- **Danh mục Khoản Thu / Khoản Chi**, **Quỹ / Tài khoản** (tự tính Đã thu / Đã chi / Còn lại).
- **Sổ quỹ** (tồn quỹ lũy kế) và **Thống kê** thu chi theo khoản.
- **Thiết lập Mẫu In**: tên công ty, địa chỉ, chữ ký (Giám đốc, Kế toán trưởng, Thủ quỹ...).

## Chạy thử nhanh

Mở trực tiếp `index.html` bằng trình duyệt (nháy đúp) là dùng được ngay.

## Đưa lên GitHub Pages

1. Tạo repository mới trên GitHub, tải `index.html` (và `README.md`) lên nhánh `main`.
2. Vào **Settings → Pages**.
3. Mục **Build and deployment → Source**: chọn **Deploy from a branch**.
4. Chọn branch **main**, thư mục **/ (root)**, bấm **Save**.
5. Đợi ~1 phút, trang sẽ chạy tại `https://<tên-tài-khoản>.github.io/<tên-repo>/`.

> Có thể dùng GitHub Desktop hoặc lệnh:
> ```
> git init && git add . && git commit -m "SDH quan ly thu chi"
> git branch -M main
> git remote add origin https://github.com/<user>/<repo>.git
> git push -u origin main
> ```

## Hai chế độ lưu dữ liệu

App tự nhận biết chế độ dựa vào cấu hình Firebase ở đầu file `index.html`:

- **Lưu máy (mặc định)** — để trống `apiKey`. Dữ liệu lưu trong `localStorage` của
  **từng trình duyệt/máy**, không đồng bộ. Phù hợp một người/một máy hoặc demo.
  Xóa cache trình duyệt sẽ mất dữ liệu.
- **Đồng bộ đám mây (khuyến nghị khi nhiều máy)** — điền cấu hình Firebase. Đăng nhập
  bằng email/mật khẩu, dữ liệu lưu tập trung trên Firestore và **đồng bộ realtime** giữa
  mọi máy. Xem hướng dẫn cài đặt từng bước trong **[`FIREBASE.md`](FIREBASE.md)**.
