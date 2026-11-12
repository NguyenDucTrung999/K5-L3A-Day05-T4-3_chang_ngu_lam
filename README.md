# LAB5 — AI Product UX & Autonomy
## Track T4: Trợ lý Khiếu nại "Hàng không đúng mô tả" trong Trò chuyện với Shopee

**Lớp:** L3A · **Bàn / Zone:** C4 · **Nhóm:** 3 chàng ngự lâm  
**Repository:** `K5-L3A-Day05-T4-3_chang_ngu_lam`

---

### Thành viên nhóm
| Họ và Tên | Mã Học Viên | Phân công vai trò |
|---|---|---|
| Nguyễn Đức Trung | [Điền mã học viên] | Trưởng nhóm: Lát cắt & phạm vi (§1), Kịch bản rủi ro Lớp ④ và thuyết minh mở đầu (§7) |
| Bùi Văn Lâm | 2A202603400 | Thành viên: Kiến trúc hệ thống, xây dựng Prototype tương tác (§5), điều khiển demo ca khó (#4) |
| Đỗ Minh Hiếu | [Điền mã học viên] | Thành viên: Phân bổ mức tự chủ theo Cost-of-error (§4), Ca đắt nhất #5 |
| Nguyễn Huy Thụ | 2A202603356 | Thành viên: Thiết kế trải nghiệm HAX/PAIR (§3), Ứng phó ca lạ (§7) |

---

### Cấu trúc bài nộp
* **[spec.md](file:///c:/Users/OS/Downloads/VinAI/K5-L3A-Day05-T4-3_chang_ngu_lam/spec.md):** Bản đặc tả hoàn chỉnh gồm 7 phần (§1 Lát cắt, §2 Kịch bản rủi ro, §3 Khi AI sai, §4 Mức tự chủ, §5 Prototype, §6 Tốt là gì, §7 Kế hoạch Demo & Ca lạ).
* **[prototype/index.html](file:///c:/Users/OS/Downloads/VinAI/K5-L3A-Day05-T4-3_chang_ngu_lam/prototype/index.html):** Màn hình kép tương tác (Dual-Pane) mô phỏng song song Người mua (Shopee App Chat) và Người bán (Kênh người bán 48h). Mở trực tiếp bằng bất kỳ trình duyệt nào.
* **[ai_log.md](file:///c:/Users/OS/Downloads/VinAI/K5-L3A-Day05-T4-3_chang_ngu_lam/ai_log.md):** Nhật ký chi tiết toàn bộ các bước thực hiện của AI, quá trình phản biện /grill-me và kiểm thử rubric.

---

### Cách chạy Prototype Demo (Dưới 30 giây)
1. Mở trực tiếp file `prototype/index.html` bằng trình duyệt (Google Chrome, Microsoft Edge, Safari).
2. Chọn kịch bản tại thanh điều khiển trên cùng:
   * **#4 Mô tả bị sửa sau khi bán** (Demo bắt buộc: Người mua đúng).
   * **#5 Người bán đúng / Tem khớp mô tả** (Demo bắt buộc: Người bán đúng).
   * **Ca lạ: Nồi chiên 6L vs 5L** (Tranh chấp thông số kỹ thuật).
3. Bật công tắc **"Chế độ Chấm thi"** để hiển thị các huy hiệu đối chiếu tiêu chuẩn: `[HAX G10]`, `[HAX G11]`, `[PAIR Trust]`, `[Mức tự chủ]`.
4. Bấm các nút tương tác:
   * Phía người mua: `[Tải lên ảnh lúc đặt]`, `[Gặp Nhân viên]` (`chuyen_truong_nhom`).
   * Phía người bán: `[Chấp thuận hoàn tiền]` (`soan_hoan_tien` tầng 1), `[Shop gửi khiếu nại đối chất]` (`chuyen_truong_nhom`).
