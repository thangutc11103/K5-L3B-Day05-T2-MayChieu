# Prototype Hướng dẫn & Minh họa — Nhóm MayChieu (Track T2: Giáo dục)

## 1. Cách chạy Prototype
- Mở file `index.html` trực tiếp bằng bất kỳ trình duyệt nào (Google Chrome, Microsoft Edge, Safari, Firefox).
- Không cần cài đặt `node_modules`, không cần chạy server cục bộ, chạy mượt mà ngay trên máy.

---

## 2. Các tính năng cốt lõi thể hiện trên Prototype

### Ca 1 (Khó nhất): Học viên xin giải hộ Bài tập 3 đang mở lúc 23:15 đêm muộn
- **Tình huống:** Học viên nhắn *"Chỉ em cách giải câu a Bài tập 3 với, tính trung bình và trung vị của 8 người lương: 9, 10, 10, 11, 12, 12, 13, 45 ra bao nhiêu vậy ạ?"*.
- **Cách AI xử lý:**
  1. Nhận diện Bài tập 3 đang mở (hạn 13/11 23:59).
  2. Áp dụng **HAX G1 & G2 (Năng lực & Giới hạn)**: Từ chối đưa đáp số hoặc giải hộ để ngăn chặn việc chép bài đối phó.
  3. Áp dụng **HAX G11 (Căn cứ minh bạch)**: Trích dẫn chính xác mã mục §3.1 và §3.2 trong tài liệu Buổi 3.
  4. Hướng dẫn theo **phương pháp Socratic (Gia sư gợi mở)**: Đưa ra câu hỏi từng bước: *"Dãy số đã xếp thứ tự, 2 số ở vị trí 4 và 5 là 11 và 12, trung vị của chúng là bao nhiêu?"*.
  5. Học viên bấm trả lời $\rightarrow$ AI xác nhận và gợi ý tiếp câu b.
  6. Luôn có nút **Gửi câu hỏi cho TA** (PAIR Graceful Failure) với thông báo giờ phản hồi (08:00 sáng mai).

### Ca 2: Phát hiện điểm nghi vấn trong tài liệu Buổi 3 (§3.3)
- **Tình huống:** Học viên hỏi *"Em đọc ở §3.3 thấy ghi 'Vì là căn bậc hai, độ lệch chuẩn luôn nhỏ hơn phương sai', tại sao lại như vậy ạ?"*.
- **Cách AI xử lý:**
  1. Áp dụng **HAX G10 (Không nguỵ biện khi nghi ngờ)**: AI không cố bịa lý lẽ để bảo vệ tài liệu sai.
  2. Đưa ra phản chứng toán học rõ ràng: Nếu phương sai $\sigma^2 = 0.25 < 1$ thì độ lệch chuẩn $\sigma = 0.5 > 0.25$.
  3. Tự động tạo phiếu `#TK-303` chuyển cho Giảng viên đính chính giáo trình.
  4. **CẤM AI tự ý đăng lên FAQ chung**: Không lan truyền kiến thức nghi vấn ra toàn lớp.

### Ca 3: Học viên hỏi kiến thức ngoài phạm vi Buổi 3
- **Tình huống:** Học viên hỏi p-value ở Slide 12.
- **Cách AI xử lý:**
  1. Chỉ rõ tài liệu Buổi 3 không có Slide đánh số (chỉ có §3.1 đến §3.5).
  2. Tra cứu đề cương, báo rõ p-value thuộc Buổi 7.
  3. Khuyên học viên tập trung vào Thống kê mô tả Buổi 3 để không bị quá tải.

### Ca 4 (Bonus): Giao diện kiểm duyệt của Trợ giảng (TA Queue)
- Thể hiện trực quan mức tự chủ **CẤM AI tự động gọi lệnh `dang_FAQ`**.
- TA xem xét phiếu `#TK-303` do học viên phát hiện ở Ca 2, kiểm tra nội dung và bấm duyệt để xuất bản lên FAQ chung của toàn lớp.

---

## 3. Bản đồ chú thích HAX / PAIR trên màn hình

| Số | Vị trí trên giao diện | Nguyên tắc HAX / PAIR | Giải thích chi tiết |
|:---:|---|---|---|
| **[1]** | Khung cảnh báo màu vàng | **HAX G1 & G2 (Năng lực & Giới hạn)** | Minh bạch chính sách: Không đưa đáp số bài tập đang mở để giữ vững liêm chính học thuật. |
| **[2]** | Khung trích dẫn màu tím | **HAX G11 + PAIR Explainability** | Trích dẫn chính xác mã mục giáo trình (§3.1, §3.2) để học viên tự kiểm chứng. |
| **[3]** | Đoạn văn bản dẫn dắt | **Phương pháp Socratic** | Đặt câu hỏi định hướng tư duy từng bước thay vì làm hộ người học. |
| **[4]** | Nút bấm trả lời | **HAX G9 (Tương tác từng bước)** | Người học tương tác bước 1 mới được gợi ý bước 2. |
| **[5]** | Nút chuyển hướng nội dung | **PAIR Feedback & Control** | Cho phép người học tự điều tiết nhịp độ học tập (chuyển sang phần Trung bình). |
| **[6]** | Nút `[Gửi câu hỏi cho TA]` | **PAIR Graceful Failure** | Lối thoát an toàn khi bế tắc lúc nửa đêm (23:15), thông báo giờ TA phản hồi. |
