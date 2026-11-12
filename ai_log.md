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

