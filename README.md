# LAB5 — AI Product UX & Autonomy
## Track T4: Trợ lý Khiếu nại "Hàng không đúng mô tả" trong Trò chuyện với Shopee

**Lớp:** L3A · **Bàn / Zone:** C4 · **Nhóm:** 3 chàng ngự lâm  
**Repository:** `K5-L3A-Day05-T4-3_chang_ngu_lam`

---

### Thành viên nhóm
| Họ và Tên | Mã Học Viên | Phân công vai trò |
|---|---|---|
| Nguyễn Đức Trung | 2A202603423 | Trưởng nhóm: Điều phối, chuẩn hóa lát cắt & phạm vi §1, xây dựng kịch bản rủi ro Lớp ④ và 2 kịch bản đắt nhất §2; thiết kế §3 cho K9, chốt bộ nguyên tắc HAX/PAIR, xây dựng tiêu chí nghiệm thu §6, chuẩn bị kịch bản demo §7 |
| Đỗ Minh Hiếu | 2A202603402 | Thành viên: Phụ trách kịch bản rủi ro Lớp ① Nguồn sự thật, thiết kế §3 cho K1 (2 đường A & B), dựng và tối ưu giao diện Prototype `prototype/index.html` (§5) |
| Nguyễn Huy Thứ | 2A202603356 | Thành viên: Phụ trách kịch bản rủi ro Lớp ② & ③, thiết kế toàn bộ mức tự chủ 5 tool §4, đề xuất giải pháp tách tool `soan_hoan_tien` và kiểm thử mức tự chủ trên 3 kịch bản |
| Bùi Văn Lâm | 2A202603400 | Thành viên: Rà soát kiến trúc Prototype đối chiếu tiêu chuẩn Rubric R5, lập bảng chú thích số ①–⑪, chụp ảnh minh chứng giao diện và phụ trách kịch bản ứng phó ca lạ (§7) |

> [!NOTE]
> Nhóm gồm 4 thành viên theo phân bổ và xác nhận của trợ giảng (TA) tại lớp L3A.

---

### Cấu trúc bài nộp
* **[spec.md](spec.md):** Bản đặc tả hoàn chỉnh gồm 7 phần (§1 Lát cắt & Phạm vi, §2 Kịch bản rủi ro, §3 Khi AI sai, §4 Mức tự chủ, §5 Prototype, §6 Tốt là gì, §7 Kế hoạch Demo & Ca lạ).
* **[prototype/index.html](prototype/index.html):** Màn hình kép tương tác (Dual-Screen) mô phỏng song song Người mua (Shopee App Chat) và Bàn duyệt hai bên (Kênh Người Bán & Trưởng nhóm sàn). Chạy trực tiếp trên trình duyệt, không cần server hay API key.
* **[ai_log.md](ai_log.md):** Nhật ký chi tiết toàn bộ các phiên làm việc của AI, ghi nhận đóng góp của từng thành viên và quá trình tinh chỉnh đối soát tiêu chuẩn Rubric.

---

### Hướng dẫn chạy và Demo Prototype (Dưới 30 giây)
1. Mở trực tiếp file `prototype/index.html` bằng trình duyệt (Google Chrome, Microsoft Edge, Safari, Firefox).
2. Tại thanh điều khiển **CA DEMO** trên cùng, chọn các kịch bản:
   * **K1 · mô tả bị sửa (có bản lưu):** Kịch bản đắt nhất 1 (Người mua đúng, AI đối chiếu snapshot).
   * **K1 · không có bản lưu:** Kịch bản đắt nhất 1 - Đường B (Thiếu dữ liệu, AI hạ độ chắc và chuyển người).
   * **K9 · doạ bóc phốt:** Kịch bản đắt nhất 2 (Khách đe dọa bóc phốt, AI giữ trung lập, chặn giải ngân tức thì).
   * **Ca lạ (tự gõ):** Nhập tin nhắn bất kỳ (ví dụ: xin số điện thoại, đòi khóa shop, đòi đền tiền mặt...).
3. Bấm nút **"Chú thích số"** trên thanh công cụ để hiển thị các ghim số ① đến ⑪ trỏ trực tiếp vào các nguyên tắc HAX/PAIR và mức tự chủ.
4. Bấm **"Gửi"** -> gửi ảnh đối chiếu -> chuyển sang **Màn 2 (Bàn duyệt)** để người bán bấm [Đồng ý] hoặc [Phản đối], và Trưởng nhóm sàn đưa ra phán quyết cuối cùng.
