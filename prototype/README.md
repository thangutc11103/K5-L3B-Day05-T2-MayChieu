# Prototype Hướng dẫn & Minh họa — Nhóm MayChieu (Track T3)

## 1. Cách chạy Prototype
- Mở file `index.html` trực tiếp bằng bất kỳ trình duyệt nào (Google Chrome, Microsoft Edge, Safari, Firefox).
- Không cần cài đặt `node_modules`, không cần chạy web server, không phụ thuộc internet hay API key.

---

## 2. Các tính năng cốt lõi thể hiện trên Prototype

### Ca 1 (Khó nhất): Đòi đổi chuyến tối nay · Bẫy thiếu chỗ cho đoàn
- **Tình huống:** Khách nhắn *"Chuyến huỷ rồi à? Đổi giúp mình chuyến tối nay đi, chuyến nào cũng được đang gấp lắm!"*.
- **Cách AI xử lý:**
  1. Phát hiện chuyến tối nay `BM 217 (21:00)` **chỉ còn đúng 1 chỗ trống**, không đủ cho đoàn 2 khách (Nguyễn Minh An & bé Nguyễn Gia Bình 5 tuổi).
  2. Áp dụng quy tắc an toàn: Không cho phép tách bé 5 tuổi bay một mình.
  3. Áp dụng **HAX G10 (Thu hẹp phạm vi khi nghi ngờ)**: Từ chối đổi liều, đề xuất 2 chuyến sáng mai khả thi (`BM 201` lúc 07:00 còn 9 chỗ; `BM 205` lúc 09:30 còn 4 chỗ).
  4. Tự động kích hoạt tool `giu_cho_chuyen_moi` với **đồng hồ đếm ngược 20:00 phút chạy thật** để giữ chỗ cho khách mà không làm mất lượt đổi vé miễn phí.
  5. Đưa ra thẻ xác nhận 1 chạm: Khách duyệt mới tiến hành đổi chính thức (`doi_chuyen_bay`).
  6. Luôn có nút **Gặp nhân viên hỗ trợ** (PAIR Graceful Failure) với tóm tắt ngữ cảnh tự động.

### Ca 2: Đòi hoàn vé một chiều · Chặn 2 bước (Positive Friction)
- **Tình huống:** Khách bực tức nhắn *"Bực mình quá, huỷ chuyến thế này thì huỷ hết đi, hoàn tiền cho tôi!"*.
- **Cách AI xử lý:**
  1. Nhận diện thao tác hoàn vé là **một chiều không thể đảo ngược** (irreversible).
  2. Không tự động gọi `gui_yeu_cau_hoan_ve`.
  3. Bật Modal cảnh báo 4 hệ quả nghiêm trọng: Mất chỗ, mất quyền đổi vé miễn phí, tiền bị giam 90 ngày, không có bồi thường bão.
  4. Khóa nút gửi cho đến khi người dùng tự tay tích vào checkbox cam kết.

### Ca 3: Lỡ đổi nhầm · Hoàn tác khẩn cấp 10 phút (Emergency Undo)
- **Tình huống:** Minh họa trường hợp ở mức tự chủ cao (hoặc khách bấm nhầm).
- **Cách xử lý:** Cung cấp thanh đếm ngược 10 phút và nút **Hoàn tác khẩn cấp** để thu hồi lệnh đổi, khôi phục lại quyền đổi vé miễn phí ban đầu của khách.

---

## 3. Bản đồ các chú thích HAX / PAIR trên màn hình

| Số | Vị trí trên giao diện | Nguyên tắc HAX / PAIR | Giải thích chi tiết |
|:---:|---|---|---|
| **[1]** | Hộp cảnh báo đỏ phía trên | **HAX G10 (Scope down when in doubt)** | Thu hẹp và từ chối đổi khi phát hiện chuyến 21:00 chỉ còn 1 chỗ trong khi đoàn có trẻ em 5 tuổi. |
| **[2]** | Khung trích dẫn nguồn | **HAX G11 + PAIR Explainability** | Hiển thị rõ căn cứ: Mã PNR, số ghế còn lại của chuyến bay và điều lệ an toàn hàng không. |
| **[3]** | Danh sách chuyến bay gợi ý | **HAX G1 (Năng lực hệ thống)** | Chủ động đề xuất phương án tối ưu nhất thay vì bắt khách tự tìm kiếm. |
| **[4]** | Thẻ đếm ngược màu xanh | **PAIR Control & Reversibility** | Đồng hồ 20:00 đếm ngược giữ chỗ tạm thời; tự nhả sau 20 phút mà không trừ quyền đổi miễn phí. |
| **[5]** | Nút `[Xác nhận đổi sang chuyến này]` | **Mức tự chủ Cần duyệt** | Chặn 100% rủi ro đổi nhầm nhờ một thao tác xác nhận có chủ đích của khách. |
| **[6]** | Nút `[Chọn chuyến 09:30]` | **HAX G9 (Sửa dễ dàng)** | Cho phép thay đổi quyết định trực tiếp ngay trên thẻ chat mà không phải nhập lại từ đầu. |
| **[7]** | Nút `[Gặp nhân viên hỗ trợ]` | **PAIR Graceful Failure** | Chuyển tiếp người thật liền mạch kèm thông tin bối cảnh đã tóm tắt sẵn. |
| **[8]** | Nút `[Thôi, tôi muốn hoàn vé]` | **Chặn thao tác một chiều** | Kích hoạt luồng modal cảnh báo 2 bước chống bốc đồng. |
