# PHIẾU BÀI TẬP 01
# **HTML5 FUNDAMENTALS — Cấu trúc, Semantic, Tables & Links**

---

## PHẦN A — ĐỌC HIỂU

### Câu A1 — HTTP & Browser

#### 1. Khi gõ `https://shopee.vn` vào trình duyệt và nhấn Enter, có 7 bước xảy ra như sau:

**Bước 1**: Trình duyệt nhận URL người dùng nhập

&nbsp;&nbsp;&nbsp;&nbsp; Khi gõ `https://shopee.vn` vào thanh địa chỉ và nhấn Enter. Chrome hiểu rằng bạn đang yêu cầu truy cập website Shopee.

> Nguồn tham chiếu: `01_introduction_html_universe.md` - `Cuộc Hành Trình 0.3 Giây Xuyên Đại Dương`

<br>

**Bước 2**: DNS Lookup – tìm địa chỉ IP của shopee.vn

&nbsp;&nbsp;&nbsp;&nbsp; Đây là bước xác định nơi gửi request.

&nbsp;&nbsp;&nbsp;&nbsp; Trình duyệt cần biết server của shopee.vn nằm ở đâu trên Internet. Vì máy tính không hiểu tên miền, nên nó sẽ tra cứu DNS để đổi `shopee.vn` sang địa chỉ IP của server.

>  Nguồn tham chiếu: `01_introduction_html_universe.md` - `1.1. Kiến trúc Client-Server — "Nhà hàng Online"`

<br>

**Bước 3**: Trình duyệt gửi HTTP Request đến server Shopee

&nbsp;&nbsp;&nbsp;&nbsp; Sau khi biết IP server, trình duyệt gửi yêu cầu HTTP (thường là GET).

> Nguồn tham chiếu: `01_introduction_html_universe.md` - `1.2. HTTP — Ngôn ngữ để Client và Server hiểu nhau`

<br>

**Bước 4**: Request đi qua mạng Internet đến server

&nbsp;&nbsp;&nbsp;&nbsp; Request từ máy tính sẽ đi theo luồng:

&nbsp;&nbsp;&nbsp;&nbsp; `Máy tính - WiFi Router - Nhà mạng - Cáp quang - Server Shopee`

> Nguồn tham chiếu: `01_introduction_html_universe.md` - `Cuộc Hành Trình 0.3 Giây Xuyên Đại Dương`

<br>

**Bước 5**: Server Shopee xử lý yêu cầu

&nbsp;&nbsp;&nbsp;&nbsp; Server nhận request và xử lý:

- kiểm tra route

- lấy HTML trang chủ

- gọi database lấy sản phẩm, banner, flash sale...

- chuẩn bị CSS, JavaScript, hình ảnh

&nbsp;&nbsp;&nbsp;&nbsp; Nếu thành công sẽ trả về: `200 OK`

> Nguồn tham chiếu: `01_introduction_html_universe.md` - `1.2. HTTP — Ngôn ngữ để Client và Server hiểu nhau`

<br>

**Bước 6**: Server gửi HTTP Response về trình duyệt

&nbsp;&nbsp;&nbsp;&nbsp; Server gửi lại dữ liệu cho trình duyệt:

- HTML

- CSS

- JavaScript

- Hình ảnh

- Font chữ

> Nguồn tham chiếu: `01_introduction_html_universe.md` - `Cuộc Hành Trình 0.3 Giây Xuyên Đại Dương`

<br>

**Bước 7**: Trình duyệt render giao diện

&nbsp;&nbsp;&nbsp;&nbsp; Chrome bắt đầu dựng trang theo quy trình trong tài liệu:

- Đọc cấu trúc trang (Parse HTML): header, menu, sản phẩm, banner,...

- Đọc giao diện (Parse CSS): màu cam Shopee, layout grid, font chữ,...

- Chạy chức năng (Execute JS): slider banner, tìm kiếm, đếm giỏ hàng, hiệu ứng flash sale,...

- Vẽ toàn bộ giao diện lên màn hình (Paint & Render)

> Nguồn tham chiếu: `01_introduction_html_universe.md` - `1.3. Browser Rendering — Từ Code thành Hình ảnh`

<br>

#### 2. Trong DevTools của Chrome, tab **Network** cho thấy:
- Các request trình duyệt gửi đi.
- Các response server trả về.
- File nào tải chậm - file nào nặng.
- Thời gian tải từng tài nguyên.
- Tổng số request của website.
> Nguồn tham chiếu: `01_introduction_html_universe.md` - `4.3. Developer Tools (F12) — "Kính hiển vi" cho website`

&nbsp;&nbsp;&nbsp;&nbsp; [Screenshot tab Network](/PBT_01/screenshots/A1-2-Screenshot_tab_Network.png):
- 1 - Status Code của request đầu tiên.
- 2 - Tổng thời gian load trang.
- 3 - Một request trả về file CSS.

<br>

### Câu A2 — Semantic HTML

#### 1. Trang web bị bị Google đánh giá SEO thấp vì dùng toàn `<div>` thay vì semantic tags, Google khó hiểu cấu trúc nội dung của trang.
Google sẽ khó phân biệt:
- Đâu là phần đầu trang.
- Đâu là menu điều hướng.
- Đâu là nội dung chính.
- Đâu là bài viết, sản phẩm.
- Đâu là sidebar.
- Đâu là footer.
Khi công cụ tìm kiếm không hiểu rõ cấu trúc, khả năng đánh giá nội dung giảm => SEO thấp hơn.
> Nguồn tham chiếu: `04_visible_part_html.md` - `Tại sao không dùng <div> cho mọi thứ?`

#### 2. Các lỗi semantic:
- Phần header dùng `<div class="header">` thay vì `<header>`.
- Điều hướng dùng `<div class="menu">` thay vì `<nav>`.
- Nội dung chính dùng `<div class="content">` thay vì `<main>`.
- Sản phẩm dùng `<div class="product">` thay vì `<article>`.
- Sidebar dùng `<div>` thay vì `<aside>`.
- Footer dùng `<div>` thay vì `<footer>`.
> Nguồn tham chiếu: `04_visible_part_html.md` - `Bản đồ Semantic Elements`

Code đã chỉnh sửa:
```html
<header>
    <div class="logo">ShopTLU</div>

    <nav>
        <div><a href="/">Trang chủ</a></div>
        <div><a href="/products">Sản phẩm</a></div>
    </nav>
</header>

<main>
    <article>
        <div class="title">iPhone 16 Pro</div>
        <div class="price">25.990.000đ</div>
        <div class="image">
            <img src="iphone.jpg" alt="iPhone 16 Pro">
        </div>
    </article>

    <aside>
        Sidebar
    </aside>
</main>

<footer>
    © 2026 ShopTLU
</footer>
```

<br>

### Câu A3 — Block vs Inline

#### 1. kết quả hiển thị:
```
Hộp 1
Text A Text B
Hộp 2
Text C Text D
Hộp 3
```

#### 2. Giải thích:
- Thẻ `<div>` là Block Element.
- Thẻ `<span>` là Inline Element.
- Thẻ `<strong>` là Inline Element.
Block Element chiếm cả dòng.
Inline Element chỉ chiếm nội dung.

> Nguồn tham chiếu: `04_visible_part_html.md` - `Block vs Inline — Hai loại element cơ bản`

<br>

### Câu A4 — Table

#### 1. Sự khác nhau giữa `<thead>`, `<tbody>`, `<tfoot>`:

- `<thead>`: Phần đầu bảng (Header)

&nbsp;&nbsp;&nbsp;&nbsp; Dùng để chứa hàng tiêu đề của bảng.

&nbsp;&nbsp;&nbsp;&nbsp; Giúp người xem hiểu dữ liệu phía dưới thuộc cột nào.

- `<tbody>`: Phần thân bảng (Body)

&nbsp;&nbsp;&nbsp;&nbsp; Chứa nội dung chính của bảng.

- `<tfoot>`: Phần cuối bảng (Footer)

&nbsp;&nbsp;&nbsp;&nbsp; Dùng để hiển thị kết quả tổng hợp.

> Nguồn tham chiếu: `05_tables_hyperlinks.md` - `Table — Bảng dữ liệu`

#### 2. Lý do không nên dùng table để tạo layout trang web:

- Table sinh ra để hiển thị dữ liệu, không phải bố cục trang.

- Hiện nay đã có CSS Grid / Flexbox tốt hơn.

- Layout bằng table khó quản lý và thiếu linh hoạt.

- Không đúng semantic HTML.

> Nguồn tham chiếu: `05_tables_hyperlinks.md` - `"Bảng Giá Sản Phẩm Đầu Tiên" — Minh làm trang e-commerce`

<br>

---

## PHẦN B — THỰC HÀNH CODE

### Bài B3 — Debug HTML

- **Lỗi 1**: Dòng 1 — Sai `DOCTYPE` — Sửa thành `<!DOCTYPE html>`
- **Lỗi 2**: Dòng 2 - Thiếu `lang` cho `<html>` - Sửa thành `<html lang="vi">`
- **Lỗi 3**: DÒng 4 - Không đóng thẻ `<title>` - Thêm thẻ đóng `</title>`
- **Lỗi 4**: Dòng 5 - Sai charset - Sửa `utf8` thành `utf-8`
- **Lỗi 5**: Dòng 8 - Sai thẻ đóng `<h1>` - Sửa thẻ đóng thành `</h1>`
- **Lỗi 6**: Dòng 12 - Sai thẻ đóng `<a>` - Đổi thẻ đóng `<a>` thành `</a>`
- **Lỗi 7**: Dòng 12 - Link không rõ ràng - Đổi thành `href="#home"` hoặc `home.html`
- **Lỗi 8**: Dòng 13 - Link không rõ ràng - Đổi thành `href="#products"` hoặc `products.html`
- **Lỗi 9**: Dòng 20 - Thiếu dấu ngoặc kép cho value của `src` - Sửa thành `src="iphone.jpg"`
- **Lỗi 10**: Dòng 20 - Thiếu thuộc tính `alt` cho ảnh - Thêm `alt="iPhone 16 Pro"`
- **Lỗi 11**: Dòng 22 - Sai thứ tự đóng thẻ `<b>` và `<p>` - Sửa thành `<p>Giá: <b>25.990.000đ</b></p>`
- **Lỗi 12**: Dòng 40 - Dùng 2 thẻ `<main>` - Đổi `<main>` thành `<aside>`
- **Lỗi 13**: Dòng 45 - Không đóng thẻ `<p>` - Thêm thẻ đóng `</p>`
- **Lỗi 14**: Dòng 48 - Không đóng thẻ `<html>` - Thêm thẻ đóng `</html>`

[Code đã chỉnh sửa](/PBT_01/code/B3-debug/debug.html)

<br>

### Câu B4 — Phân tích trang web thật

#### 1. Semantic tag:

- 3 thẻ semantic HTML5 mà trang `tiki.vn` sử dụng:

&nbsp;&nbsp;&nbsp;&nbsp; [Thẻ `<header>` bọc các phần logo, searchbox, button trang chủ, button tài khoản, giỏ hàng, địa chỉ giao hàng](/PBT_01/screenshots/B4-Element_screenshot_1.png)

&nbsp;&nbsp;&nbsp;&nbsp; [Thẻ `<main>` bao toàn bộ các phần tử từ banner đến hết trang.](/PBT_01/screenshots/B4-Element_screenshot_2.png)

&nbsp;&nbsp;&nbsp;&nbsp; [Thẻ `<footer>` bao toàn bộ các phần tử từ khối thông tin hỗ trợ khách hàng, về Tiki, hợp tác và liên kết,... đến hết trang.](/PBT_01/screenshots/B4-Element_screenshot_3.png)

- 2 thẻ mà trang không dùng đúng semantic:

&nbsp;&nbsp;&nbsp;&nbsp; [Thẻ `<div>` bao các phần nội dung chính thay vì `<section>`.](/PBT_01/screenshots/B4-Element_screenshot_4.png)

&nbsp;&nbsp;&nbsp;&nbsp; [Thẻ `<div>` bao các card sản phẩm thay vì `<article>`.](/PBT_01/screenshots/B4-Element_screenshot_5.png)

#### 2. `<table>`:

- Không tìm thấy table do trang web sử dụng hệ thống flexbox với các thẻ `<div>` hoặc `<ul>`, `<li>` để dễ làm chủ bố cục và CSS.

#### 3. `<form>`:

- [`<form>` không có `action` và `method`](/PBT_01/screenshots/B4-Element_screenshot_6.png). Vậy nên:

&nbsp;&nbsp;&nbsp;&nbsp; `action` mặc định chứa URL hiện tại của trang web.

&nbsp;&nbsp;&nbsp;&nbsp; `method` mặc định là `GET`.

hoặc có thể trang web thay bằng sự kiện onclick của button `Tiếp tục` và xử lý bằng hàm JavaScript (VD hàm `handleSubmit()`).

- 2 input types được sử dụng là `tel` và `checkbox`.

---

## PHẦN C — SUY LUẬN

### Câu C1 - Thiết kế cấu trúc

[Cấu trúc HTML cho trang chi tiết sản phẩm.](/PBT_01/code/C1-structure/structure.html)

<br>

### Câu C2 - So sánh & Tranh luận

Quan điểm *"dùng `<div>` cho mọi thứ rồi thêm class là đủ”* nghe có vẻ tiện, nhưng về lâu dài lại gây hại nhiều hơn lợi. `<div>` chỉ là thẻ vô nghĩa về mặt ngữ nghĩa, dùng để chia bố cục chung. Trong khi đó, semantic HTML như `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>` giúp trình duyệt hiểu rõ cấu trúc nội dung.

Lý do kỹ thuật đầu tiên là SEO. Công cụ tìm kiếm như Google không chỉ đọc chữ, mà còn phân tích cấu trúc trang. Nếu bài viết được đặt trong `<article>`, menu trong `<nav>`, nội dung chính trong `<main>`,..., bot sẽ xác định phần quan trọng dễ hơn, từ đó hỗ trợ index tốt hơn. Một trang toàn `<div>` khiến cấu trúc mơ hồ và khó đánh giá nội dung.

Lý do thứ hai là Accessibility. Người dùng sử dụng screen reader cần các mốc điều hướng rõ ràng. Khi có `<nav>`, họ có thể nhảy thẳng đến menu; có `<main>`, họ bỏ qua phần header để vào nội dung chính. Nếu tất cả đều là `<div>`, trải nghiệm của người khiếm thị sẽ kém hơn đáng kể.

Ví dụ, thay vì viết `<div class="menu">...</div>`, ta dùng `<nav>...</nav>`. Screen reader sẽ thông báo đây là vùng điều hướng, còn công cụ tìm kiếm hiểu đây là menu chính của trang.

Tuy nhiên, `<div>` vẫn rất phù hợp trong nhiều trường hợp. Chẳng hạn dùng làm wrapper để chia layout, nhóm các phần tử phục vụ CSS Grid/Flexbox, hoặc tạo card giao diện không mang ý nghĩa nội dung riêng.

Tóm lại, semantic HTML là cách viết web đúng chuẩn, dễ bảo trì, thân thiện SEO và hỗ trợ mọi người dùng tốt hơn. `<div>` nên dùng đúng chỗ, không nên thay thế toàn bộ HTML semantics.
