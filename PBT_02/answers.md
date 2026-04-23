# PHIẾU BÀI TẬP 02
# **HTML5 FORMS & MEDIA — Biểu mẫu, Validation & Đa phương tiện**

---

## PHẦN A — ĐỌC HIỂU

### Câu A1 — Input Types

1. `type="email"` &rightarrow; Ô nhập email. Tự kiểm tra đúng định dạng email (có @, domain...) &rightarrow; Dùng cho form đăng ký / đăng nhập tài khoản.

2. `type="password"` &rightarrow; Ô nhập mật khẩu, ký tự bị ẩn bằng dấu chấm. Có thể kết hợp `required`, `minlength`, `pattern` để kiểm tra độ mạnh mật khẩu &rightarrow; Dùng cho form đăng ký / đăng nhập.

3. `type="text"` &rightarrow; Ô nhập text một dòng. Không tự kiểm tra định dạng riêng nhưng hỗ trợ `required`, `minlength`, `maxlength`, `pattern` &rightarrow; Dùng để nhập các trường dữ liệu như họ tên, địa chỉ,... trong form thông tin cá nhân hay form đặt hàng.

4. `type="number"` &rightarrow; Ô nhập số, trình duyệt thường có nút tăng/giảm giá trị. Kiểm tra chỉ cho nhập số, hỗ trợ `min`, `max`, `step` &rightarrow; Dùng để nhập số lượng trong đặt hàng, form thông tin sản phẩm,....

5. `type="tel"` &rightarrow; Ô nhập số điện thoại. Không kiểm tra chuẩn số điện thoại quốc tế mặc định nhưng hỗ trợ `pattern` &rightarrow; Dùng để nhập số điện thoại trong form thông tin cá nhân hay form đặt hàng.

6. `type="date"` &rightarrow; Ô chọn ngày với lịch. Kiểm tra định dạng ngày hợp lệ, hỗ trợ `min`, `max` &rightarrow; Dùng để chọn ngày sinh trong form thông tin cá nhân hay ngày giao hàng dự kiến trong form chi tiết đơn hàng.

7. `type="url"` &rightarrow; Ô nhập đường link. Tự kiểm tra định dạng URL hợp lệ (`http://`, `https://`) &rightarrow; Dùng để nhập link video review sản phẩm trong form chi tiết sản phẩm.

8. `type="file"` &rightarrow; Nút chọn tệp từ máy tính để upload. Hỗ trợ giới hạn loại file bằng `accept`, nhiều file bằng `multiple` &rightarrow; Dùng để upload ảnh sản phẩm trong form chi tiết sản phẩm hoặc ảnh đại diện người dùng trong form thông tin cá nhân.

9. `type="search"` &rightarrow; Ô tìm kiếm. Không có validation đặc biệt &rightarrow; Dùng làm ô kiếm sản phẩm trong trang sản phẩm.

10. `type="range"` &rightarrow; Thanh trượt (slider) để kéo chọn giá trị. Hỗ trợ `min`, `max`, `step` &rightarrow; Dùng để lọc khoảng giá sản phẩm trong trang sản phẩm.

<br>

### Câu A2 — Validation Attributes

Khi user bấm Submit, trình duyệt sẽ chạy HTML5 form validation built-in trước. Nếu có ô không hợp lệ, form không gửi đi, focus vào ô lỗi và hiện thông báo mặc định của browser.

1. TH1:

```html
<input type="text" required value="">
```

&rightarrow; Không submit được do thuộc tính `required` nghĩa là bắt buộc nhập. Giá trị hiện tại rỗng ("") nên vi phạm rule.

[Screenshot kết quả validation thực tế.](/PBT_02/screenshots/A2-Name.png) &rightarrow; Đúng với dự đoán.

<br>

2. TH2:
```html
<input type="email" value="abc">
```

&rightarrow; Không submit được do `type="email"` tự kiểm tra định dạng email. `value="abc"` không có `@`, không có domain nên không hợp lệ.

[Screenshot kết quả validation thực tế.](/PBT_02/screenshots/A2-Email.png) &rightarrow; Đúng với dự đoán.

<br>

3. TH3:
```html
<input type="number" min="1" max="10" value="15">
```

&rightarrow; Không submit được do `max="10"` giới hạn tối đa là **10**. `value="15"` vượt giới hạn.

[Screenshot kết quả validation thực tế.](/PBT_02/screenshots/A2-Age.png) &rightarrow; Đúng với dự đoán.

<br>

4. TH4:
```html
<input type="text" pattern="[0-9]{10}" value="abc123">
```

&rightarrow; Không submit được do `pattern="[0-9]{10}"` nghĩa là phải nhập **đúng 10 chữ số liên tiếp** (`[0-9]`: bất kỳ chữ số nào từ 0 đến 9; `{10}`: 10 lần). `value="abc123"` có chữ cái, chỉ 6 ký tự, không đủ 10 chữ số.

[Screenshot kết quả validation thực tế.](/PBT_02/screenshots/A2-Phone_number.png) &rightarrow; Đúng với dự đoán.

<br>

5. TH5:
```html
<input type="password" minlength="8" value="123">
```

&rightarrow; Vẫn submit được do `minlength="8"` không kiểm tra giá trị được đặt sẵn bằng thuộc tính `value` trong HTML khi trang vừa load mà chủ yếu áp dụng khi người dùng thực sự chỉnh sửa dữ liệu. Nếu người dùng chỉnh sửa dữ liệu, form sẽ không submit được do `minlength="8"` yêu cầu ít nhất 8 ký tự. `value="123"` chỉ có 3 ký tự.

[Screenshot kết quả validation thực tế.](/PBT_02/screenshots/A2-Password.png) &rightarrow; Đúng với dự đoán.

<br>

### Câu A3 — Accessibility

1. `<label for="email">` quan trọng cho người dùng screen reader vì giúp liên kết tên mô tả với ô nhập liệu. Từ đó người dùng dùng biết đây là ô nhập gì.

<br>

2. Dùng `<fieldset>` + `<legend>` khi có nhiều input thuộc cùng một nhóm thông tin.

&nbsp;&nbsp;&nbsp;&nbsp;  VD cụ thể thông tin giao hàng:

```html
<fieldset>
    <legend>Thông tin giao hàng</legend>

    <label for="name">Họ tên</label>
    <input id="name">

    <label for="phone">Số điện thoại</label>
    <input id="phone">

    <label for="address">Địa chỉ</label>
    <input id="address">
</fieldset>
```

<br>

3. `aria-label` dùng khi không có text hiển thị trên màn hình, nhưng vẫn cần tên cho screen reader.

&nbsp;&nbsp;&nbsp;&nbsp; VD icon button chỉ chứa icon, nhưng screen reader cần text để đọc. screen reader sẽ không biết nút đó để làm gì trừ khi có `aria-label`.

```html
<button aria-label="Tìm kiếm">giả sử icon kính lúp ở đây</button>
```

&nbsp;&nbsp;&nbsp; Không nên dùng `aria-label` khi đã có `<label>` vì:

- Gây trùng thông tin, ghi đè label thật làm screen reader đọc không như mong muốn.

- Code thừa.

<br>

### Câu A4 - Media

1. Thuộc tính `loading="lazy"` trên thẻ `<img>` trì hoãn tải ảnh cho đến khi ảnh gần xuất hiện trong viewport của người dùng.

&rightarrow; Cải thiện tốc độ tải trang.

&nbsp;&nbsp;&nbsp; Không nên dùng `loading="lazy"` khi đó là ảnh đầu trang, logo quan trọng xuất hiện ngay khi mở trang.

<br>

2. Nên cung cấp nhiều `<source>` trong thẻ `<video>` vì mỗi trình duyệt hỗ trợ codec/format khác nhau. Nếu browser không phát được format đầu tiên, nó sẽ thử format tiếp theo. Từ đó giúp tương thích nhiều trình duyệt và tối ưu chất lượng và dung lượng.

&nbsp;&nbsp;&nbsp;&nbsp; Ba format video web phổ biến:

- `MP4`: Phổ biến nhất, đăng tải đa nền tảng.

- `WebM`: Khả năng nén tốt. Dùng khi cần tối ưu hóa tốc độ tải trang.

- `MOV`: Không nén hoặc nén tốt. Dùng khi ưu tiên chất lượng hình ảnh cao nhất.

<br>

3. Thuộc tính `alt` trên `<img>` dùng để:

- Hiển thị text thay thế tại vị trí ảnh khi trang không load được ảnh.

- Screen reader đọc nội dung để người dùng hiểu hình ảnh đó đang hiển thị gì.

&nbsp;&nbsp;&nbsp;&nbsp; `alt` tốt cho 3 trường hợp:

- Ảnh sản phẩm iPhone 16

```html
<img src="" alt="Mặt sau iPhone 16 màu đen">
```

- Ảnh trang trí (decorative)

```html
<!-- Nếu chỉ để đẹp, không mang nội dung thì không dùng alt để screen reader bỏ qua -->
<img src="" alt="">
```

- Ảnh biểu đồ doanh thu Q1/2026

```html
<img src="" alt="Biểu đồ cột hiển thị doanh thu quý 1 năm 2026, ghi nhận mức tăng trưởng 15% so với cùng kỳ năm trước">
```

<br>

### Câu A5 - So sánh `<figure>` vs `<img>`

Dùng Cách 1 (`img`) khi ảnh chỉ là nội dung hình ảnh đơn lẻ, không cần chú thích hiển thị kèm theo.

- VD1: Avatar user trong comment

```html
<img src="avatar.jpg" alt="Ảnh đại diện của Minh">
<span>Minh (22/04/2026)</span>
<p>Sản phẩm tốt!</p>
```

- VD2: Logo

```html
<img src="logo.svg" alt="">
```

<br>

Dùng Cách 2 (`figure` + `figcaption`) khi ảnh là một khối nội dung độc lập và cần mô tả liên quan trực tiếp.

- VD1: Ảnh sản phẩm trong phần chi tiết sản phẩm

```html
<figure>
    <img src="iPhone16.jpg" alt="iPhone 16 Pro Max màu Titan">
    <figcaption>iPhone 16 Pro Max 256GB màu Titan — <span style="color: red;">25.990.000đ</span></figcaption>
</figure>
```

- VD2: Ảnh trình bày biểu đồ trong báo cáo

```html
<figure>
    <img src="q1_2026.jpg" alt="Biểu đồ cột hiển thị doanh thu quý 1 năm 2026, ghi nhận mức tăng trưởng 15% so với cùng kỳ năm trước">
    <figcaption>Biểu đồ doanh thu Q1/2026</figcaption>
</figure>
```

<br>

---

## PHẦN B — THỰC HÀNH CODE

### Bài B1 — Form Đăng ký Tài khoản

HTML không thể validate confirm password vì validation mặc định của HTML chỉ kiểm tra từng input riêng lẻ, không so sánh giá trị giữa hai ô khác nhau. Vậy nên HTML không thể tự kiểm tra ô confirm password có trùng với password hay không.