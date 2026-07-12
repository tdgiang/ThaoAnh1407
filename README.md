# 🎁 Website Chúc Mừng Sinh Nhật

Bản dựng lại **giống hệt** trang gốc `happy-birthday-love-link`, dùng chính bộ mã
nguồn gốc (CSS + hiệu ứng), chỉ thay phần nạp dữ liệu Firebase bằng một **CONFIG cục bộ**
để bạn tự điền nội dung — không cần tài khoản Firebase, không cần backend.

## 🎬 Luồng các cảnh (giống bản gốc)

1. **Màn mở đầu** — nền sao, hạt hồng bay, hộp quà 🎁, "Happy Birthday" (font Pacifico), tên người nhận, nút "Chạm để bắt đầu".
2. **Mưa chữ** kiểu Matrix (chữ tiếng Việt hồng) + chữ chính kết bằng hạt sáng (HAPPY, BIRTHDAY, tên…).
3. **Đồng hồ neon** trái tim (clock-reveal).
4. **Chúc mừng lớn** — "HAPPY / Birthday / — to — / [Tên]" vàng-hồng lấp lánh.
5. **Lời chúc** — thẻ hiện lần lượt tối đa 3 lời chúc.
6. **Sách ảnh lật 3D** — bìa bánh sinh nhật màu nước + các trang ảnh của bạn.
7. **Màn kết** — **ảnh xếp thành hình trái tim** (viền neon hồng) + **bóng bay** có ảnh/tên bay lên + pháo hoa. *(Hiện ra sau khi lật hết sách.)*
8. **Nhạc nền** phát suốt (nút MUSIC).

## ✏️ Cách chỉnh sửa nội dung

Mở `index.html`, tìm khối `window.BIRTHDAY_CONFIG` (gần giữa file) và sửa:

| Trường         | Ý nghĩa |
|----------------|---------|
| `name`         | Tên người nhận (màn mở đầu + phần chúc mừng lớn) |
| `sequenceName` | Tên chèn vào chuỗi chữ bay (thường để trùng `name`) |
| `wishes`       | Mảng tối đa **3** lời chúc |
| `images`       | Mảng ảnh cho sách lật — link `http...` hoặc file trong thư mục `image/` |
| `song`         | Link nhạc `.mp3` (file trong `music/` hoặc URL). Để `""` nếu không dùng |

### Thay ảnh của bạn — ⚠️ PHẢI để trong thư mục `photos/`
Chép ảnh của người nhận vào thư mục **`photos/`** rồi khai báo trong `images`:
```js
images: ["photos/anh1.jpg", "photos/anh2.jpg", "photos/anh3.jpg"]
```
> **Lưu ý quan trọng:** màn kết (ảnh xếp trái tim + bóng bay ảnh) **chỉ nhận ảnh có đường
> dẫn chứa `photos/`** hoặc link Cloudinary. Nếu để ảnh ở thư mục khác, sách vẫn hiện
> nhưng **màn trái tim sẽ trống**. Vì vậy hãy luôn đặt ảnh người nhận trong `photos/`.

Ảnh mẫu hiện tại (`photos/sample1..6.jpg`) là ảnh ngẫu nhiên — hãy thay bằng ảnh thật.

### Thay nhạc
File `music/birthday-song.mp3` hiện là **nhạc demo tải từ trang gốc** — hãy thay bằng
bài nhạc **bạn có bản quyền/được phép dùng** trước khi công khai.

## ▶️ Xem thử (cần chạy qua web server, không mở trực tiếp file)

```bash
cd ThaoAnh
python3 -m http.server 8000
# mở http://localhost:8000
```
> Nhạc chỉ phát sau khi bấm **"Chạm để bắt đầu"** (trình duyệt chặn tự phát).

## 🚀 Đăng lên mạng (miễn phí)
- **Vercel / Netlify**: kéo–thả cả thư mục `ThaoAnh`, hoặc kết nối GitHub.
- **GitHub Pages**: đẩy lên repo, bật Pages.

## 📂 Cấu trúc
```
index.html          ← trang chính + CONFIG nội dung (sửa ở đây)
index.css           ← style gốc
ui.js               ← điều phối toàn bộ hiệu ứng (giữ nguyên)
clock-reveal.js     ← cảnh đồng hồ neon
birthday-greeting.js← cảnh chúc mừng lớn
settings.js, lang.js, stubs.js ← phụ trợ (giữ nguyên)
image/              ← ảnh hệ thống (theend.jpg = bìa sách; logo.png = favicon)
photos/             ← ẢNH NGƯỜI NHẬN đặt ở đây (bắt buộc cho màn trái tim)
music/              ← nhạc nền
```

## ⚠️ Ghi chú bản quyền
Mã nguồn, ảnh bìa (`theend.jpg`) và nhạc demo lấy từ trang gốc `happy-birthday-love-link`
(tác giả TikTok @iamtritoan) để phục vụ mục đích cá nhân/học tập. Nếu dùng công khai,
hãy tự thay ảnh, nhạc và cân nhắc ghi nguồn cho tác giả gốc.
