# MEMO QUYẾT ĐỊNH: TÁI THIẾT KẾ WORKFLOW & THUẬT TOÁN ỨNG DỤNG AI - SHOPVIẾT

**Dự án:** ShopViết - Trợ lý viết mô tả sản phẩm và trả lời đánh giá cho người bán trên sàn TMĐT

---

## 1. Vấn đề & nguyên nhân gốc

* **Hiện trạng & triệu chứng:** Trợ lý ShopViết đã triển khai thử nghiệm cho 50 shop TMĐT, nhưng tỷ lệ sử dụng thường xuyên chỉ đạt $< 20\%$. Các chủ shop vẫn giữ thói quen tự gõ tay mô tả sản phẩm và bỏ qua các đánh giá 1-3 sao của khách hàng.

* **Nguyên nhân gốc:** Vấn đề không phải do người bán lười biếng hay không biết dùng AI, mà do **thiếu độ tin cậy và nỗi sợ rủi ro vận hành**:
  1. Người bán sợ AI sinh ra các "Từ cấm của Sàn" (như *tuyệt đối, 100%, trị dứt điểm, cam kết...*) dẫn đến việc bị Shopee/TikTok Shop phạt ẩn sản phẩm hoặc khóa shop.
  2. Văn phong AI quá chung chung, không giữ được bản sắc riêng của từng shop.

---

## 2. Framework và bằng chứng

* **Áp dụng Frameworks:**
  * **ADKAR Model:** Nghẽn ở **Desire**. Người bán lo ngại rủi ro khóa shop. Việc mở lớp hướng dẫn Prompting (Knowledge) không giải quyết được nếu hệ thống thiếu bộ lọc an toàn.
  * **Gartner-Lite Assessment:** Dự án có **Direction** tốt (giảm 35% thời gian) nhưng thiếu **Readiness** (chưa có Data Owner quản lý bộ từ cấm Sàn) và **Absorption** (chưa có cơ chế Human-in-the-loop để người bán duyệt nhanh).
  * **Mollick Framework:** Định hình lại mô hình Copilot - AI đóng vai trò lọc từ cấm & tạo bản nháp; Người bán giữ quyền duyệt 1-click và chịu trách nhiệm 100% nội dung xuất bản.

* **Bằng chứng thực tế đính kèm:**
  Log hệ thống cho thấy 75% lượt hủy không sử dụng bài viết của AI xảy ra khi phát hiện AI dùng từ ngữ vi phạm chính sách Shopee. Phỏng vấn 3 Top Sellers: *"Thà viết chậm một chút còn hơn dùng AI rồi bị sàn quét khóa sản phẩm đang chạy FSK (Flash Sale)"*.

---

## 3. Các thay đổi quan trọng sau phản biện chéo

Sau phiên phản biện ở Chặng 3 với nhóm, Team Thượng Hạng đã cập nhật 2 thay đổi cốt lõi từ Dashboard v1 sang v2:

1. **Thay đổi 1:**
   Chuyển đổi chỉ số Tầng 1 từ *"Số tài khoản đăng nhập"* (Activity metric) sang *"Tỷ lệ lượt tạo câu có tùy chỉnh Văn phong (Tone-of-Voice)"* để đo lường thực chất mức độ cá nhân hóa niềm tin.
2. **Thay đổi 2:**
   Bổ sung Product Metric bắt buộc: *"Tỷ lệ nội dung không dính từ cấm Sàn $\ge 99.5\%$"*. Nếu chỉ số này tụt dưới 98%, AI Engineer bắt buộc phải khóa tính năng Auto-submit và kích hoạt chế độ kiểm duyệt thủ công kép.

---

## 4. Quyết định

* **Quy tắc quyết định:** **SỬA (PIVOT/FIX)**
* **Lý do:** Hướng đi thị trường hoàn toàn chính xác, nhưng hệ thống cần 30 ngày tập trung gia cố bộ lọc an toàn từ cấm và tính năng Tùy chỉnh Văn phong trước khi mở rộng quy mô.

---

## 5. Bước tiếp theo & lộ trình 30-60-90 ngày

* **Lộ trình thực thi:**
  * **0-30 ngày:** Nhúng bộ dữ liệu 200+ Từ cấm Sàn; tích hợp nút chọn Tone-of-Voice 1-click; chỉ định Data Owner cập nhật thuật toán sàn. *(Gate 30: 100% bài viết qua bộ lọc từ cấm)*.
  * **31-60 ngày:** Chạy thử nghiệm với 20 Top Sellers ngành Thời trang/Mỹ phẩm; kiểm tra xác suất 20% bài đăng hàng tuần. *(Gate 60: Tỷ lệ chấp nhận bài nháp không cần sửa $> 80\%$)*.
  * **61-90 ngày:** Mở rộng cho 100+ shop và đo lường thời gian tiết kiệm thực tế. *(Gate 90: Tỷ lệ sử dụng tự nhiên $> 75\%$)*.
