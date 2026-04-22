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

