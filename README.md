# Đôi Ta

Ứng dụng web (cài được lên màn hình điện thoại) cho hai người yêu nhau:

- **Thấy vị trí của nhau** khi mở app, kèm thời gian cập nhật, khoảng cách, pin (Android).
- **Hai bên cùng đồng ý:** một người tạo cặp và gửi link mời, người kia bấm Đồng ý. Luôn có dòng "Đang chia sẻ vị trí", có nút Tạm dừng và Rời cặp.
- **🔔 Nhờ cập nhật:** người kia mở app sẽ thấy lời nhắn và gửi vị trí ngay.
- **Nơi đôi ta đến:** lưu quán ăn, cà phê, chỗ vui chơi, danh sách "Muốn đi"; mỗi người tự chấm 1–5 sao và ghi chú.

Giới hạn: là app web nên điện thoại chỉ gửi vị trí khi app đang mở.

## Chạy thử không cần máy chủ

Mở `index.html?demo=1`: dữ liệu chỉ lưu trong máy, có sẵn một "người yêu" giả.

## Máy chủ

Dùng Firestore (đăng nhập ẩn danh) qua REST, cấu hình ở đầu `index.html` (`FB`). Dữ liệu:

- `doita/{mã cặp}`: `members` (tối đa 2 uid), `ping_<uid>`
- `doita/{mã cặp}/loc/{uid}`: vị trí cuối của từng người
- `doita/{mã cặp}/places/{id}`: địa điểm, điểm sao `r_<uid>`

Luật bảo mật cần dán vào Firebase console: xem `firestore.rules`.
