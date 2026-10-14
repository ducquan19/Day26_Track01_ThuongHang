# Lab 26 - AI Adoption Change Management

## Thông tin nhóm

* **Tên nhóm:** Thượng Hạng
* **Dự án:** ShopViết - Trợ lý viết mô tả sản phẩm và trả lời đánh giá cho người bán trên sàn TMĐT
* **Danh sách thành viên:**

|MSSV|Họ và tên|Phần phụ trách|Góp ý đã đưa cho nhóm bạn
|---|---|---|---|
|Đặng Văn Thái Anh|2A202602407|||
|Nguyễn Thị Bảo Trang|2A202602580|||
|Đoàn Quang Thanh|2A202602841|||
|Vũ Quang Tiến|2A202602872|||
|Trần Đức Quân|2A202602922|||

---

## Phạm vi

* **Sản phẩm AI:** ShopViết (Extension/Web Copilot tạo mô tả sản phẩm & phản hồi đánh giá khách hàng).
* **Nhóm người dùng chính:** 50 Chủ shop TMĐT / Nhân viên trực chat & đăng bài (Shopee/TikTok Shop).
* **Quy trình liên quan:** Nhận bài/đánh giá $\rightarrow$ Hỏi ShopViết $\rightarrow$ Lọc từ cấm & Chọn Tone-of-Voice $\rightarrow$ Duyệt & Đăng bài.
* **Vấn đề quan sát được:** Tỷ lệ quay lại dùng $< 20\%$. Người bán ngại dùng AI vì sợ bị dính "Từ cấm của Sàn" gây khóa sản phẩm và câu từ bị generic không đúng văn phong shop.

---

## Nguyên nhân gốc

1. **Về mặt niềm tin & con người (ADKAR - Desire):**
   Người bán có nỗi sợ lớn về rủi ro vận hành (khóa shop, ẩn sản phẩm) khi AI dùng từ ngữ vi phạm chính sách sàn.
2. **Về mặt quản trị & độ sẵn sàng (Gartner-Lite - Readiness):**
   Chưa có Data Owner chịu trách nhiệm cập nhật bộ danh sách từ cấm của các sàn TMĐT định kỳ.

---

## Cách làm mới

* **Nguồn kiểm chứng & lọc an toàn:** Hệ thống tự động chạy qua bộ lọc từ cấm và hiển thị cảnh báo đỏ nếu phát hiện từ nhạy cảm trước khi xuất bản.
* **Người chịu trách nhiệm:** Áp dụng Mollick Framework - AI gợi ý bản nháp; Người bán duyệt/chỉnh sửa 1-click và chịu trách nhiệm 100% nội dung đăng lên sàn.
* **Xử lý khi AI sai/không phù hợp:** Bấm nút *"Đổi Tone-of-Voice"* hoặc *"Báo lỗi từ cấm"* 1-click để AI học và tạo lại câu phản hồi mới trong 3 giây.

---

## Chỉ số

* **Product-level Metric (Tầng 4 - Chất lượng & An toàn):**
  * **Tỷ lệ nội dung không dính Từ cấm Sàn TMĐT $\ge 99.5\%$**
  * *Baseline:* 65% | *Target:* 99.5% | *Nguồn:* RAG Audit Log | *Owner:* Thành viên 2 (AI Engineer)
  * *Hành động khi chỉ số xấu:* Tạm dừng auto-generate, siết chặt thuật toán lọc từ cấm Regex/Vector DB.
* **Workflow-level Metric (Tầng 5 - Giá trị Nghiệp vụ):**
  * **Tỷ lệ bài nháp AI được Người bán chấp nhận ngay $\ge 85\%$**
  * *Baseline:* 35% | *Target:* 85% | *Nguồn:* Báo cáo Chấp nhận Nội dung | *Owner:* Thành viên 3 (Data Expert)
  * *Hành động khi chỉ số xấu:* Cập nhật lại bộ dữ liệu mẫu (Gold Dataset 100+ mẫu) và fine-tune Prompt.

---

## Quyết định

* **Quyết định:** **SỬA (PIVOT/FIX)**
  Tập trung 30 ngày xây dựng Bộ lọc Từ cấm Sàn tự động và tính năng Tùy chỉnh Văn phong trước khi Mở rộng (Rollout).
* **2 Thay đổi lớn trong bản Dashboard v2 so với v1 (sau phản biện chéo):**
  1. **Thay đổi 1:** Chuyển đổi chỉ số Tầng 1 từ *"Số tài khoản đăng nhập"* sang *"Tỷ lệ lượt tạo câu có tùy chỉnh Văn phong (Tone-of-Voice)"*.
  2. **Thay đổi 2:** Bổ sung Product Metric bắt buộc về Tỷ lệ không dính từ cấm sàn ($\ge 99.5\%$) kèm quy trình khóa tính năng nếu vi phạm ngưỡng an toàn.
