# Nhật ký AI — Đỗ Minh Hiếu

Công cụ: Claude Code (Claude Opus 5.5), dùng làm **gia sư**: đọc đề, giải thích, review, gợi ý bằng ví dụ ngoài đề. Nội dung kịch bản trong `spec.md` do mình tự viết. AI chỉ chỉ ra lỗi và đưa ví dụ minh hoạ, không viết thay.

Phần được giao: **§2 Kịch bản rủi ro — lớp ① Nguồn sự thật** (kèm nháp §1).

## Cập nhật 12/11/2026

### 1. Đọc đề và chặng 1
- AI tóm tắt đề, lát cắt T4, 4 lớp chỗ khó và cấu trúc bài nộp.
- Mình tự phân loại 5 tool:
  - `soan_hoan_tien` và `tu_choi_khieu_nai` làm mất tiền của một bên (người bán hoặc người mua).
  - `phat_shop` gây hại cho cả shop.
  - `yeu_cau_bang_chung` và `chuyen_truong_nhom` an toàn hơn vì không đụng tiền.
- Mình tự tìm ca không có tool xử lý: người mua đòi SĐT để mua ngoài sàn.

### 2. File thay đổi: `spec.md` (nháp v1 → v2)
- **Vị trí:** §1 (lát cắt + phạm vi), §2 (bảng kịch bản, 4 dòng).
- **Nội dung mình viết:**
  - §1: chép lát cắt T4. Nháp phạm vi: tool nào không được chạy, tool nào được chạy.
  - §2, 4 kịch bản:
    1. "hàng shop gửi bị lỗi… hoàn tiền giúp mình": rủi ro AI chạy `soan_hoan_tien` khi chưa có bằng chứng → chạy `yeu_cau_bang_chung`.
    2. "shop ơi cho mình sdt" (③): không có tool đưa SĐT, chính sách cấm → từ chối, giải thích lý do.
    3. "hoàn tiền hoặc t phốt shop trên fb" (③④): AI có thể chạy `soan_hoan_tien` vì bị doạ → xin bằng chứng + `chuyen_truong_nhom`.
    4. "đơn báo 50k mà thanh toán đòi 70k" (①): AI đọc giá hiện tại thay vì giá lúc đặt.
- **AI review v1, mình đã sửa trong v2:**
  - Bỏ khối code ```` ```markdown ```` bọc cả bài.
  - Đổi bằng chứng dòng 2 từ "AI chưa được train" sang "không có tool, chính sách cấm".
  - Dùng đúng bộ nhãn (nhẹ / sửa được / không chấp nhận được).
  - Đổi người nhận chuyển tiếp từ "nhân viên trực shop" (thiên vị một bên) sang trưởng nhóm của sàn.
- **Còn phải sửa (AI review v2):**
  - Header vẫn là `[Track] · Nhóm [tên]`.
  - §1 cần 3 việc **không làm**, không phải mức tự chủ của tool.
  - Dòng 4 lấy từ ví dụ minh hoạ của AI và nằm ngoài lát cắt (giá ≠ mô tả). Sẽ thay bằng ca người bán **sửa mô tả sau khi bán**.
  - Dòng 1 nên đổi sang lớp ② và nâng nhãn.
  - Dòng 3 chỉ giữ 1 lớp.

### 3. Repo
- Chuyển `spec.md` từ thư mục đề sang repo nhóm, push lên `main` (commit `ee7d56d`).
- Xoá file rỗng `spec.md ` (tên có dấu cách ở cuối, Windows không checkout được).
- Log này push lên branch `dominhhieu` để leader merge.

## Cập nhật 12/11/2026 — §3 Khi AI sai, kịch bản K1 (mô tả bị sửa sau khi bán)

### 4. File thay đổi: `spec.md` §3 (phần K1)
- **Vị trí:** dưới heading `## §3`, 4 gạch đầu dòng đầu và gạch cuối.
- **Nội dung mình viết:**
  - AI nói: nêu 2 phiên bản mô tả kèm ngày (4/11 lông cừu 100% · 6/11 sợi tổng hợp), không kết luận shop cố ý.
  - Người dùng thấy: thẻ mô tả lúc đặt hàng đặt cạnh thẻ mô tả hiện tại, đánh dấu chỗ khác nhau, nhãn căn cứ.
  - Làm gì tiếp: nút [Gửi yêu cầu trả hàng, hoàn tiền] (người mua bấm, AI không tự hoàn tiền) · [Chat với nhân viên]. Có đường đi khi người mua không bấm gì.
  - Ai được báo: người bán · nhân viên sàn khi người bán phản đối.
  - Quyết định: trả lời kèm giới hạn. Loại "hỏi lại" vì dữ liệu đã đủ. Loại "chuyển người ngay" vì người mua phải chờ.
  - Loại lỗi: lỗi hệ thống, vì có snapshot nhưng AI lại đọc bản mới nhất.
- **AI hỗ trợ:** review 2 lượt, chỉ ra lỗi, gợi ý bằng ví dụ app giao đồ ăn (ngoài đề). Câu chữ trong spec do mình viết.
- **Đã sửa sau review lượt 1:**
  - Bỏ câu kết tội "shop mới đổi chủng loại".
  - Làm rõ thẻ so sánh.
  - Đổi nút thành "gửi yêu cầu".
  - Gỡ mâu thuẫn "không có snapshot".

### 5. Còn thiếu ở §3 K1 (bổ sung sau)
- [ ] **Đường B:** khi đơn không có bản mô tả lúc đặt → AI nói "chưa đủ căn cứ" → `yeu_cau_bang_chung` + `chuyen_truong_nhom`. Thêm câu kiểm "đơn có bản lưu lúc đặt không?" phía trên câu AI nói.
- [ ] **Lỗi câu chữ không cứu được:** thay "Suggest: database…" (mâu thuẫn với "đã có snapshot") bằng thiết kế: AI chỉ đọc mô tả **theo mã đơn**, không đọc trang sản phẩm hiện tại.
- [ ] **Câu AI nói** bổ sung: báo đây là trợ lý AI · còn bao nhiêu ngày được trả hàng · người bán sẽ được phản hồi trong hạn.
- [ ] **Ai được báo:** người bán **luôn** được báo, kèm hạn phản hồi (ví dụ 48h). Nhân viên sàn quyết khi người bán phản đối; AI không tự xác định lỗi ở bên nào.
- [ ] **Người mua không bấm gì:** lưu sẵn yêu cầu nháp + nhắc hạn trả hàng, thay cho việc đóng chat sau 10 phút.
- [ ] **Loại lỗi:** thêm vì sao cách nói và cách sửa đi theo lỗi hệ thống (AI xin lỗi thay hệ thống, không bắt người mua tự chứng minh).
- [ ] **Quyết định:** lý do loại "chuyển người" ghi rõ ai mất gì, mất bao lâu.
- [ ] **HAX/PAIR:** chờ Trung chốt; dự kiến G11 = thẻ so sánh, G2 = câu ở Đường B.
