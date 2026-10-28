## 2026-10-28 — Part A: Tối ưu Semantic HTML
Tool: Copilot (Copilot SDK trong VS Code)
Asked for: Cải thiện ngữ nghĩa HTML nhưng giữ nguyên layout, đặt ô tìm kiếm trong form và giữ các id/class hiện có.
Kept: Giữ cấu trúc layout bằng div ở những chỗ chỉ dùng để bố cục; giữ nguyên id/class để CSS, app.js và check.js tiếp tục hoạt động.
Changed: Thay các phần tử bằng landmark, heading, list item, label, form và button HTML phù hợp, bao gồm cả card trong template. Đã chạy `selfCheck()` trong Console và đạt 8/8; xác nhận các kiểm tra landmark, heading, catalogue list, label, search form và button đều qua.
Rejected: Không chuyển các div chỉ làm nhiệm vụ layout thành section; không sửa style.css hoặc check.js vì sẽ làm thay đổi layout hay vô hiệu hóa bài tự kiểm tra.

## 2026-10-28 — Part B1: Event Delegation và sản phẩm hết hàng
Tool: Copilot (Copilot SDK trong VS Code)
Asked for: Thêm sản phẩm vào giỏ bằng một click listener duy nhất trên `#catalogue` và không cho thêm sản phẩm đã hết hàng.
Kept: Dùng event delegation trên `#catalogue`, tìm card và mã sản phẩm từ nút được bấm, rồi cập nhật số lượng giỏ.
Changed: Bỏ qua click không đến từ nút Add hợp lệ và nút bị disabled; kiểm tra trạng thái “Sold out” trước khi cập nhật giỏ. Đối chiếu với README `Done means`, hàng 4 (sản phẩm hết hàng không làm tăng giỏ), hàng 5 (Enter trên nút Add) và hàng 6 (Add sau Load more).
Rejected: Không gắn listener riêng cho từng nút Add vì không xử lý được các nút được tạo sau khi Load more; không thêm Tote bag đã Sold out vào giỏ.

## 2026-10-28 — Part B2: Lọc sản phẩm theo từ khóa
Tool: Copilot (Copilot SDK trong VS Code)
Asked for: Hoàn thiện `applyFilter()` để lọc tên sản phẩm theo từ khóa không phân biệt hoa/thường và hiển thị một dòng trạng thái an toàn.
Kept: Chuẩn hóa từ khóa và tên sản phẩm về chữ thường để so khớp; hiện/ẩn card theo kết quả và xóa trạng thái khi ô tìm kiếm rỗng.
Changed: Ghi nội dung trạng thái bằng `textContent` thay vì diễn giải chuỗi người dùng như HTML, đồng thời hiển thị thông báo phù hợp khi không có kết quả. Đối chiếu với README `Done means`, hàng 7 (scarf/SCARF và ô trống) và hàng 8 (chuỗi thử XSS phải hiển thị nguyên văn, không bật alert hay tạo ảnh lỗi).
Rejected: Không dùng `innerHTML` cho nội dung trạng thái vì chuỗi nhập như `<img src=x onerror=alert(1)>` không được phép chạy như markup hoặc mã.

## 2026-10-28 — Part B3: Ngăn form tìm kiếm tải lại trang
Tool: Copilot (Copilot SDK trong VS Code)
Asked for: Bắt sự kiện submit của form tìm kiếm để nhấn Enter không làm tải lại trang.
Kept: Gắn listener vào form chứa ô tìm kiếm và tiếp tục áp dụng bộ lọc khi gửi form.
Changed: Gọi `event.preventDefault()` trong submit handler trước khi lọc để ngăn hành vi submit mặc định. Đối chiếu với README `Done means`, hàng 9: nhập `cap`, nhấn Enter, địa chỉ không đổi thành `?q=cap` và số lượng giỏ không mất.
Rejected: Không để browser submit form theo mặc định vì sẽ reload trang và làm mất trạng thái giỏ.

## 2026-10-28 — Part B4: Tính tổng giỏ hàng
Tool: Copilot (Copilot SDK trong VS Code)
Asked for: Hoàn thiện `renderCart()` để hiển thị chính xác tổng số lượng và tổng giá trị giỏ hàng, kể cả sản phẩm được thêm sau Load more.
Kept: Tính số lượng từ các mã sản phẩm trong giỏ và cộng giá theo số lượng; định dạng tổng tiền theo locale `vi-VN`.
Changed: Tính tổng dựa trên toàn bộ card hiện có trong `#catalogue`, bao gồm card được Load more thêm vào, rồi cập nhật cả `#cart-count` và `#cart-total`. Đối chiếu với README `Done means`, hàng 4 (số lượng) và hàng 6 (thêm sản phẩm mới sau Load more); kết quả định dạng theo yêu cầu `Cart (3) · 540.000 đ`.
Rejected: Không tính tiền chỉ trên danh sách sản phẩm ban đầu hoặc cộng giá mỗi sản phẩm đúng một lần, vì sẽ bỏ sót sản phẩm Load more hoặc tính sai khi một sản phẩm được thêm nhiều lần.