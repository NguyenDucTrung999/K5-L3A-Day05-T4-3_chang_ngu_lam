# Nhật Ký Hoạt Động Của AI (AI Log Tổng Hợp Cả Nhóm)

**Dự án:** LAB5 — AI Product UX & Autonomy · Track T4 (E-commerce)  
**Nhóm sinh viên:** Nhóm 3 chàng ngự lâm (Lớp L3A · Zone C4)  
**Thành viên:**  
1. Nguyễn Đức Trung — MSSV: 2A202603423 (Trưởng nhóm)  
2. Đỗ Minh Hiếu — MSSV: 2A202603402  
3. Nguyễn Huy Thứ — MSSV: 2A202603356  
4. Bùi Văn Lâm — MSSV: 2A202603400  
**Thời gian thực hiện:** Ngày 12/11/2026  
**Mục tiêu:** Hoàn thiện toàn diện bài nộp `spec.md` (§1 đến §7), xây dựng sản phẩm mẫu tương tác `prototype/index.html`, chụp ảnh minh chứng đánh số ①–⑪, và tài liệu hướng dẫn demo `README.md`.

---

## PHẦN I. NHẬT KÝ LÀM VIỆC CỦA NGUYỄN ĐỨC TRUNG (TRƯỞNG NHÓM)

### 1. Phiên làm việc Chặng 1 & Chặng 2 (Lát cắt, Phạm vi & Kịch bản rủi ro Lớp ④)
- **Công việc thực hiện:**
  - Chuẩn hóa Mục §1: Đưa lát cắt chuẩn 1 câu 5 cột của Track 4 và xây dựng 3 việc tính năng KHÔNG làm có lý do rõ ràng theo chi phí sai sót (Cost-of-Error) và bảo vệ tính trung lập cho sàn.
  - Xây dựng 3 kịch bản rủi ro sắc bén thuộc Lớp ④ Đặc thù domain: Kịch bản đe dọa bóc phốt trên mạng xã hội, Kịch bản khách xé tem mác giặt sạch đòi hoàn tiền không trả hàng, và Kịch bản xung đột khi người bán có video đối chất.
  - Tổng hợp cùng các thành viên để hoàn thiện bảng 10 kịch bản rủi ro phủ trọn vẹn 4 lớp khó của đề bài.
  - Lập luận chi tiết 4 ý cho 2 kịch bản đắt nhất: Kịch bản 1 (Người bán sửa mô tả sau khi đặt — Lớp ①) và Kịch bản 9 (Khách đe dọa bóc phốt để ép hoàn tiền 15 phút — Lớp ④), cùng kịch bản suýt được chọn (Kịch bản 7).

### 2. Phiên làm việc Chặng 3 (Khi AI sai — K9 & Bộ nguyên tắc HAX/PAIR) & Chặng 6 (Tốt là gì)
- **Công việc thực hiện:**
  - Thiết kế chi tiết trải nghiệm cho Kịch bản K9: Viết lời thoại nguyên văn của AI chuẩn mực, thiết kế các thẻ hiển thị trên giao diện (nhãn Trợ lý AI, căn cứ quy trình đối soát, nút nộp video/ảnh tem, nút gặp nhân viên hỗ trợ).
  - Phân loại lỗi K9 là Lỗi ngữ cảnh (Context Error theo PAIR) và quy chuẩn cách phản hồi không nhận lỗi về sàn.
  - Chốt 3 nguyên tắc HAX/PAIR dùng chung cho cả nhóm và Prototype: HAX G10 (Thu hẹp phạm vi), HAX G11 (Giải thích căn cứ hệ thống), và PAIR (Graceful Failure & Human Escalation).
  - Chỉ ra lỗi sửa câu chữ không cứu được (tự ý giải ngân khi bị đe dọa) và thiết kế giải pháp cứu nó bằng ràng buộc cứng ở tầng kiến trúc hệ thống (Hard Constraint).
  - Xây dựng Mục §6: 3 tiêu chí Pass/Fail chấm được, thực hiện chấm thử trên K1 và K9 (3/3 Đạt), và chỉ rõ rủi ro còn lại (Residual Risk).

---

## PHẦN II. NHẬT KÝ LÀM VIỆC CỦA ĐỖ MINH HIẾU

Công cụ sử dụng: Claude Code (Claude Opus 5.5).  
Phần được giao: **§2 Kịch bản rủi ro — Lớp ① Nguồn sự thật, §3 Khi AI sai — Kịch bản K1, và xây dựng Prototype `prototype/index.html`.**

### 1. Phân tích Chặng 1 & Chặng 2 (Lớp ① Nguồn sự thật)
- Phân loại 5 công cụ theo tính chất rủi ro tài chính: `soan_hoan_tien` và `tu_choi_khieu_nai` ảnh hưởng trực tiếp đến tiền; `phat_shop` gây tê liệt gian hàng; `yeu_cau_bang_chung` và `chuyen_truong_nhom` an toàn hơn.
- Xây dựng các kịch bản nguồn sự thật: Người bán sửa mô tả sau khi bán, thỏa thuận ngầm qua tin nhắn riêng, và lỗi đọc giá/mô tả hiện tại thay vì bản ghi lúc đặt.

### 2. Thiết kế Chặng 3 (Kịch bản K1: Mô tả bị sửa sau khi bán)
- Viết trải nghiệm người dùng với thẻ so sánh trực quan đối chiếu 2 phiên bản mô tả (lúc đặt 04/11 vs hiện tại 06/11) có tô vàng vị trí sai lệch.
- Phân nhánh rõ ràng 2 đường đi:
  - **Đường A (Có bản lưu Snapshot):** AI đối chiếu snapshot, báo rõ hạn trả hàng còn lại, người bán có 24h phản hồi, yêu cầu gửi ảnh nhãn mác áo.
  - **Đường B (Không có bản lưu Snapshot):** AI thông báo chưa đủ căn cứ, xin ảnh chụp bài đăng lúc mua + ảnh nhãn mác, chuyển Trưởng nhóm sàn.
- Phân loại lỗi: Lỗi hệ thống (System Error). Thiết kế cứu lỗi là AI chỉ được phép đọc mô tả theo mã đơn hàng trong database snapshot, cấm đọc trang sản phẩm hiện tại.

### 3. Xây dựng Prototype `prototype/index.html` (§5)
- Dựng giao diện tương tác kép (Dual-Screen): Màn 1 (Shopee Chat người mua) và Màn 2 (Bàn duyệt Kênh Người Bán & Trưởng nhóm sàn).
- Thiết kế theme "Hồ sơ đối chiếu" trực quan với 3 màu sắc chuẩn hóa tương ứng 3 mức tự chủ: Xanh (Tự làm), Vàng (Cần duyệt), Đỏ (Cấm).
- Cài đặt đầy đủ 4 luồng demo: K1 có bản lưu, K1 không có bản lưu, K9 dọa bóc phốt, và Ca lạ (tự gõ).
- Tích hợp công tắc "Chú thích số" hiển thị 11 ghim chú thích ①–⑪ đối chiếu với Rubric R5.

---

## PHẦN III. NHẬT KÝ LÀM VIỆC CỦA NGUYỄN HUY THỨ

Phần được giao: **§2 Kịch bản rủi ro — Lớp ② & Lớp ③, và toàn bộ §4 Mức tự chủ.**

### 1. Xây dựng Kịch bản rủi ro (Lớp ② Mơ hồ & Lớp ③ Ngoài thẩm quyền)
- Xây dựng các ca kiểm thử: Khách nhắn tin cộc lốc thiếu mã đơn (K4), đơn nhiều món giao sai 1 món (K5), khách đòi số điện thoại/địa chỉ riêng của shop (K6), khách nghi hàng giả đòi khóa shop (K7), khách đòi đền thêm tiền mặt 200k làm lỡ tiệc (K8).
- Phân định ranh giới: AI kiên quyết từ chối cung cấp dữ liệu cá nhân theo chính sách bảo mật và từ chối các khoản đòi bồi thường ngoài phạm vi đơn hàng.

### 2. Thiết kế Mức tự chủ của các công cụ (§4)
- Phân bổ 5 công cụ theo chi phí sai sót (Cost-of-Error):
  - `yeu_cau_bang_chung`: Tự làm (có hoàn tác).
  - `chuyen_truong_nhom`: Tự làm (an toàn, không đụng tiền).
  - `soan_ho_so_hoan_tien`: Tự làm (chỉ gom hồ sơ, tạm giữ Escrow).
  - `duyet_giai_ngan`: Cần người duyệt (tiền về người mua khó lấy lại; shop duyệt ca rõ ràng hoặc sàn duyệt ca tranh chấp).
  - `tu_choi_khieu_nai`: Cần người duyệt (100% Trưởng nhóm sàn duyệt).
  - `phat_shop`: Cấm (chuyển bộ phận Pháp chế ngoài luồng chat).
- **Đề xuất sáng tạo:** Tách công cụ `soan_hoan_tien` thành 2 bước (`soan_ho_so_hoan_tien` và `duyet_giai_ngan`) để tối ưu hóa thời gian xử lý cho các ca rõ ràng mà vẫn chặn đứng rủi ro thất thoát tài chính.
- Kiểm thử mức tự chủ trên 3 kịch bản: K1 (Đắt nhất 1), K9 (Đắt nhất 2), K8 (Bình thường). Tuyên bố chuyển đổi lời hứa với người dùng.

---

## PHẦN IV. NHẬT KÝ LÀM VIỆC CỦA BÙI VĂN LÂM

Phần được giao: **Rà soát kiến trúc Prototype, đối chiếu tiêu chuẩn Rubric R5, lập bảng chú thích số ①–⑪, chuẩn bị minh chứng hình ảnh và kịch bản demo.**

### 1. Rà soát Prototype đối chiếu Rubric R5
- Kiểm tra tính mượt mà của các tương tác trên `prototype/index.html`: đảm bảo không có lỗi JavaScript trên Console, giao diện co giãn tốt (responsive) từ 375px (mobile) đến 1440px (desktop).
- Xác minh sự hiển thị đầy đủ của 3 mức tự chủ trên giao diện:
  - Tự làm: Thẻ màu xanh kèm nút [Hoàn tác].
  - Cần người duyệt: Hộp thoại Modal ghi rõ số tiền bồi hoàn và cảnh báo khó đảo lại.
  - Cấm: Không có nút bấm cho `phat_shop`, có khung viền đỏ cảnh báo cấm rõ ràng.

### 2. Xây dựng Bảng chú thích số ①–⑪ và Minh chứng giao diện
- Đối chiếu từng vị trí trên màn hình với các nguyên tắc HAX/PAIR:
  - ① HAX G1 (Nhãn Trợ lý AI).
  - ② HAX G10 (Kiểm tra bản lưu snapshot).
  - ③ HAX G11 / PAIR Explainability (Thẻ đối chiếu snapshot).
  - ④ HAX G2 (Chip độ chắc chắn).
  - ⑤ HAX G9 / Mức Tự làm (Sự kiện gửi yêu cầu bằng chứng kèm nút Hoàn tác).
  - ⑥ PAIR Graceful Failure / Mức Tự làm (Nút gặp nhân viên sàn).
  - ⑦ Mức Cấm (`phat_shop` không có nút).
  - ⑧ Cần người duyệt (Đồng hồ đếm ngược 24h của shop).
  - ⑨ Cần người duyệt (`duyet_giai_ngan` kèm modal xác nhận).
  - ⑩ Cần người duyệt (`tu_choi_khieu_nai` 100% sàn duyệt).
  - ⑪ Nguyên tắc trung lập (Ẩn lời đe dọa bóc phốt khỏi mắt người bán).
- Soạn thảo tài liệu `README.md` tại thư mục gốc để hướng dẫn người chấm chạy và demo sản phẩm dưới 30 giây.

---

## PHẦN V. TỔNG HỢP, RÀ SOÁT VÀ ĐỒNG BỘ TOÀN DIỆN (TRƯỚC GIỜ NỘP)

Trong phiên làm việc cuối cùng trước khi đóng gói nộp bài, nhóm đã tiến hành rà soát chéo giữa `spec.md` và `prototype/index.html`, xử lý triệt để 9 điểm lệch (B1 đến B9) và hoàn thiện các mục còn thiếu (A1 đến A5):

1. **A1 (Bảng thành viên):** Đã điền đầy đủ 4 thành viên kèm MSSV chính xác: Nguyễn Đức Trung (`2A202603423`), Đỗ Minh Hiếu (`2A202603402`), Nguyễn Huy Thứ (`2A202603356`), Bùi Văn Lâm (`2A202603400`), kèm ghi chú về nhóm 4 người theo xác nhận của TA.
2. **A2 (Mục §5 Prototype):** Đã hoàn thiện toàn diện Mục §5 với đường dẫn file, công cụ, phần mock, bảng chú thích số ①–⑪ chi tiết, lập luận lựa chọn cách hiển thị bằng chứng (loại thanh % tin cậy, loại chữ chay, loại popup), và cách điều khiển 3 mức tự chủ trên UI.
3. **A3 (Ảnh đánh số):** Trỏ đường dẫn trực tiếp tới 2 ảnh minh chứng [prototype/screen1-annotated.png](prototype/screen1-annotated.png) và [prototype/screen2-annotated.png](prototype/screen2-annotated.png).
4. **A4 (Đồng bộ Log):** File `ai_log.md` này được hợp nhất tại nhánh `main`, lưu trữ đầy đủ nhật ký của cả 4 thành viên.
5. **A5 (Mục §7 Demo):** Đã xây dựng khung kịch bản phân công thuyết trình 4 phút, sẵn sàng 2 câu hỏi bẫy của Hội đồng chấm và khung ghi nhận sau buổi demo.
6. **B1 & B2 (Khắc phục lỗi bịa nguồn và cam kết thời gian):** Sửa câu căn cứ trong K9 thành *"Căn cứ: Quy trình đối soát trả hàng của sàn. Lời đe doạ không thay cho bằng chứng."* và sửa thời gian phản hồi thành *"phụ thuộc giờ trực của nhân viên sàn"*.
7. **B3 (Bỏ tự đóng chat):** Không đóng chat sau 10 phút; lưu sẵn hồ sơ nháp và hiển thị rõ số ngày trả hàng còn lại (14 ngày).
8. **B4 (Bổ sung Đường B cho K1):** Hoàn thiện luồng khi đơn không có bản lưu snapshot: AI hạ mức độ chắc chắn, gọi `yeu_cau_bang_chung` xin ảnh bài đăng lúc mua + ảnh nhãn mác, và chuyển `chuyen_truong_nhom`.
9. **B5 (Đồng nhất dữ liệu snapshot):** Khẳng định cơ sở dữ liệu đã có sẵn snapshot theo đơn hàng; thiết kế cứu lỗi là AI chỉ đọc dữ liệu mô tả theo mã đơn hàng, cấm đọc trang sản phẩm hiện tại.
10. **B6 & B8 (Đồng bộ Sổ quyền hạn và Tách tool):** Tách `soan_hoan_tien` thành 2 dòng `soan_ho_so_hoan_tien` (Tự làm) và `duyet_giai_ngan` (Cần người duyệt), bổ sung điều kiện quá hạn 24h chỉ tự hoàn khi hồ sơ đã có đủ bằng chứng.
11. **B7 (Điều chỉnh Tiêu chí 2 ở §6):** Video mở hộp chỉ bắt buộc khi có tranh chấp hoặc lời đe dọa; ca shop đã nhận gửi nhầm thì hoàn tiền ngay khi shop đồng ý.
12. **B9 (Bổ sung HAX G1, G2, G9 vào §3.5):** Tích hợp trọn vẹn 6 nguyên tắc HAX/PAIR khớp 100% với các điểm đánh số trên prototype.
