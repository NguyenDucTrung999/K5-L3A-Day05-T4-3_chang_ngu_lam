# Ghi nhận trạng thái hiện tại của `spec.md`

## 1. Thông tin chung (Header)
- **Nhóm:** `3 chàng ngự lâm` · **Lớp:** `L3A` · **Bàn / zone:** `C4` · **Track:** `T4 · Thương mại điện tử`
- **Thành viên:** Nguyễn Đức Trung, Đỗ Minh Hiếu, Nguyễn Huy Thứ (`2A202603356`).

## 2. Mục `§1. Lát cắt & phạm vi`
- **1.1. Lát cắt:** Điền nguyên văn lát cắt và bảng tóm tắt 5 cột của Track 4 (*Trò chuyện với Shopee — người mua báo "hàng nhận không đúng mô tả"*).
- **1.2. Ba việc tính năng này KHÔNG làm (kèm lý do):**
  1. Không tự ý giải ngân tiền hoàn (`soan_hoan_tien`) hay đóng khiếu nại trả tiền cho người bán (`tu_choi_khieu_nai`) chỉ dựa trên lời nói một phía hoặc lời đe dọa bóc phốt.
  2. Không tự động xử phạt, trừ điểm uy tín hoặc khóa tài khoản gian hàng (`phat_shop`) khi tiếp nhận khiếu nại sai mô tả thông thường.
  3. Không cung cấp thông tin liên hệ cá nhân (số điện thoại, địa chỉ nhà riêng) giữa người mua và người bán, và không chấp nhận yêu cầu đòi bồi thường thiệt hại gián tiếp ngoài giá trị đơn hàng.

## 3. Mục `§2. Kịch bản rủi ro`
- **2.1. Bảng 10 kịch bản rủi ro (STT 1 → 10):** Phủ đủ 4 lớp chỗ khó `① Nguồn sự thật`, `② Mơ hồ / thiếu thông tin`, `③ Ngoài phạm vi / thẩm quyền`, `④ Đặc thù domain`.
- **2.2. Quyết định chọn 2 kịch bản đắt nhất (Lập luận 4 ý):**
  - **Kịch bản đắt nhất 1:** Kịch bản 1 *(Người bán sửa mô tả áo len lông cừu 100% thành sợi tổng hợp sau khi khách đặt hàng — Lớp ①)*.
  - **Kịch bản đắt nhất 2:** Kịch bản 9 *(Khách dùng lời đe dọa bóc phốt mạng xã hội để ép hoàn tiền gấp trong 15 phút — Lớp ④)*.
  - **Kịch bản suýt được chọn:** Kịch bản 7 *(Khách nghi hàng giả yêu cầu khóa vĩnh viễn shop và phạt tiền gian hàng — Lớp ③)*.

## 4. Mục `§4. Mức tự chủ`
- **4.1. Bảng mức tự chủ cho 5 Tool (theo Cost-of-Error):**
  - `yeu_cau_bang_chung`: **Tự làm** (có nút bỏ qua/gặp nhân viên).
  - `chuyen_truong_nhom`: **Tự làm** (Trưởng nhóm nhận trong 30p–2h).
  - `soan_hoan_tien`: **Cần người duyệt** (Shop hoặc Trưởng nhóm sàn duyệt dựa trên Snapshot + bằng chứng; quá hạn 24h shop im lặng thì chuyển Trưởng nhóm duyệt hoàn).
  - `tu_choi_khieu_nai`: **Cần người duyệt** (Nhân viên/Trưởng nhóm sàn duyệt; mở cửa sổ 24h cho khách bổ sung bằng chứng trước khi đóng).
  - `phat_shop`: **Cấm** (Chuyển bộ phận Pháp chế / Kiểm soát gian lận xử lý riêng).
- **4.2. Tool khó xếp nhất & Tách bước Tool:**
  - Chọn `soan_hoan_tien` (ghi nhận ý kiến ban đầu của Thứ, Hiếu, Trung và cái giá của mỗi phía trên Kịch bản 8, 9, 10).
  - Tách `soan_hoan_tien` thành 2 bước: `soan_ho_so_hoan_tien` (**Tự làm**) và `duyet_giai_ngan` (**Cần người duyệt**), kèm luật chọn rõ mã đơn (Kịch bản 4) và món hàng lỗi (Kịch bản 5) trước khi gọi `yeu_cau_bang_chung`.
- **4.3. Thử mức đã đặt trên 3 kịch bản:** Kiểm thử trên **Kịch bản 1** (đắt nhất 1), **Kịch bản 9** (đắt nhất 2) và **Kịch bản 8** (bình thường) theo 3 câu hỏi của Rubric.
- **4.4. Đổi lời hứa với người dùng:** Từ *"phán quyết và hoàn tiền ngay trong tích tắc"* sang *"giữ nguyên bằng chứng lúc đặt hàng, hướng dẫn 1 bước bổ sung và bảo vệ khoản tiền chờ hai bên xác nhận công bằng"*.
