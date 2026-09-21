# [Thực hành] CSS | flex-wrap property

Dự án thực hành chuyên sâu về thuộc tính **`flex-wrap`** trong **CSS Flexible Box Layout Module (Flexbox)**, bao gồm tài liệu lý thuyết chuẩn W3C, bộ giả lập tương tác trực quan (Interactive Live Playground), ma trận so sánh 4 giá trị đồng thời, các ví dụ độc lập và ứng dụng thực tế trong thiết kế giao diện web responsive hiện đại.

---

## 📌 1. Giới Thiệu Thuộc Tính `flex-wrap`

Thuộc tính **`flex-wrap`** trong CSS được sử dụng để chỉ định xem các phần tử con bên trong (**flex items**) bắt buộc phải nằm trên một hàng duy nhất hay được phép tự động bọc (ngắt dòng) thành nhiều hàng khi không gian của **flex container** không còn đủ chứa.

Mặc định trong Flexbox, các flex item sẽ cố gắng co lại (`flex-shrink`) để vừa vặn trên một hàng duy nhất. Thuộc tính `flex-wrap` giúp người lập trình kiểm soát hành vi bẻ dòng này để tạo nên các bố cục thích ứng (responsive) hoàn hảo.

---

## ⚙️ 2. Cú Pháp & Các Giá Trị Thuộc Tính

### Cú pháp tổng quát:

```css
flex-wrap: nowrap | wrap | wrap-reverse | initial | inherit;
```

### Bảng phân tích chi tiết các giá trị:

| Giá trị            | Loại                 | Diễn giải cơ chế hoạt động                                                                                                                            | Hướng trục phụ (Cross-Axis) |
| ------------------ | -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------- |
| **`nowrap`**       | _Mặc định (Default)_ | Không bọc dòng. Tất cả flex item bị ép nằm trên **1 dòng duy nhất**. Item sẽ co nhỏ lại theo `flex-shrink` hoặc tràn ra ngoài container (_overflow_). | Không có đa dòng            |
| **`wrap`**         | _Phổ biến_           | Cho phép bọc thành nhiều dòng. Khi vượt quá chiều rộng container, item sẽ tự động chuyển sang dòng mới theo chiều tự nhiên từ trên xuống dưới.        | Top → Bottom (với `row`)    |
| **`wrap-reverse`** | _Đảo chiều_          | Cho phép bọc thành nhiều dòng nhưng **đảo ngược chiều của trục phụ**. Dòng mới sẽ được xếp ngược từ dưới lên trên (dòng 1 ở đáy, dòng 2 ở trên).      | Bottom → Top (với `row`)    |
| **`initial`**      | _Từ khóa chuẩn W3C_  | Đưa giá trị thuộc tính trở về giá trị mặc định ban đầu được chỉ định bởi W3C (`nowrap`).                                                              | Không có đa dòng            |
| **`inherit`**      | _Kế thừa_            | Nhận giá trị `flex-wrap` từ phần tử cha trực tiếp.                                                                                                    | Theo cha                    |

---

## 💡 3. Thuộc Tính Viết Tắt (Shorthand): `flex-flow`

CSS cung cấp thuộc tính viết tắt **`flex-flow`** kết hợp giữa `flex-direction` và `flex-wrap`:

```css
/* Cú pháp: flex-flow: <'flex-direction'> <'flex-wrap'>; */

.container {
  display: flex;
  flex-flow: row wrap; /* Xếp hàng ngang và tự bọc dòng */
}

.chat-box {
  display: flex;
  flex-flow: row wrap-reverse; /* Hàng ngang bọc ngược lên trên */
}
```

---

## 🎯 4. Mối Liên Hệ Giữa `flex-wrap` và `align-content`

> **Lưu ý quan trọng của CSS Flexbox:**
> Thuộc tính **`align-content`** căn chỉnh khoảng cách giữa các **hàng flex** dọc theo trục chéo (cross-axis).
> Thuộc tính này **CHỈ CÓ HIỆU LỰC** khi flex container có nhiều hàng – tức là khi:
> `flex-wrap: wrap` hoặc `flex-wrap: wrap-reverse` được kích hoạt và có ít nhất 2 hàng phần tử được tạo ra.
> Nếu `flex-wrap: nowrap` (chỉ có 1 dòng), thuộc tính `align-content` sẽ bị bỏ qua và bạn cần dùng `align-items`.

---

## 📁 5. Cấu Trúc Mã Nguồn Trong Dự Án

```text
thuc-hanh-CSS-flex-wrap-property/
│
├── index.html       # Cổng thông tin tổng hợp: lý thuyết, bộ giả lập playground, so sánh và trắc nghiệm
├── vidu1.html       # Ví dụ chuyên sâu về flex-wrap: nowrap (minh họa flex-shrink và overflow)
├── vidu2.html       # Ví dụ chuyên sâu về flex-wrap: wrap (kết hợp align-content và gap)
├── vidu3.html       # Ví dụ chuyên sâu về flex-wrap: wrap-reverse (thuật toán xác định thứ tự hàng)
├── vidu4.html       # Ví dụ chuyên sâu về flex-wrap: initial (W3C reset & computed style)
└── README.md        # Tài liệu hướng dẫn & giải thích chi tiết
```

---

## 🚀 6. Hướng Dẫn Chạy & Thử Nghiệm

1. **Khởi chạy trực tiếp:**
   - Mở bất kỳ tệp HTML nào (`index.html`, `vidu1.html`, `vidu2.html`, ...) trực tiếp trên trình duyệt hiện đại (Chrome, Edge, Firefox, Safari).
   - Hoặc sử dụng extension **Live Server** trong VS Code để trải nghiệm hot-reload.

2. **Thao tác trên bộ giả lập (`index.html`):**
   - Chuyển đổi giữa 4 giá trị `nowrap`, `wrap`, `wrap-reverse`, `initial`.
   - Điều chỉnh thanh trượt **Độ rộng container** để xem items tự nhảy hàng theo thời gian thực.
   - Thay đổi các giá trị `align-content` và `justify-content` để quan sát sự tương tác bố cục.
   - Nhấn nút **"Sao chép CSS"** để lấy ngay đoạn mã đã tùy biến.

---
