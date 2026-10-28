# BRIEF — Prompts given to the AI Assistant



## Part A: Semantic HTML Refactoring

```
Hãy giúp tôi hoàn thiện duy nhất PART A trong dự án (file index.html và app.js nếu cần).

Yêu cầu công việc cho Part A:
1. Chuyển đổi các thẻ <div> không cần thiết trong `index.html` thành các thẻ Semantic HTML có ý nghĩa phù hợp (như <header>, <main>, <nav>, <section>, <article>, <form>, <fieldset>, <ul>, <li>, <template>,...).
2. BẮT BỘC giữ lại các thẻ <div> đóng vai trò làm khung chứa layout (Grid/Flexbox wrapper). KHÔNG chuyển tất cả thẻ <div> thành <section>.
3. Đảm bảo ô nhập tìm kiếm (<input id="q">) được đặt bên trong một thẻ <form> hợp lệ.
4. Kiểm tra thẻ <template id="card-template"> ở cuối trang chứa đúng cấu trúc mẫu của một thẻ sản phẩm (card).

Ràng buộc kỹ thuật nghiêm ngặt:
- Scope: Chỉ chỉnh sửa 2 file `index.html` và `app.js`. Tuyệt đối KHÔNG sửa hoặc xóa `style.css` và `check.js`.
- Giữ nguyên 100% tất cả các thuộc tính id, class, data-* có sẵn từ starter kit để check.js hoạt động chính xác.
- Không viết code cho phần tương tác B1-B4 trong bước này.

Mục tiêu kiểm tra: Sau khi sửa xong, khi tôi mở trang web trên trình duyệt và gọi hàm `selfCheck()` trong Console, hệ thống phải in ra chính xác dòng chữ "Session 4 self-check: 8/8 passed".
```

## Part B1: Event Delegation for Add Buttons


```
Hãy giúp tôi hoàn thiện DUY NHẤT phần B1 trong file app.js.

Yêu cầu công việc cho B1:
- Bắt sự kiện click vào nút "Add" (.add) để tăng số lượng sản phẩm được chọn trong giỏ hàng và gọi renderCart().
- BẮT BỘC sử dụng Event Delegation: Chỉ gắn 1 event listener duy nhất ('click') lên container cha `#catalogue`. KHÔNG gắn listener riêng lẻ cho từng nút Add.
- Xử lý Sold-out: Nếu nút Add có thuộc tính `disabled` hoặc thẻ sản phẩm hết hàng, bấm vào nút Add KHÔNG làm gì cả.
- KHÔNG viết trước code cho phần B2 (applyFilter), B3 (search form submit) hay B4 (loadMore).

Ràng buộc kỹ thuật:
- Scope: Chỉ chỉnh sửa trong `app.js` (và `index.html` nếu thực sự cần). Tuyệt đối KHÔNG chạm vào `style.css` và `check.js`.
- An toàn XSS: Dùng `textContent` khi cập nhật hiển thị, không dùng `innerHTML`.
- Giữ nguyên DOM: Giữ nguyên tất cả id, class, data-* có sẵn.

Mục tiêu: Bấm nút Add trên sản phẩm hoạt động bình thường qua event listener trên `#catalogue`.
```

## Part B2: Filter as You Type (Search)

```
Dựa trên code B1 hiện tại trong file app.js, hãy viết tiếp DUY NHẤT phần B2.

Yêu cầu công việc cho B2:
- Viết hàm `applyFilter()` để lọc danh sách sản phẩm khi người dùng gõ vào ô tìm kiếm (`#q` / `searchInput`):
  + Tìm kiếm không phân biệt chữ hoa/chữ thường (Case-insensitive).
  + Cập nhật trạng thái thông báo trong `#status` ( statusBox.textContent ):
    * Nếu từ khóa rỗng (`""`): xóa thông báo.
    * Nếu có kết quả: hiển thị `"Showing X of Y products"`.
    * Nếu không tìm thấy: hiển thị `"No products match "..." "`.
- BẮT BỘC dùng `textContent` cho `statusBox` để chống lỗi XSS tuyệt đối (khi nhập chuỗi độc hại như `<img src=x onerror=alert(1)>`).
- Gắn sự kiện `input` vào `searchInput` để gọi `applyFilter()`.
- KHÔNG chỉnh sửa logic B1 đã viết. KHÔNG viết trước B3 và B4.

Ràng buộc kỹ thuật:
- Scope: Chỉ chỉnh sửa `app.js`. Giữ nguyên id, class hiện có.

Mục tiêu: Lọc đúng sản phẩm khi gõ từ khóa, chống XSS thành công.
```

## Part B3: Search Form Submission Protection

```
Dựa trên code B1 và B2 hiện tại trong file app.js, hãy viết tiếp DUY NHẤT phần B3.

Yêu cầu công việc cho B3:
- Bắt sự kiện `'submit'` trên form tìm kiếm (`searchInput.form`).
- Gọi `event.preventDefault()` để ngăn trình duyệt reload/tải lại trang và không đẩy `?q=...` lên thanh URL khi người dùng nhấn phím Enter trong ô tìm kiếm.
- Gọi hàm `applyFilter()` đã có ở B2 để thực hiện lọc sản phẩm khi submit form.
- KHÔNG chỉnh sửa logic B1, B2 đã có. KHÔNG động vào hàm loadMore của B4.

Ràng buộc kỹ thuật:
- Scope: Chỉ chỉnh sửa `app.js` (và `index.html` nếu form search cần điều chỉnh).

Mục tiêu: Nhấn Enter trong ô search không bị load lại trang.
```

## Part B4: Dynamic Cart Total & Load More

```
Dựa trên code B1, B2, B3 hiện tại trong file app.js, hãy viết tiếp phần B4 để hoàn thiện bài tập.

Yêu cầu công việc cho B4:
- Hoàn thiện hàm `renderCart()` để tính đúng Tổng số lượng (`cartCount`) và Tổng số tiền (`cartTotal`) dựa trên tất cả các thẻ `.card` có trong `#catalogue`.
- Đảm bảo khi người dùng bấm nút "Load more" (`#load-more`), các sản phẩm mới (như Belt) được clone từ `<template id="card-template">` và chèn vào `#catalogue`:
  + Khi bấm "Add" trên sản phẩm mới (Belt), số lượng và tổng tiền vẫn được tính toán và cập nhật chính xác nhờ Event Delegation của B1.
  + Đảm bảo hàm `applyFilter()` của B2 vẫn áp dụng đúng cho các sản phẩm mới nạp thêm.

Ràng buộc kỹ thuật:
- Scope: Chỉ chỉnh sửa `app.js`. Dùng `textContent` khi đổ dữ liệu vào template cloned card, không dùng `innerHTML`.

Mục tiêu: Hoàn tất toàn bộ kịch bản kiểm tra `selfCheck()`, B4 tính đúng tổng tiền bao gồm cả các sản phẩm nạp từ Load More.
```