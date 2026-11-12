# Nhật ký thay đổi AI (AI Log)

## Cập nhật ngày 12/11/2026 - Phiên làm việc Chặng 1 và Chặng 2

### 1. File thay đổi: teamwork/K5-L3A-Day05-T4-3_chang_ngu_lam/spec.md
- Vị trí thay đổi: Từ dòng 1 đến dòng 40 (thay thế phần tiêu đề, cấu trúc bảng thành viên, Mục 1 và Mục 2).
- Nội dung thay đổi:
  - Cập nhật tiêu đề bài nộp: Track 4 Thương mại điện tử, Nhóm 3 chàng ngự lâm.
  - Điều chỉnh cấu trúc bảng thành viên để sẵn sàng cho nhóm 4 người.
  - Hoàn thiện Mục 1 (Lát cắt và phạm vi):
    + Ghi rõ nội dung lát cắt chuẩn của Track 4.
    + Bổ sung chi tiết 3 việc tính năng không làm kèm lý do bảo vệ tính trung lập và an toàn tài chính cho cả người mua và người bán.
  - Hoàn thiện phần đóng góp của Thành viên 4 trong Mục 2 (Kịch bản rủi ro - Lớp 4 Đặc thù domain):
    + Kịch bản 1: Khách đe dọa bóc phốt trên mạng xã hội trong 15 phút, AI không được tự ý kích hoạt công cụ soan_hoan_tien mà phải giữ trung lập và yêu cầu bằng chứng qua công cụ yeu_cau_bang_chung (Mức hại: Không chấp nhận được).
    + Kịch bản 2: Khách đã xé tem mác, giặt đồ nhưng khiếu nại chất vải không đúng mô tả và đòi hoàn tiền không trả hàng, AI không được tự ý hoàn tiền mà phải từ chối hoặc chuyển chuyên viên thẩm định qua công cụ chuyen_truong_nhom (Mức hại: Không chấp nhận được).
    + Kịch bản 3: Xung đột khi người bán đã có video đóng hàng hợp lệ nhưng khách dọa xóa ứng dụng, AI không được tự phán quyết mà chuyển chuyên viên giải quyết qua công cụ chuyen_truong_nhom (Mức hại: Sửa được).
  - Bổ sung lập luận chi tiết giải thích lý do lựa chọn 2 kịch bản đắt nhất (Kịch bản 1 và Kịch bản 2) và lý do loại bỏ kịch bản suýt được chọn (Kịch bản 3) dựa trên chi phí sai sót không thể đảo ngược của công cụ soan_hoan_tien.
- Mục đích: Cung cấp đầy đủ nội dung Chặng 1 và Chặng 2 theo đúng tiêu chuẩn Rubric R1 và R2 cho Thành viên 4 phụ trách Khía cạnh 4 (Xung đột lợi ích hai đầu và áp lực tâm lý).

### 2. File thay đổi: teamwork/K5-L3A-Day05-T4-3_chang_ngu_lam/spec.md
- Vị trí thay đổi: Dòng 21 và dòng 28 đến dòng 34.
- Nội dung thay đổi:
  + Dòng 21: Chuẩn hóa lại tiêu đề cột trong bảng kịch bản rủi ro ("Một sản phẩm tốt nên làm gì").
  + Dòng 28 đến dòng 34: Tạm thời gỡ bỏ nội dung lựa chọn 2 kịch bản đắt nhất và kịch bản suýt được chọn, thay bằng dòng ghi chú chờ thảo luận và thống nhất giữa các thành viên sau khi tổng hợp đầy đủ kịch bản từ 4 người.
- Lý do: Theo yêu cầu của người dùng để nhóm thảo luận nội bộ trước khi chốt quyết định chính thức.

### 3. File thay đổi: teamwork/K5-L3A-Day05-T4-3_chang_ngu_lam/spec.md
- Vị trí thay đổi: Từ dòng 19 đến dòng 39.
- Nội dung thay đổi:
  - Cập nhật trọn vẹn Mục 2 (§2. Kịch bản rủi ro) gồm đúng 8 kịch bản bao phủ đủ 4 lớp rủi ro (mỗi lớp 2 kịch bản):
    + Lớp ① Nguồn sự thật: Kịch bản 1 (Người bán sửa mô tả sau khi bán) và Kịch bản 2 (Cam kết trong tin nhắn chat riêng).
    + Lớp ② Mơ hồ / thiếu thông tin: Kịch bản 3 (Tin nhắn cộc lốc thiếu mã đơn và lỗi) và Kịch bản 4 (Khiếu nại dung tích nồi chiên không đúng quy chuẩn đo lường).
    + Lớp ③ Ngoài phạm vi / thẩm quyền: Kịch bản 5 (Khách đòi số điện thoại và địa chỉ riêng của người bán) và Kịch bản 6 (Khách đòi khóa shop, phạt tiền gian hàng vì nghi hàng giả).
    + Lớp ④ Đặc thù domain: Kịch bản 7 (Khách đe dọa bóc phốt trên mạng xã hội) và Kịch bản 8 (Khách xé tem mác, giặt đồ nhưng đòi hoàn tiền không trả hàng).
  - Từng kịch bản đều trích dẫn chính xác công cụ của Track 4 (`soan_hoan_tien`, `tu_choi_khieu_nai`, `yeu_cau_bang_chung`, `chuyen_truong_nhom`, `phat_shop`) và dữ liệu cụ thể (snapshot đơn hàng, log chat, dung tích khoang chứa, tem mác).
  - Hoàn thiện lập luận cho 2 kịch bản đắt nhất: Kịch bản 1 (phá hủy nguồn sự thật) và Kịch bản 7 (thao túng tài chính và áp lực xã hội), cùng lý do loại trừ kịch bản suýt được chọn là Kịch bản 6.
- Mục đích: Đạt chuẩn 100% tiêu chí Rubric R2 (10/10 điểm) của đề bài LAB5.

### 4. File thay đổi: teamwork/K5-L3A-Day05-T4-3_chang_ngu_lam/spec.md
- Vị trí thay đổi: Toàn bộ file (giải quyết xung đột merge từ nhánh main vào nhánh trung).
- Nội dung thay đổi:
  - Đồng bộ format chuẩn và hoàn chỉnh từ nhánh main sang nhánh trung, tích hợp đầy đủ đóng góp của 3 thành viên (Nguyễn Đức Trung, Đỗ Minh Hiếu, Nguyễn Huy Thụ).
  - Hoàn thiện bảng 10 kịch bản rủi ro tại Mục §2 và lập luận chọn 2 kịch bản đắt nhất (Kịch bản 1 và Kịch bản 9) cùng kịch bản suýt được chọn (Kịch bản 7).
  - Giải quyết dứt điểm xung đột merge (`both added: spec.md`) và tạo commit merge sạch sẽ.

### 5. File thay đổi: teamwork/K5-L3A-Day05-T4-3_chang_ngu_lam/spec.md
- Vị trí thay đổi: Từ dòng 71 đến dòng 120 (Mục §3) và từ dòng 138 đến dòng 165 (Mục §6).
- Nội dung thay đổi (phần phân công của Nguyễn Đức Trung - Trưởng nhóm):
  - Mục §3 (Khi AI sai):
    + Hoàn thiện thiết kế chi tiết cho Kịch bản K9 (Khách đe dọa bóc phốt trên mạng xã hội để ép hoàn tiền gấp trong 15 phút): Lời thoại nguyên văn của AI, các thành phần trực quan người dùng thấy (thẻ cảnh báo, căn cứ chính sách, nút nộp video mở hộp, nút thoát hiểm gặp người), các bước tiếp theo và thông báo đến người bán (60 giây) và trưởng nhóm sàn (5 phút).
    + Lập luận chiến lược 4 ý: Chọn trả lời kèm giới hạn; loại phương án hỏi lại vu vơ và loại phương án dừng chuyển người ngay lập tức kèm lý do cụ thể.
    + Phân loại lỗi: Lỗi ngữ cảnh (Context Error theo nguyên tắc PAIR) và cách ứng xử chuyên nghiệp không nhận lỗi sai của sàn.
    + Chốt 3 nguyên tắc HAX/PAIR dùng chung cho cả nhóm và Prototype: HAX G10 (Thu hẹp phạm vi khi nghi ngờ), HAX G11 (Giải thích căn cứ hệ thống), và PAIR (Thiết kế thoát hiểm Graceful Failure & Human Escalation).
    + Chỉ ra lỗi sửa câu chữ không cứu được (tự ý giải ngân soan_hoan_tien khi bị đe dọa) và thiết kế giải pháp cứu nó bằng ràng buộc cứng ở tầng kiến trúc hệ thống (Hard Constraint).
  - Mục §6 (Tốt là gì):
    + Xây dựng 3 tiêu chí Pass/Fail chấm được rõ ràng: Tiêu chí 1 (Tính toàn vẹn dữ liệu gốc - Ground Truth Integrity), Tiêu chí 2 (Tính trung lập tài chính - Financial Neutrality), Tiêu chí 3 (Quyền kiểm soát và Thoát hiểm minh bạch - Transparency & Fallback Control).
    + Bảng chấm thử thiết kế trên 2 kịch bản đắt nhất (K1 và K9) đạt 3/3 tiêu chí.
    + Chỉ rõ rủi ro còn lại (Residual Risk) liên quan đến video mở kiện hàng dàn dựng tinh vi cần quy trình đối soát hậu kiểm của con người.
- Mục đích: Đạt chuẩn tối đa các tiêu chí Rubric R3 (25 điểm) và Rubric R6 (5 điểm).

### 6. File thay đổi: teamwork/K5-L3A-Day05-T4-3_chang_ngu_lam/spec.md
- Vị trí thay đổi: Toàn bộ các phần từ Header, Mục §3, Mục §4 và Mục §6 trên nhánh main và nhánh trung.
- Nội dung thay đổi:
  - Tích hợp đóng góp của Đỗ Minh Hiếu tại Mục §3.1 (Kịch bản K1: Người bán sửa mô tả sau khi khách đặt hàng): Bổ sung câu thoại nguyên văn lịch sự chuẩn CSKH Shopee, giao diện hiển thị thẻ so sánh Snapshot đơn hàng (Cột trái: lúc đặt 04/11 - Cột phải: lúc sửa 06/11), phân loại Lỗi hệ thống (System Error), và kiến trúc Snapshot bất biến để cứu lỗi mà câu chữ không cứu được.
  - Tích hợp đóng góp của Nguyễn Huy Thụ tại Mục §4 (Mức tự chủ của 5 công cụ): Bảng phân bổ 5 tool theo Cost-of-Error, giải pháp sáng tạo tách công cụ soan_hoan_tien thành 2 bước (soan_ho_so_hoan_tien tự làm và duyet_giai_ngan cần người duyệt), bảng kiểm thử 3 kịch bản khớp hoàn toàn với bảng kịch bản rủi ro, và tuyên bố đổi lời hứa với người dùng.
  - Đánh giá logic toàn diện:
    + Chuẩn hóa lỗi chính tả tên thành viên "Nguyễn Huy Thứ" thành "Nguyễn Huy Thụ" và thống nhất bảng phân công.
    + Đảm bảo tính liên kết chặt chẽ giữa 10 kịch bản Mục §2, 2 kịch bản đắt nhất Mục §3 (K1 và K9), cơ chế tự chủ Mục §4 và 3 tiêu chí nghiệm thu Mục §6.
  - Hoàn tất commit trên nhánh main (commit `0050afb`) và đồng bộ sạch sẽ sang nhánh trung (commit `5d2ecf5`).
- Mục đích: Đồng bộ bài nộp hoàn chỉnh nhất lên nhánh main, chuẩn bị sẵn sàng cho Chặng 5 (Prototype) và Chặng 7 (Demo).

