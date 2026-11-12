# Còn thiếu — trước khi nộp (hạn 23:59 12/11/2026)

Trạng thái lúc ghi file:
- `main` có `spec.md` (§1–§4, §6) và `prototype/index.html` (commit `7a606ca`).
- File này nằm trên branch `dominhhieu`.

## Yêu cầu của đề (nhắc lại)

- Repo public, tên `K5-L3A-Day05-T4-3_chang_ngu_lam`. Mở thử bằng cửa sổ ẩn danh phải xem được.
- `spec.md`: bảng thành viên ở đầu, có **mã học viên đúng**, rồi §1→§7.
- `prototype/`: file HTML (hoặc README chứa link) + **1–2 ảnh có đánh số**.
- Rubric R5: *bấm qua được ca khó · thấy độ chắc/bằng chứng · mức tự chủ trên màn hình đúng như §4 · mỗi nguyên tắc HAX/PAIR trỏ được vào một chỗ (ảnh đánh số) · có lập luận cách hiện*.
- Demo T4 bắt buộc: ca **"người bán đúng, hoặc mô tả đã bị sửa"** + 1 ca lạ. Mỗi người trình bày 1 phần.
- Vibe-coding rule: ai không giải thích được phần có tên mình thì phần đó 0 điểm.

## Cách dùng prototype

Mở `prototype/index.html` bằng trình duyệt, không cần server.

- Thanh **CA DEMO** chọn ca:
  - K1 có bản lưu
  - K1 không có bản lưu
  - K9
  - Ca lạ (tự gõ)
- Bấm **Gửi** → **Gửi ảnh** → sang **Màn 2** → người bán **Đồng ý** hoặc **Phản đối** → trưởng nhóm sàn quyết.
- Nút **Chú thích số** hiện số ①–⑪ và bảng giải thích, dùng để chụp ảnh đánh số.

## A. Chặn nộp bài

- [ ] **A1. Bảng thành viên**
  - Điền MSSV của Trung và của Hiếu (`2A202603402`).
  - Thêm người thứ 4 (tên, MSSV, việc đã làm).
  - Đề yêu cầu **đúng 3 người**: hỏi TA về nhóm 4 người.
- [ ] **A2. §5 Prototype (đang trống)**
  - File `prototype/index.html` · công cụ: HTML + Claude Code · phần mock: toàn bộ (không backend, không gọi AI thật, ca lạ dùng so khớp từ khoá).
  - Bảng số ①–⑪: chép từ bảng "Chú thích số" trong prototype. Mỗi số ghi *thể hiện gì · HAX/PAIR nào · mức tự chủ nào*.
  - Quyết định: hiện bằng chứng bằng **thẻ so sánh mô tả lúc đặt / hiện tại** + **chip độ chắc** (chắc gì / chưa xác minh gì). Các cách đã cân nhắc: thanh % độ tin cậy, chỉ ghi chữ, popup. Ghi vì sao loại từng cách.
  - Điều khiển mức tự chủ: tự làm = sự kiện xanh + **Hoàn tác** · cần duyệt = hộp xác nhận ghi số tiền + "khó đảo lại" · cấm = **không có nút**.
- [ ] **A3. Ảnh đánh số trong `prototype/`**: bật "Chú thích số", chụp Màn 1 (ca K1 sau khi gửi ảnh) và Màn 2.
- [ ] **A4. AI log** của Trung và Thụ chưa có trên `main` (chỉ nằm trên branch của từng người).
- [ ] **A5. §7 Demo**: điền sau buổi demo (ca lạ nhận được · prototype đi đường nào · nhóm có đổi ý gì không).

## B. Spec lệch với prototype (sửa spec cho khớp)

- [ ] **B1. §3.2 K9** trích *"Chính sách Trả hàng & Hoàn tiền Shopee Điều 3.2"*. Nguồn này **không có trong dữ liệu track**: chính là lỗi ① (bịa nguồn). Prototype ghi: *"Căn cứ: quy trình đối soát trả hàng của sàn. Lời đe doạ không thay cho bằng chứng."*
- [ ] **B2. §3.2 K9 và §6 tiêu chí 3** hứa *"phản hồi dưới 5 phút"*. Không có tool hay dữ liệu nào đảm bảo được. Prototype ghi: *"thời gian phản hồi phụ thuộc giờ trực"*.
- [ ] **B3. §3.1 K1** tự đóng hội thoại sau 10 phút: ép người mua, có thể làm mất khiếu nại. Prototype không đóng chat; hạn trả hàng vẫn hiển thị.
- [x] **B4. §3.1 K1 thiếu Đường B** — xong: spec §3.1 đã có Đường B đầy đủ + bảng so sánh A/B; prototype `fb6625e` tách hành vi 2 đường. (đơn không có bản lưu mô tả lúc đặt): AI nói "chưa đủ căn cứ", xin ảnh trang sản phẩm lúc mua + nhãn, chuyển trưởng nhóm sàn. Câu AI nói ở K1 cũng cần thêm: báo đây là trợ lý AI · hạn trả hàng còn bao nhiêu ngày · người bán có 24h phản hồi. (Chi tiết: `ai_log_dominhhieu.md`, mục 5.)
- [ ] **B5. §3.3 mâu thuẫn §3.5:** §3.3 nói hệ thống *đã có* snapshot nhưng AI đọc bản mới; §3.5 nói *phải tạo* snapshot. Chốt 1 cách. Gợi ý: snapshot đã có, thiết kế cứu là **AI chỉ đọc mô tả theo mã đơn**, không đọc trang sản phẩm hiện tại.
- [ ] **B6. §4 `soan_hoan_tien`:** "quá hạn 24h → tự động hoàn tiền" xung đột với khoá cứng K9 ở §3.5 (cần video mở hộp). Thêm điều kiện: *chỉ tự hoàn khi hồ sơ đã đủ bằng chứng*.
- [ ] **B7. §6 tiêu chí 2** bắt mọi ca hoàn tiền phải có video mở hộp, mâu thuẫn với §4.3 K8 (shop đã nhận gửi nhầm, chỉ cần shop bấm đồng ý). Sửa tiêu chí: video chỉ bắt buộc khi **có tranh chấp hoặc lời đe doạ**.
- [ ] **B8. §4.1** bảng vẫn có 1 dòng `soan_hoan_tien`, trong khi §4.2 đã tách thành `soan_ho_so_hoan_tien` (tự làm) + `duyet_giai_ngan` (cần duyệt). Tách thành 2 dòng, giống "Sổ quyền hạn" trong prototype.
- [ ] **B9. §3.4** chốt 3 nguyên tắc (G10, G11, PAIR). Prototype còn trỏ thêm **G1** (nhãn "Trợ lý AI", Luật AI 134/2025 Điều 11), **G2** (chip độ chắc), **G9** (Hoàn tác). Hoặc thêm vào §3.4, hoặc ghi ở §5 là nguyên tắc phụ.

## C. Chuẩn bị demo

- [ ] Chia lượt nói: lát cắt (30") · bấm K1 · một mức tự chủ + cái giá khi sai · trả lời ca lạ.
- [ ] Tập 2 câu TA hay hỏi: *"Chỉ chỗ nào là G10?"* (số ②) · *"Nút này sai thì ai mất gì, vì vậy nó ở mức nào?"* (ví dụ "Đồng ý hoàn tiền": người bán mất tiền, khó đảo, nên **cần duyệt**).
- [ ] Người đứng tên §5 đọc hiểu phần `Flows` trong `prototype/index.html` (các hàm `runK1`, `runK9`, `runFree`).

## Gợi ý chia việc

| Người | Việc |
|---|---|
| Hiếu | B3, B4, B5 (K1) · đọc hiểu prototype |
| Trung | B1, B2, B6, B7, B9 · A4 |
| Thụ | B8 |
| Người thứ 4 | A2, A3 (§5 + ảnh) |
| Cả nhóm | A1 · C · A5 sau demo |

## Cập nhật: K1 Đường A và Đường B khác nhau ở hành vi

- Prototype (`main`, `fb6625e`), ca **"K1 · không có bản lưu"**:
  - Dải đỏ "Chưa đối chiếu được".
  - Ô "lúc đặt" để trống, gạch chéo.
  - Danh sách căn cứ ✓/✗.
  - AI **không** soạn hồ sơ hoàn tiền.
  - Chỉ trưởng nhóm sàn quyết; người bán chỉ tự nguyện nhận trả hoặc giải trình.
  - Quá hạn **không** tự hoàn tiền.
- Spec (`dominhhieu`): §3.1 Đường B có đủ "thấy gì · làm gì tiếp · ai được báo · quyết định + phương án loại", kèm bảng so sánh A/B.
- [ ] Người viết §5: bảng chú thích ②③④⑧ đã đổi câu chữ, cần chép lại từ prototype.
