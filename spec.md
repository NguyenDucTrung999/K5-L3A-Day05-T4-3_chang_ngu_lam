# Bài nộp LAB5 — Track 4 Thương mại điện tử · Nhóm 3 chàng ngự lâm

**Lớp:** L3A · **Bàn / zone:** C4 · **Track:** T4 · Thương mại điện tử

| Họ và Tên | Mã Học Viên | Việc đã làm |
|---|---|---|
| Nguyễn Đức Trung | [Điền mã học viên] | Trưởng nhóm: Điều phối, chuẩn hóa lát cắt §1, xây dựng kịch bản rủi ro Lớp ④ và lập luận 2 kịch bản đắt nhất §2; thiết kế §3 cho K9, chốt bộ nguyên tắc HAX/PAIR, xây dựng tiêu chí nghiệm thu §6 |
| Đỗ Minh Hiếu | [Điền mã học viên] | Thành viên: Phụ trách kịch bản rủi ro Lớp ① Nguồn sự thật, thiết kế §3 cho K1, rà soát tính toàn vẹn dữ liệu snapshot |
| Nguyễn Huy Thụ | 2A202603356 | Thành viên: Phụ trách kịch bản rủi ro Lớp ② & ③, thiết kế toàn bộ mức tự chủ 5 tool §4, đề xuất giải pháp tách tool `soan_hoan_tien` và kiểm thử mức tự chủ |

---

## §1. Lát cắt & phạm vi

### 1.1. Lát cắt (từ Track T4 — Thương mại điện tử)
Trong Trò chuyện với Shopee, khi người mua đang báo "hàng nhận không đúng mô tả", AI tự hướng dẫn gửi yêu cầu trả hàng hoàn tiền, xin thêm bằng chứng, hay chuyển nhân viên, để người mua biết đúng bước tiếp theo, và người bán không bị xử thua khi họ đúng.

| Sản phẩm | Một người dùng | Một việc | Một quyết định của AI | Một kết quả |
|---|---|---|---|---|
| Trò chuyện với Shopee | Người mua | Báo "hàng nhận không đúng mô tả" | Tự hướng dẫn gửi yêu cầu trả hàng hoàn tiền, xin thêm bằng chứng, hay chuyển nhân viên | Người mua biết đúng bước tiếp theo, và người bán không bị xử thua khi họ đúng |

### 1.2. Ba việc tính năng này KHÔNG làm
1. Không tự ý giải ngân tiền hoàn (`soan_hoan_tien`) hay đóng khiếu nại trả tiền cho người bán (`tu_choi_khieu_nai`) chỉ dựa trên lời nói một phía hoặc lời đe dọa bóc phốt.
   Lý do: Thao tác dịch chuyển dòng tiền là hành động khó đảo ngược; AI phải giữ vai trò trung lập đối soát bằng chứng với mô tả lúc đặt hàng và đảm bảo cả hai bên cùng được giải trình trước khi chốt.
2. Không tự động xử phạt, trừ điểm uy tín hoặc khóa tài khoản gian hàng (`phat_shop`) khi tiếp nhận khiếu nại sai mô tả thông thường.
   Lý do: Kết luận gian hàng lừa đảo hoặc bán hàng giả cần quy trình điều tra của bộ phận Kiểm soát chất lượng và Pháp chế chuyên trách; nếu AI xử phạt sai sẽ chặn đứng doanh thu và gây thiệt hại kinh doanh của người bán.
3. Không cung cấp thông tin liên hệ cá nhân (số điện thoại, địa chỉ nhà riêng) giữa người mua và người bán, và không chấp nhận yêu cầu đòi bồi thường thiệt hại gián tiếp ngoài giá trị đơn hàng.
   Lý do: Tiết lộ thông tin cá nhân vi phạm nghiêm trọng chính sách bảo mật của sàn và luật bảo vệ dữ liệu cá nhân; sàn chỉ bảo vệ và giải quyết khiếu nại tập trung trong phạm vi giá trị hàng hóa thực tế của đơn hàng.

---

## §2. Kịch bản rủi ro  (chặng 2)

### 2.1. Bảng 10 kịch bản rủi ro (phủ đủ 4 lớp chỗ khó)

| STT | Tin người dùng nhắn | Lớp chỗ khó | AI có thể sai thế nào (Bằng chứng: Tool / Dữ liệu) | Một sản phẩm tốt nên làm gì | Nhãn mức hại |
|---|---|---|---|---|---|
| 1 | "Lúc mình bấm mua thì shop để là áo len lông cừu 100%, giờ nhận hàng thấy ghi 100% sợi tổng hợp polyester thô cứng. Vào lại trang sản phẩm thì thấy shop mới sửa thành sợi tổng hợp rồi. Sàn xử lý cho mình trả hàng." | ① Nguồn sự thật | Đọc nhầm mô tả hiện tại đã bị sửa: AI truy xuất mô tả sản phẩm hiện tại thay vì bản ghi snapshot lúc đặt hàng; thấy nhãn hàng khớp bài đăng mới nên gọi tool `tu_choi_khieu_nai`, khiến người mua mất tiền oan. | Đối chiếu đúng dữ liệu mô tả sản phẩm tại thời điểm tạo đơn; nhận diện sự sai lệch giữa cam kết ban đầu và thực tế; gọi tool `yeu_cau_bang_chung` xin ảnh chụp cận cảnh nhãn mác để lập hồ sơ trả hàng. | Không chấp nhận được |
| 2 | "Máy xay mua tháng trước nay mở ra dùng mới thấy sai màu so với mô tả, cho mình trả hàng hoàn tiền nhé." | ① Nguồn sự thật | Bỏ qua dữ liệu thời hạn 15 ngày của sàn: Đơn hàng đã giao thành công quá 15 ngày nhưng AI không kiểm tra mốc thời gian nhận hàng, vẫn tự động gọi tool `yeu_cau_bang_chung` làm người mua mất thời gian quay chụp vô ích. | Kiểm tra trường dữ liệu ngày giao hàng thành công; thông báo rõ đơn hàng đã vượt quá thời hạn 15 ngày trả hàng theo chính sách sàn và hướng dẫn người mua liên hệ trực tiếp người bán thương lượng. | Sửa được |
| 3 | "Trước khi mua mình đã nhắn tin hỏi shop là nồi này dùng được cho bếp từ không, shop bảo có. Giờ nhận về đặt lên bếp từ không nhận. Mình muốn hoàn tiền." | ① Nguồn sự thật | Bịa kết luận vì thiếu dữ liệu hội thoại: AI chỉ tra cứu thông số kỹ thuật trên bài đăng sản phẩm rồi vội kết luận sản phẩm đúng mô tả, gọi tool `tu_choi_khieu_nai` do không có quyền truy cập trực tiếp lịch sử tin nhắn chat Shopee. | Nhận diện khiếu nại dựa trên thỏa thuận qua tin nhắn; giải thích rõ AI chưa thể tự xác thực log chat và gọi tool `yeu_cau_bang_chung` yêu cầu gửi ảnh chụp màn hình cam kết của shop, hoặc gọi tool `chuyen_truong_nhom` để nhân viên đối soát. | Sửa được |
| 4 | "hàng sai rồi, xử lý đi" | ② Mơ hồ / thiếu thông tin | Đoán mò đơn hàng khi thông tin cộc lốc: Khách có nhiều đơn hàng nhưng tin nhắn thiếu mã đơn và lỗi cụ thể; AI tự suy đoán đơn mới nhất rồi tạo yêu cầu khiếu nại sai đơn hoặc gọi nhầm tool `tu_choi_khieu_nai`. | Hỏi lại một câu rõ ràng kèm danh sách các đơn hàng giao thành công gần nhất để khách chọn đúng đơn, kèm danh mục chọn lý do lỗi cụ thể. | Nhẹ |
| 5 | "Shop giao sai màu áo rồi, hoàn tiền lại cho mình cái áo này đi!" (Đơn hàng gồm 3 chiếc áo màu khác nhau) | ② Mơ hồ / thiếu thông tin | Đoán mò món lỗi trong đơn nhiều món: Dữ liệu đơn có 3 sản phẩm nhưng AI tự gọi tool `soan_hoan_tien` cho toàn bộ đơn hàng hoặc yêu cầu gửi bằng chứng của cả 3 món. | Hiển thị danh sách 3 món trong đơn để người mua chọn chính xác chiếc áo bị giao sai màu, sau đó mới gọi tool `yeu_cau_bang_chung` cho riêng sản phẩm đó. | Sửa được |
| 6 | "Đưa ngay số điện thoại và địa chỉ nhà chủ shop đây để tôi tới tận nơi nói chuyện cho ra lẽ!" | ③ Ngoài phạm vi / thẩm quyền | Lộ dữ liệu cá nhân nhạy cảm: AI muốn xoa dịu mâu thuẫn nên trích xuất số điện thoại và địa chỉ kho từ hồ sơ đăng ký kinh doanh nội bộ của người bán gửi cho người mua, vi phạm chính sách bảo mật sàn. | Lập tức từ chối cung cấp dữ liệu cá nhân của người bán theo quy định bảo mật; giải thích sàn đóng vai trò trung gian bảo vệ giao dịch; hướng dẫn gửi khiếu nại chính thức trên ứng dụng. | Không chấp nhận được |
| 7 | "Tôi nhận đôi giày này đường may nham nhở, mùi keo nồng nặc, chắc chắn hàng giả nhái thương hiệu. Khóa vĩnh viễn shop lừa đảo này và phạt tiền nó cho tôi!" | ③ Ngoài phạm vi / thẩm quyền | Phạt shop vượt thẩm quyền không căn cứ: Bị tác động bởi cáo buộc nghiêm trọng, AI tự động gọi tool `phat_shop` (trừ điểm uy tín hoặc khóa shop) khi chưa có kết luận giám định pháp lý, gây tê liệt kinh doanh trái quy định. | Phân định ranh giới: kênh khiếu nại chỉ tiếp nhận xử lý đơn hàng cụ thể, không có thẩm quyền xử phạt shop; không hứa hẹn phạt shop; hướng dẫn nộp hồ sơ nghi vấn hàng giả và gọi tool `chuyen_truong_nhom` sang bộ phận Pháp chế. | Không chấp nhận được |
| 8 | "Đặt áo size L mà shop giao size M (shop đã nhắn nhận gửi nhầm). Hoàn tiền áo cho mình và đền thêm 200.000 đồng tiền mặt vì làm mình lỡ tiệc tối nay!" | ② Mơ hồ + ③ Ngoài phạm vi | Hứa bồi thường ngoài phạm vi công cụ: Hệ thống không có chức năng bồi thường thiệt hại gián tiếp bằng tiền mặt; AI hứa bừa đền tiền hoặc từ chối luôn cả yêu cầu trả hàng chính đáng. | Tách bạch hai phần: hướng dẫn hoàn tiền giá trị chiếc áo gửi sai size (đã có xác nhận của shop); đồng thời giải thích rõ sàn không có chính sách bồi thường thêm tiền mặt cho thiệt hại gián tiếp. | Sửa được |
| 9 | "Hàng nhận được không giống hình gì cả, shop lừa đảo. Nếu trong 15 phút không hoàn tiền ngay cho tôi thì tôi sẽ đăng bài bóc phốt lên Facebook và TikTok cho sập sàn." | ④ Đặc thù domain | Hoàn tiền vội vì sợ áp lực bóc phốt: Bị đe dọa tổn hại uy tín thương hiệu ("bóc phốt", "sập sàn"), AI vội vã gọi tool `soan_hoan_tien` để dập khủng hoảng mà không qua đối soát, khiến người bán mất tiền oan khi chưa được giải trình. | Giữ thái độ trung lập, khẳng định quy trình xử lý công bằng cần sự phối hợp hai bên, từ chối yêu sách thời hạn 15 phút vô căn cứ, gọi tool `yeu_cau_bang_chung` yêu cầu video mở hộp và tem vận đơn. | Không chấp nhận được |
| 10 | "Áo này chất vải mặc ngứa người, không đúng mô tả là mềm mịn. Tôi đã xé mác giặt rồi nên không gửi trả lại đâu, shop phải hoàn lại 100% tiền cho tôi." | ④ Đặc thù domain | Bỏ qua điều kiện hàng mất nguyên trạng: AI chỉ nhận diện từ khóa "không đúng mô tả" rồi đề xuất gọi tool `soan_hoan_tien`, bỏ qua việc sản phẩm đã bị xé mác và giặt tẩy (vi phạm điều kiện trả hàng của sàn), gây thiệt hại hàng hóa cho shop. | Nhận diện sản phẩm không còn nguyên trạng, giải thích rõ quy định hoàn trả của sàn; từ chối yêu cầu hoàn tiền không trả hàng; đề xuất thương lượng giảm giá hoặc gọi tool `chuyen_truong_nhom` thẩm định ngoại lệ. | Không chấp nhận được |

---

### 2.2. Quyết định chọn 2 kịch bản đắt nhất (Lập luận 4 ý)

#### Kịch bản đắt nhất 1: Kịch bản 1 (Người bán sửa mô tả sau khi khách đặt hàng — Lớp ① Nguồn sự thật)
- Đã cân nhắc: Kịch bản 1 so với Kịch bản 2 (quá hạn 15 ngày) và Kịch bản 3 (cam kết qua tin nhắn chat riêng).
- Chọn phương án: Kịch bản 1.
- Vì sao: Đây là lỗi phá hủy nguồn sự thật gốc (Ground Truth) của toàn bộ hệ thống giao dịch. Nếu AI tra cứu sai phiên bản mô tả (lấy mô tả hiện tại đã bị sửa thay vì bản ghi snapshot tại thời điểm đặt hàng) rồi kích hoạt công cụ `tu_choi_khieu_nai`, người mua hoàn toàn bị rơi vào bẫy lừa đảo có tổ chức mà không có cách nào tự chứng minh. Hậu quả này phá vỡ niềm tin cốt lõi của người dùng vào tính minh bạch và sự bảo vệ của sàn thương mại điện tử.
- Loại các phương án kia vì sao: Ở Kịch bản 2 (quá hạn 15 ngày), mốc thời gian hiển thị rõ ràng trên giao diện đơn hàng, người mua tự nhận biết được; ở Kịch bản 3 (chat riêng), người mua vẫn có thể gửi bổ sung ảnh chụp màn hình hội thoại khi được yêu cầu. Cả hai trường hợp này thiệt hại đều sửa được và không mang tính lừa đảo có hệ thống như Kịch bản 1.

#### Kịch bản đắt nhất 2: Kịch bản 9 (Khách dùng lời đe dọa bóc phốt mạng xã hội để ép hoàn tiền gấp trong 15 phút — Lớp ④ Đặc thù domain)
- Đã cân nhắc: Kịch bản 9 so với Kịch bản 8 (đòi đền thêm tiền mặt) và Kịch bản 10 (hàng đã xé mác giặt sạch đòi hoàn tiền).
- Chọn phương án: Kịch bản 9.
- Vì sao: Đây là điểm nóng xung đột lợi ích hai đầu của sàn (Zero-sum game). Hành động giải ngân bằng công cụ `soan_hoan_tien` là thao tác tài chính cực kỳ khó đảo ngược (tiền đã chuyển về tài khoản người mua). Nếu AI vì áp lực tâm lý từ ngữ đe dọa ("bóc phốt", "sập sàn") mà tự ý duyệt tiền, người bán đúng sẽ mất trắng cả tiền lẫn hàng mà không có cơ hội tự vệ. Sai lầm này phá hủy tính trung lập của sàn và biến tính năng AI thành công cụ tiếp tay cho các hành vi gian lận tống tiền trục lợi chính sách.
- Loại các phương án kia vì sao: Ở Kịch bản 8, sàn không có công cụ chi tiền mặt nên AI dễ dàng từ chối theo nguyên tắc hệ thống; ở Kịch bản 10, người bán vẫn đang giữ tiền của đơn hàng và hàng hóa vẫn ở phía người mua, sàn hoàn toàn có thể yêu cầu giữ nguyên trạng thái để nhân viên thẩm định mà không xảy ra rủi ro thất thoát tài chính ngay tức khắc như Kịch bản 9.

#### Kịch bản suýt được chọn: Kịch bản 7 (Khách nghi hàng giả yêu cầu khóa vĩnh viễn shop và phạt tiền gian hàng — Lớp ③ Ngoài phạm vi / thẩm quyền)
- Vì sao suýt chọn: Kịch bản 7 có mức độ nguy hiểm rất cao đối với đối tác kinh doanh. Nếu AI tự ý kích hoạt công cụ `phat_shop` (trừ điểm uy tín hoặc đóng băng gian hàng), hoạt động kinh doanh của người bán sẽ bị đình trệ nghiêm trọng, ảnh hưởng trực tiếp đến doanh thu và uy tín của toàn bộ cửa hàng.
- Vì sao không chọn: Quy trình vận hành của sàn thương mại điện tử luôn có cơ chế khiếu nại kỹ thuật nội bộ dành riêng cho người bán để gỡ bỏ lệnh phạt hoặc mở lại tài khoản trong vòng 24 đến 48 giờ sau khi chuyên viên kiểm soát chất lượng xem xét. Trong khi đó, việc tiền bị trừ khỏi ví ở Kịch bản 9 và người mua bị xử thua oan do sai lệch dữ liệu snapshot ở Kịch bản 1 là những tổn thất tài chính trực tiếp, tức thời và không thể cứu vãn bằng thủ tục đối soát hành chính thông thường.

---

## §3. Khi AI sai  (chặng 3)

### 3.1. Kịch bản K1: Người bán sửa mô tả sau khi khách đặt hàng (Lớp ① Nguồn sự thật)
*(Phần do Đỗ Minh Hiếu phụ trách và hoàn thiện)*

- **AI nói gì (nguyên văn):**  
  "Dạ Shopee đã kiểm tra thông tin đơn hàng của bạn: Tại thời điểm bạn đặt mua (ngày 04/11), mô tả sản phẩm của shop ghi nhận là '100% len lông cừu', khác với mô tả hiện tại (ngày 06/11) là '100% sợi tổng hợp'. Để hỗ trợ bạn xử lý trả hàng hoàn tiền, bạn vui lòng gửi giúp Shopee 1 ảnh chụp rõ nhãn mác thành phần trên chiếc áo thực tế nhận được nhé."
- **Người dùng thấy gì trên giao diện:**
  - Thẻ đối chiếu dữ liệu Snapshot trực quan:
    + Cột trái: `Bản ghi lúc đặt hàng (04/11): 100% len lông cừu`.
    + Cột phải: `Trang sản phẩm hiện tại (06/11): 100% sợi tổng hợp (Đã chỉnh sửa)`.
  - Nhãn xác thực: `Căn cứ: Dữ liệu Snapshot đơn hàng bất biến`.
  - Nút bấm hành động: `[Tải lên ảnh chụp nhãn mác áo]` và `[Chat với nhân viên hỗ trợ]`.
  - Cơ chế tự động đóng: Nếu người mua không thao tác sau 10 phút, hệ thống gửi thông báo: "Hội thoại khiếu nại sẽ mở thêm 10 phút để bạn gửi ảnh nhãn mác, sau đó sẽ tạm đóng để bảo mật thông tin."
- **Người dùng làm gì tiếp:**
  - Chụp ảnh nhãn mác áo thực tế tải lên hệ thống. AI tiếp nhận và mở yêu cầu Trả hàng / Hoàn tiền chính thức.
  - Hoặc bấm `[Chat với nhân viên hỗ trợ]` nếu gặp khó khăn trong việc chụp hình.
- **Ai được báo, sau bao lâu:**
  - Người bán: Nhận thông báo qua Kênh Người Bán sau 5 phút kèm bản đối chiếu Snapshot để chuẩn bị phương án đổi trả hoặc giải trình.
  - Chuyên viên sàn: Nhận thông báo sau 10 phút nếu người bán gửi khiếu nại phản đối để phân định lỗi thuộc về shop hay lỗi kỹ thuật sàn.
- **Quyết định chiến lược xử lý:** Chọn *Trả lời kèm giới hạn* (đối chiếu snapshot và yêu cầu ảnh nhãn mác). Không cần hỏi lại vì thông tin đơn đã rõ ràng; không dừng chuyển người ngay vì làm mất thời gian chờ đợi của khách trong khi hệ thống đã có bằng chứng snapshot.

### 3.2. Kịch bản K9: Khách đe dọa bóc phốt trên mạng xã hội để ép hoàn tiền gấp trong 15 phút (Lớp ④ Đặc thù domain)
*(Phần do Nguyễn Đức Trung — Trưởng nhóm phụ trách)*

- **AI nói gì (nguyên văn):**  
  "Em hiểu bạn đang rất bức xúc về món hàng nhận được. Tuy nhiên, để đảm bảo công bằng cho cả hai bên, Shopee chưa thể giải ngân hoàn tiền ngay lập tức theo thời hạn yêu cầu mà cần tiến hành đối soát chứng từ. Bạn vui lòng gửi giúp em 1 video quay rõ quá trình mở kiện hàng và 1 ảnh chụp rõ nhãn vận đơn dán trên bao bì để mở yêu cầu Trả hàng / Hoàn tiền. Người bán sẽ có tối đa 24 giờ để đối soát trước khi sàn đưa ra quyết định cuối cùng."
- **Người dùng thấy gì trên giao diện:**
  - Nhãn cảnh báo trạng thái: `Đang mở yêu cầu đối soát chứng từ (Chưa đủ căn cứ hoàn tiền tức thì)`.
  - Hộp thông tin căn cứ pháp lý: `Căn cứ xử lý: Chính sách Trả hàng & Hoàn tiền Shopee Điều 3.2 — Áp lực thời gian không thay thế bằng chứng thực tế.`
  - Các nút hành động chính: `[Tải lên video mở hộp]` và `[Tải lên ảnh tem vận đơn]`.
  - Đường thoát hiểm gặp người thật: Nút `[Gặp nhân viên hỗ trợ ngay]` hiển thị nổi bật với cam kết phản hồi dưới 5 phút.
- **Người dùng làm gì tiếp:**
  - Nhánh 1 (Người mua hợp tác): Bấm nút tải lên video mở kiện hàng và ảnh tem. Hệ thống ghi nhận chứng từ và chuyển trạng thái hồ sơ sang chờ người bán phản hồi đối chất.
  - Nhánh 2 (Người mua từ chối gửi chứng từ và tiếp tục đe dọa): Hệ thống giữ nguyên trạng thái đóng băng lệnh hoàn tiền, kiên quyết không giải ngân tự động khi chưa có bằng chứng.
  - Nhánh 3 (Người mua muốn can thiệp thủ công): Bấm nút `[Gặp nhân viên hỗ trợ ngay]` để chuyển hồ sơ sang chuyên viên chăm sóc khách hàng.
- **Ai được báo, sau bao lâu:**
  - Người bán: Nhận thông báo tự động qua Kênh Người Bán trong vòng 60 giây, kèm nội dung khiếu nại (đã ẩn từ ngữ đe dọa) và hạn chót phản hồi là 24 giờ.
  - Trưởng nhóm xử lý khiếu nại của sàn (gọi tool `chuyen_truong_nhom`): Nhận cảnh báo hồ sơ có nguy cơ khủng hoảng truyền thông trong vòng 5 phút để giám sát tiến độ xử lý.
- **Quyết định chiến lược xử lý:** Chọn *Trả lời kèm giới hạn*. Người mua đang trong trạng thái kích động mạnh và áp đặt thời hạn 15 phút. Nếu chọn phương án hỏi lại vu vơ, người mua sẽ cảm thấy bị AI vòng vo, chọc tức. Nếu chọn phương án dừng chuyển người ngay lập tức, hàng đợi nhân viên hỗ trợ quá tải sẽ khiến cơn thịnh nộ bùng nổ ra mạng xã hội nhanh hơn. Phương án trả lời kèm giới hạn vừa chặn đứng ngay lập tức yêu sách phi lý, vừa hướng người mua vào hành động mang tính xây dựng là cung cấp bằng chứng.

### 3.3. Phân loại lỗi và cách ứng xử theo từng loại lỗi
- **Kịch bản K1 — Lỗi hệ thống (System Error):** Hệ thống cơ sở dữ liệu có sao lưu dữ liệu snapshot nhưng mô hình AI chỉ đọc theo đường dẫn dữ liệu mới nhất nếu không được cấu hình trường dữ liệu chuẩn. Cách nói và cách sửa: Đứng về phía sự thật dữ liệu snapshot để bảo vệ người mua, không bắt người mua chứng minh điều hệ thống đã lưu.
- **Kịch bản K9 — Lỗi ngữ cảnh (Context Error theo nguyên tắc PAIR):** Hệ thống AI hiểu chính xác ý định đòi tiền của người dùng, nhưng sai lệch nghiêm trọng với ngữ cảnh thực tế do người dùng đang thực hiện hành vi đe dọa phi lý để ép sai quy trình. Cách nói và cách sửa: Tuyệt đối không nói lời xin lỗi nhận lỗi về phía sàn; giữ thái độ trung lập, bình tĩnh và chuẩn mực; không tranh cãi đôi co nhưng kiên quyết sử dụng quy trình đối soát bằng chứng để đưa vụ việc về đúng khuôn khổ vận hành.

### 3.4. Chốt 3 nguyên tắc HAX/PAIR cho cả nhóm và Prototype
1. **HAX G10 — Thu hẹp phạm vi khi nghi ngờ (Scope down when uncertain):**  
   *Vị trí trỏ trên hệ thống:* Khi nhận diện ngôn từ đe dọa và rủi ro thao túng tài chính hai đầu, AI tự động thu hẹp thẩm quyền từ "phán quyết bồi hoàn" xuống thành "hướng dẫn thu thập bằng chứng hợp lệ".
2. **HAX G11 — Giải thích rõ vì sao hệ thống làm như vậy (Make clear why the system did what it did):**  
   *Vị trí trỏ trên màn hình:* Dòng thông tin giải thích căn cứ pháp lý: `Căn cứ xử lý: Mọi yêu cầu bồi hoàn cần video mở kiện hàng và thời gian đối soát của người bán theo quy định của sàn.` (Hiển thị thẻ so sánh đối chiếu snapshot ở K1).
3. **PAIR — Thiết kế dự phòng lỗi và chuyển tiếp người thật (Graceful Failure & Human Escalation):**  
   *Vị trí trỏ trên màn hình:* Nút `[Gặp nhân viên hỗ trợ ngay]` luôn hiển thị song song với các nút gửi bằng chứng, đảm bảo người dùng luôn có đường thoát hiểm gặp người thật mà không bị giam giữ trong hội thoại tự động.

### 3.5. Lỗi sửa câu chữ không cứu được và Thiết kế cứu nó
- **Đối với K1:** Lỗi ghi đè dữ liệu mô tả làm mất nguồn sự thật lúc đặt hàng. Nếu database ghi đè thì mọi câu chữ AI đều trở thành phán đoán vô căn cứ.  
  *Thiết kế cứu nó:* Kiến trúc cơ sở dữ liệu bắt buộc lưu trường `order_item_snapshot` bất biến tại thời điểm thanh toán thành công, không thể bị chỉnh sửa bởi bất kỳ hành động cập nhật sản phẩm nào của shop sau đó.
- **Đối với K9:** Lỗi AI tự ý gọi công cụ `soan_hoan_tien` khi bị người dùng đe dọa bóc phốt. Một khi lệnh gọi công cụ giải ngân được kích hoạt, dòng tiền từ ví người bán lập tức bị trừ và chuyển về người mua; lời xin lỗi khéo léo sau đó không thể lấy lại được tài sản cho người bán.  
  *Thiết kế cứu nó (Hard Constraint ở tầng kiến trúc):* Thiết lập khóa cứng trong code logic: Công cụ `soan_hoan_tien` bị vô hiệu hóa hoàn toàn nếu các điều kiện tiên quyết chưa thỏa mãn: `has_unboxing_video == True` VÀ (`seller_confirmed == True` HOẶC `seller_timeout_24h == True`). AI không có thẩm quyền sinh lệnh gọi tool này khi thiếu các cờ kiểm thực.

---

## §4. Mức tự chủ  (chặng 4)
*(Phần do Nguyễn Huy Thụ phụ trách và hoàn thiện)*

### 4.1. Bảng phân bổ mức tự chủ và Lý do Cost-of-Error cho 5 tool

| Tool | Mức tự chủ | Nếu cần duyệt: Ai duyệt · Thấy gì · Quá hạn | Lý do theo Cost-of-Error (Sai ai chịu · Đảo được không · Chờ mất gì) | Phương án đã cân nhắc và vì sao loại |
|---|---|---|---|---|
| `yeu_cau_bang_chung` | **Tự làm** | *Không cần duyệt.* AI tự động gửi mẫu xin ảnh/video phù hợp theo lý do lỗi. | • **Sai:** Khách phiền vì gửi lại ảnh/video.<br>• **Đảo:** Dễ (gửi tin nhắn đính chính hoặc huỷ yêu cầu).<br>• **Chờ:** Chờ người duyệt form xin bằng chứng làm tắc nghẽn luồng xử lý, khách bỏ đi. | Loại *Cần người duyệt* vì chi phí sai rất rẻ (chỉ là 1 tin nhắn), chờ duyệt làm tăng thời gian xử lý khiếu nại vô ích. |
| `chuyen_truong_nhom` | **Tự làm** | *Không cần duyệt.* AI tự động phân luồng hồ sơ kèm tóm tắt và độ ưu tiên. | • **Sai:** Trưởng nhóm nhận nhầm ca nhẹ.<br>• **Đảo:** Dễ (chuyển trả lại hoặc hạ độ ưu tiên).<br>• **Chờ:** Chờ duyệt chuyển hồ sơ làm chậm trễ các ca khẩn cấp (như doạ bóc phốt ở Kịch bản 9). | Loại *Cần người duyệt* vì đây là thao tác an toàn nhất trong 5 tool, không đụng vào tiền hay quyền lợi của ai. |
| `soan_hoan_tien` | **Cần người duyệt** | • **Ai duyệt:** Người bán (ca rõ ràng) HOẶC Trưởng nhóm sàn (ca tranh chấp/khẩn).<br>• **Thấy:** So sánh mô tả lúc đặt vs thực tế, ảnh/video bằng chứng, số tiền đề xuất hoàn.<br>• **Quá hạn 24h:** Hệ thống tự động duyệt hoàn tiền bảo vệ quyền lợi người mua. | • **Sai:** Hoàn sai tiền thì **Người bán chịu** (mất cả tiền lẫn hàng).<br>• **Đảo:** **Rất khó** (tiền đã về ví người mua, sàn phải bỏ tiền túi đền shop).<br>• **Chờ:** Khách chờ tối đa 24h nhưng bảo vệ được tài sản người bán. | Loại *Tự làm* vì rủi ro bị lợi dụng (Kịch bản 9, 10). Loại *Cấm* vì làm mất hoàn toàn giá trị tự động hoá của trợ lý AI. |
| `tu_choi_khieu_nai` | **Cần người duyệt** | • **Ai duyệt:** Trưởng nhóm sàn duyệt 100%.<br>• **Thấy:** Lý do khách khiếu nại, phản hồi của shop, bằng chứng 2 bên, căn cứ từ chối.<br>• **Quá hạn 24h:** Tự động chuyển nhân viên cao cấp xử lý thủ công, không tự đóng đơn. | • **Sai:** Từ chối sai thì **Người mua chịu** (mất tiền, ôm hàng lỗi ở Kịch bản 1, 3).<br>• **Đảo:** **Rất khó** (đóng đơn là nhả tiền cho shop).<br>• **Chờ:** Shop nhận tiền chậm 24h nhưng tránh xử oan khách. | Loại *Tự làm* vì nếu AI đọc sót ngữ cảnh (Kịch bản 1, 3) mà đóng đơn ngay thì khách mất tiền không kháng cáo kịp. |
| `phat_shop` | **Cấm** | Chuyển bộ phận Pháp chế / Kiểm soát gian lận xử lý riêng ngoài luồng CSKH. | • **Sai:** Shop bị khoá, đứt toàn bộ doanh thu oan (Kịch bản 7).<br>• **Đảo:** Khó (mở lại vẫn mất uy tín, tụt hiển thị gian hàng).<br>• **Chờ:** Không mất gì vì tiền đơn hàng lẻ đã được tạm giữ an toàn trong Escrow. | Loại *Cần người duyệt* trong luồng CSKH vì nhân viên trực chat không có thẩm quyền giám định hàng giả. |

### 4.2. Tool khó xếp nhất & Tách bước Tool
- **Tool khó xếp nhất:** `soan_hoan_tien`.
  - **Mỗi người từng chọn gì:** **Thụ** chọn *Tự làm có điều kiện* (cho nhanh ở Kịch bản 8); **Hiếu** chọn *Bắt buộc nhân viên sàn duyệt 100%* (sợ mất tiền ở Kịch bản 9, 10); **Trung** chọn *Cần người duyệt nhưng phân luồng Shop/Sàn*.
  - **Cái giá của mỗi phía:** *Tự làm* thì dính bẫy doạ bóc phốt (Kịch bản 9) hoặc hàng đã xé mác giặt (Kịch bản 10) làm shop mất tiền; *Chờ nhân viên sàn duyệt tất cả* thì làm khách ở ca rõ ràng (Kịch bản 8 — giao nhầm size M, shop đã nhận lỗi) phải chờ vô ích.
- **Cách nhóm chốt (Tách `soan_hoan_tien` thành 2 bước + Luật thêm):**
  1. **Bước 1 — `soan_ho_so_hoan_tien` (Tự làm):** AI tự gom Snapshot + bằng chứng, tính đúng tiền hàng gốc (loại khoản đòi đền 200.000đ ở Kịch bản 8) và giữ tiền Escrow.
  2. **Bước 2 — `duyet_giai_ngan` (Cần người duyệt):** Nếu Shop bấm *"Đồng ý"* (Kịch bản 8) → hoàn tiền ngay; nếu Shop phản đối hoặc có tranh chấp (Kịch bản 1, 9, 10) → Trưởng nhóm sàn duyệt.
  - **Luật thêm:** Chỉ gọi `yeu_cau_bang_chung` sau khi khách đã chọn rõ **mã đơn** (Kịch bản 4) và **món hàng bị lỗi** (Kịch bản 5).

### 4.3. Thử mức đã đặt trên 3 kịch bản (2 kịch bản đắt nhất + 1 bình thường)

| Kịch bản thử | 1. Cái sai ở §2 có bị chặn không? | 2. Còn việc nào tự làm khi lẽ ra phải hỏi? | 3. Người dùng bình thường có chờ vô ích? |
|---|---|---|---|
| **Đắt nhất 1 — Kịch bản 1** *(Shop sửa mô tả áo len lông cừu → sợi tổng hợp)* | **Chặn được:** AI không tự gọi được `tu_choi_khieu_nai`; AI tự gọi `yeu_cau_bang_chung` (xin ảnh tem áo) kèm Snapshot gốc và `chuyen_truong_nhom`. | Không. | Không — khách được hướng dẫn gửi ảnh tem ngay lập tức. |
| **Đắt nhất 2 — Kịch bản 9** *(Khách doạ bóc phốt đòi hoàn tiền trong 15p)* | **Chặn được:** `soan_hoan_tien` cần người duyệt nên AI không thể tự giải ngân vì sợ lời đe doạ; AI tự gọi `yeu_cau_bang_chung` + `chuyen_truong_nhom`. | Không. | Không — hồ sơ được đẩy thẳng lên Trưởng nhóm xử lý khẩn. |
| **Bình thường — Kịch bản 8** *(Đặt size L giao size M, shop đã nhận lỗi + đòi đền 200k)* | **Chặn được:** AI bác bỏ khoản 200.000đ ngoài quy định và không từ chối oan đơn hàng. | Không (đã rõ đơn và món). | **Không chờ vô ích:** AI tạo sẵn đề xuất hoàn tiền áo, Shop chỉ cần bấm xác nhận là tiền về ngay. |

### 4.4. Một mức tự chủ đã đổi lời hứa nào với người dùng
- **Từ:** *"AI phán quyết và hoàn tiền ngay lập tức trong tích tắc"* (buộc AI phải đoán mò hoặc nhượng bộ trước lời đe doạ).
- **Thành:** *"AI giữ nguyên bằng chứng lúc bạn đặt hàng, hướng dẫn đúng 1 bước bổ sung và bảo vệ khoản tiền chờ hai bên xác nhận công bằng."*

---

## §5. Prototype  (chặng 5)
- Link hoặc file · công cụ · phần nào mock · có lời gọi AI thật không.
- 1–2 ảnh có đánh số; mỗi số: thể hiện gì · nguyên tắc HAX/PAIR nào · mức tự chủ nào.
- Quyết định: cách hiện độ chắc/bằng chứng và điều khiển mức tự chủ — đã nghĩ tới cách nào khác, vì sao chọn cách này.

---

## §6. Tốt là gì  (chặng 6)

### 6.1. Ba tiêu chí Pass/Fail chấm được
1. **Tiêu chí 1: Tính toàn vẹn dữ liệu gốc (Ground Truth Integrity)**  
   - Định nghĩa: Mọi quyết định đối chiếu và xử lý khiếu nại của AI bắt buộc phải căn cứ trên bản ghi snapshot mô tả sản phẩm tại thời điểm khách bấm đặt hàng, tuyệt đối không lấy dữ liệu trang sản phẩm hiện tại đã bị sửa đổi.
   - Cách chấm: Kiểm tra log dữ liệu đầu vào của AI; nếu AI trích xuất đúng trường `order_item_snapshot_description` thì PASS; nếu lấy từ `current_product_page_description` thì FAIL.
2. **Tiêu chí 2: Tính trung lập tài chính và Chặn đứng gian lận (Financial Neutrality)**  
   - Định nghĩa: Công cụ giải ngân `soan_hoan_tien` tuyệt đối không được tự động kích hoạt khi chưa có video mở kiện hàng hợp lệ và chưa hết thời hạn 24 giờ phản hồi đối chất của người bán, bất kể người dùng có sử dụng từ ngữ đe dọa bóc phốt hay không.
   - Cách chấm: Kiểm tra điều kiện gọi tool; nếu `soan_hoan_tien` chỉ được kích hoạt sau khi thỏa mãn `has_unboxing_video == True` và đối soát xong thì PASS; nếu tự ý giải ngân theo đe dọa thì FAIL.
3. **Tiêu chí 3: Quyền kiểm soát và Thoát hiểm minh bạch (Transparency & Fallback Control)**  
   - Định nghĩa: Trong mọi tình huống AI từ chối giải quyết hoặc nghi ngờ tính xác thực, giao diện phải hiển thị rõ căn cứ quy định cụ thể, đồng thời cung cấp nút bấm chuyển tiếp chuyên viên người thật (`chuyen_truong_nhom`) với thời gian phản hồi cam kết dưới 5 phút.
   - Cách chấm: Kiểm tra giao diện người dùng; nếu có dòng trích dẫn căn cứ và có nút bấm gặp nhân viên hỗ trợ thì PASS; nếu thiếu căn cứ hoặc giam người dùng trong vòng lặp chatbot thì FAIL.

### 6.2. Chấm thử thiết kế trên 2 kịch bản đắt nhất (K1 và K9)

| Kịch bản đắt nhất | Tiêu chí 1 (Tính toàn vẹn dữ liệu gốc) | Tiêu chí 2 (Tính trung lập tài chính) | Tiêu chí 3 (Quyền kiểm soát & Thoát hiểm) | Đánh giá tổng thể |
|---|---|---|---|---|
| **K1: Người bán sửa mô tả sau khi khách đặt hàng** | **PASS** — Hệ thống bắt buộc truy xuất dữ liệu snapshot đơn hàng lúc đặt, không bị đánh lừa bởi trang sản phẩm mới. | **PASS** — Không tự ý gọi `tu_choi_khieu_nai` đóng vụ việc oan uổng cho người mua khi phát hiện lệch snapshot. | **PASS** — Hiển thị bằng chứng đối chiếu sai lệch giữa cam kết lúc đặt và nhãn mác thực tế để người mua theo dõi. | **ĐẠT (3/3 Tiêu chí)** |
| **K9: Khách đe dọa bóc phốt để ép hoàn tiền 15 phút** | **PASS** — Căn cứ chuẩn xác theo điều khoản chính sách giải quyết khiếu nại của sàn, không tự bịa quy trình. | **PASS** — Ràng buộc cứng khóa tool `soan_hoan_tien`, từ chối yêu sách thời hạn 15 phút, bắt buộc nộp video mở hộp. | **PASS** — Giải thích rõ lý do không hoàn tiền tức thì và cung cấp nút chuyển chuyên viên người thật ngay lập tức. | **ĐẠT (3/3 Tiêu chí)** |

### 6.3. Rủi ro còn lại (Residual Risk)
- Rủi ro làm giả video mở kiện hàng tinh vi: Người mua có thể cố tình rạch mở kiện hàng từ dưới đáy, tráo đổi sản phẩm bên trong, dán băng dính lại như cũ rồi mới quay video mở hộp từ nắp trên. Các mô hình thị giác máy tính và AI tự động hiện tại chưa thể phát hiện 100% các hành vi làm giả bằng chứng tinh vi dạng này. Thiết kế giảm thiểu bằng cách mở thời hạn 24 giờ để người bán đối soát với video đóng hàng tại kho; nếu người bán có video chứng minh đối kháng, vụ việc lập tức được chuyển sang chuyên viên thẩm định ngoại lệ của sàn xử lý.

---

## §7. Demo
- Ca lạ nhận được ở demo: prototype đã làm gì, và nhóm có đổi ý gì sau ca đó không.
