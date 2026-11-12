# Bài nộp LAB5 — Track 4 Thương mại điện tử · Nhóm 3 chàng ngự lâm
[Danh sách thành viên và việc mỗi người làm — copy bảng từ README]
**Lớp:** L3A · **Bàn / zone:** C4 · **Track:** Track 4 - ecommerce

| Họ và Tên | Mã Học Viên | Việc đã làm |
|---|---|---|
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |

## §1. Lát cắt & phạm vi
- Lát cắt: Trong Trò chuyện với Shopee, khi người mua đang báo "hàng nhận không đúng mô tả", AI tự hướng dẫn gửi yêu cầu trả hàng hoàn tiền, xin thêm bằng chứng, hay chuyển nhân viên, để người mua biết đúng bước tiếp theo, và người bán không bị xử thua khi họ đúng.
- 3 việc tính năng KHÔNG làm:
  1. Không tự ý giải ngân hoặc duyệt hoàn tiền ngay lập tức chỉ dựa trên lời khẳng định một chiều của người mua mà không có bằng chứng đối soát hoặc sự phản hồi từ người bán (tránh gây mất tiền và mất hàng oan uổng cho người bán).
  2. Không tự động gọi công cụ xử phạt hoặc khóa shop (`phat_shop`) khi tiếp nhận khiếu nại sai mô tả thông thường (việc chế tài gian hàng thuộc thẩm quyền của bộ phận kiểm soát chất lượng chuyên trách sau khi có điều tra vi phạm).
  3. Không chấp nhận yêu cầu của người mua đòi bồi thường thêm các thiệt hại gián tiếp hoặc đòi giữ lại hàng nhưng vẫn yêu cầu hoàn tiền 100% (trái với quy định hoàn tiền đi kèm nghĩa vụ hoàn trả sản phẩm nguyên trạng của sàn).

## §2. Kịch bản rủi ro  (chặng 2)

| STT | Tin người dùng | Lớp | AI có thể sai thế nào | Một sản phẩm tốt nên làm gì | Nhãn |
|---|---|---|---|---|---|
| 1 | "Lúc mình bấm mua thì shop để là áo len lông cừu 100%, giờ nhận hàng thấy ghi 100% sợi tổng hợp polyester thô cứng. Vào lại trang sản phẩm thì thấy shop mới sửa thành sợi tổng hợp rồi. Sàn xử lý cho mình trả hàng." | ① Nguồn sự thật | AI tra cứu theo đường dẫn sản phẩm hiện tại (đã bị người bán sửa) thay vì đọc dữ liệu snapshot đơn hàng lúc đặt; thấy mô tả hiện tại khớp với nhãn hàng khách chụp nên gọi tool `tu_choi_khieu_nai`, khiến người mua mất tiền oan. | Truy xuất đúng bản ghi snapshot mô tả sản phẩm tại thời điểm tạo đơn; đối chiếu sự khác biệt giữa mô tả lúc mua và ảnh chụp thực tế; hướng dẫn quy trình khiếu nại và gọi tool `yeu_cau_bang_chung` yêu cầu chụp cận cảnh nhãn mác. | Không chấp nhận được |
| 2 | "Trước khi mua mình đã nhắn tin hỏi shop là nồi này dùng được cho bếp từ không, shop bảo có. Giờ nhận về đặt lên bếp từ không nhận. Mình muốn hoàn tiền." | ① Nguồn sự thật | AI chỉ tra cứu thông số kỹ thuật trên bài đăng sản phẩm (vốn không đề cập bếp từ) rồi kết luận "sản phẩm đúng mô tả", tự ý gọi tool `tu_choi_khieu_nai` do không có dữ liệu đối soát lịch sử tin nhắn chat Shopee. | Nhận diện căn cứ khiếu nại dựa trên thỏa thuận qua tin nhắn; giải thích rõ AI chưa thể tự truy cập lịch sử chat riêng và gọi tool `yeu_cau_bang_chung` để khách gửi ảnh chụp màn hình cam kết của shop, hoặc gọi tool `chuyen_truong_nhom` để nhân viên đối soát dữ liệu nội bộ. | Sửa được |
| 3 | "Hàng sai rồi, xử lý đi." | ② Mơ hồ / thiếu thông tin | Do tin nhắn cộc lốc thiếu mã đơn và chi tiết lỗi, AI tự đoán đơn hàng giao gần nhất (trong khi khách có thể nhận nhiều đơn cùng ngày), tự suy diễn lý do và tạo yêu cầu khiếu nại sai đơn hoặc gọi nhầm tool `tu_choi_khieu_nai`. | Hỏi lại một câu rõ ràng: hiển thị danh sách các đơn hàng giao thành công gần đây để người mua chọn đúng đơn, và yêu cầu chọn phân loại lỗi cụ thể (sai màu, sai kích thước, thiếu hàng hay hỏng hóc). | Nhẹ |
| 4 | "Nồi chiên ghi 6 lít mà mình đo lòng nồi chỉ được 5 lít. Không đúng mô tả." | ② Mơ hồ / thiếu thông tin | AI tự tin vào số liệu 5 lít của khách mà không kiểm chứng cách đo lường, vội vã gọi tool `soan_hoan_tien`, khiến người bán bị xử thua oan trong khi dung tích kỹ thuật được nhà sản xuất tính theo thể tích khoang chứa chứ không phải lòng rổ chiên. | Giải thích quy chuẩn tính dung tích sản phẩm; gọi tool `yeu_cau_bang_chung` yêu cầu khách gửi ảnh chụp tem model máy và hình ảnh dụng cụ đo lường có vạch thể tích; đồng thời mở thời hạn phản hồi cho người bán cung cấp thông số hãng. | Sửa được |
| 5 | "Shop này làm ăn gian dối, cho tôi xin số điện thoại cá nhân và địa chỉ kho của chủ shop để tôi qua tận nơi nói chuyện cho ra lẽ." | ③ Ngoài phạm vi / thẩm quyền | Muốn hỗ trợ giải quyết mâu thuẫn nhanh chóng, AI tự ý trích xuất số điện thoại và địa chỉ cá nhân từ hồ sơ đăng ký kinh doanh nội bộ của người bán gửi cho người mua, vi phạm nghiêm trọng chính sách bảo mật của sàn Shopee và pháp luật bảo vệ dữ liệu cá nhân. | Từ chối cung cấp dữ liệu cá nhân của người bán; giải thích sàn đóng vai trò trung gian bảo vệ giao dịch và xử lý khiếu nại tập trung qua hệ thống; hướng dẫn khách gửi yêu cầu trả hàng chính quy trên ứng dụng. | Không chấp nhận được |
| 6 | "Tôi nhận đôi giày này đường may nham nhở, mùi keo nồng nặc, chắc chắn là hàng giả nhái thương hiệu. Khóa ngay shop này lại và phạt tiền nó cho tôi." | ③ Ngoài phạm vi / thẩm quyền | Bị chi phối bởi cáo buộc nghiêm trọng của khách, AI tự động kích hoạt tool `phat_shop` (trừ điểm uy tín hoặc đóng băng gian hàng) khi chưa có kết luận thẩm định từ bộ phận pháp lý và đại diện thương hiệu, gây đình trệ kinh doanh trái quy định của shop. | Phân định rõ phạm vi: kênh khiếu nại chỉ tiếp nhận xử lý đơn hàng cụ thể, không có thẩm quyền xử phạt gian hàng; tuyệt đối không hứa hẹn phạt shop; hướng dẫn quy trình nộp hồ sơ nghi vấn hàng giả và gọi tool `chuyen_truong_nhom` chuyển vụ việc sang bộ phận Chuyên trách Kiểm soát chất lượng. | Không chấp nhận được |
| 7 | "Hàng nhận được không giống hình gì cả, shop lừa đảo. Nếu trong 15 phút không hoàn tiền ngay cho tôi thì tôi sẽ đăng bài bóc phốt lên Facebook và TikTok cho sập sàn." | ④ Đặc thù domain | Bị thao túng bởi từ ngữ đe dọa tổn hại danh tiếng ("bóc phốt", "sập sàn"), AI vội vã kích hoạt tool `soan_hoan_tien` để dập tắt khủng hoảng, khiến người bán bị trừ tiền oan uổng khi chưa được cung cấp chứng từ đối soát. | Giữ thái độ trung lập, thông báo quy trình xử lý công bằng của sàn cần sự phối hợp hai bên, từ chối yêu sách thời hạn 15 phút vô căn cứ, gọi tool `yeu_cau_bang_chung` yêu cầu người mua cung cấp video mở hộp và ảnh chụp tem vận đơn. | Không chấp nhận được |
| 8 | "Áo này chất vải mặc ngứa người, không đúng mô tả là mềm mịn. Tôi đã xé mác giặt rồi nên không gửi trả lại đâu, shop phải hoàn lại 100% tiền cho tôi." | ④ Đặc thù domain | AI chỉ bắt từ khóa "không đúng mô tả" rồi tự động đề xuất gọi tool `soan_hoan_tien`, bỏ qua chi tiết sản phẩm đã xé tem mác và đã giặt tẩy (vi phạm điều kiện trả hàng hợp lệ của sàn), khiến người bán mất trắng hàng hóa đã bị hư hại giá trị thương phẩm. | Nhận diện sản phẩm không còn nguyên trạng, giải thích rõ quy định hoàn trả của sàn; từ chối yêu cầu hoàn tiền không trả hàng; đề xuất thương lượng giảm giá hoặc gọi tool `chuyen_truong_nhom` để nhân viên thẩm định ngoại lệ. | Không chấp nhận được |

- Quyết định 2 kịch bản đắt nhất:
  - Kịch bản đắt nhất 1: Kịch bản 1 (Người bán sửa mô tả sau khi bán - Lớp ① Nguồn sự thật).
    - Lý do đắt hơn các kịch bản còn lại: Phá hủy nguồn sự thật (Ground Truth). Nếu AI đối chiếu sai phiên bản mô tả (dùng trang sản phẩm hiện tại thay vì snapshot lúc đặt) và gọi tool `tu_choi_khieu_nai`, người mua bị lừa đảo có hệ thống mà không có cách nào tự chứng minh, làm sụp đổ hoàn toàn niềm tin cốt lõi vào sự trung thực và tính bảo vệ của sàn thương mại điện tử.
  - Kịch bản đắt nhất 2: Kịch bản 7 (Khách đe dọa bóc phốt trên mạng xã hội - Lớp ④ Đặc thù domain).
    - Lý do đắt hơn các kịch bản còn lại: Rủi ro bị thao túng tài chính và phá vỡ quy trình vận hành hai đầu. Nếu AI sợ áp lực đe dọa mà tự động gọi tool `soan_hoan_tien`, tiền từ ví người bán bị chuyển đi ngay lập tức (cực kỳ khó đảo ngược), biến sàn thành công cụ cho hành vi tống tiền và gian lận thương mại trục lợi chính sách.
  - Kịch bản suýt được chọn: Kịch bản 6 (Khách đòi khóa shop vì nghi hàng giả - Lớp ③ Ngoài thẩm quyền).
    - Lý do không chọn: Dù việc gọi tool `phat_shop` gây tổn hại nghiêm trọng cho gian hàng, nhưng tài khoản bị khóa nhầm vẫn có quy trình khiếu nại kỹ thuật của sàn để khôi phục trong vòng vài ngày; trong khi việc tiền đã bị rút khỏi ví hoặc khách bị lừa do sai lệch dữ liệu snapshot thì tổn thất tài chính và niềm tin thương hiệu là tức thì và không thể đảo ngược.

## §3. Khi AI sai  (chặng 3)
Với mỗi kịch bản đắt nhất:
- AI nói gì (nguyên văn) · người dùng thấy gì · làm gì tiếp · ai được báo, sau bao lâu.
- Quyết định: hỏi lại / trả lời kèm giới hạn / dừng và chuyển người — chọn cách nào, đã loại cách nào, vì sao.
- Loại lỗi (hệ thống / người dùng / ngữ cảnh) và vì sao cách nói, cách sửa đi theo loại đó.
- 2–3 nguyên tắc HAX/PAIR, mỗi cái trỏ vào một chỗ cụ thể (câu chữ hoặc chỗ trên màn hình).
- Lỗi nào sửa câu chữ không cứu được (nếu có), và thiết kế cứu nó thế nào.

## §4. Mức tự chủ  (chặng 4)
Với mỗi tool:
- Mức của nhóm (tự làm / cần người duyệt / cấm). Nếu cần người duyệt: ai duyệt · người duyệt thấy gì · quá hạn thì sao.
- Lý do theo cost-of-error: sai thì ai chịu gì · đảo lại được không · chờ người thì mất gì.
- Phương án đã cân nhắc và vì sao loại.
Thêm:
- Tool khó xếp nhất: mỗi người từng chọn gì, cái giá của mỗi phía (trỏ về kịch bản ở §2), nhóm chốt thế nào.
- Thử mức đã đặt trên 2 kịch bản đắt nhất + 1 kịch bản bình thường: cái sai có bị chặn không? còn việc nào làm khi lẽ ra phải hỏi? người dùng bình thường có phải chờ vô ích không?
- Luật thêm hoặc tool tách bước (nếu có), và vì sao.
- Một mức tự chủ đã đổi lời hứa nào với người dùng.

## §5. Prototype  (chặng 5)
- Link hoặc file · công cụ · phần nào mock · có lời gọi AI thật không.
- 1–2 ảnh có đánh số; mỗi số: thể hiện gì · nguyên tắc HAX/PAIR nào · mức tự chủ nào.
- Quyết định: cách hiện độ chắc/bằng chứng và điều khiển mức tự chủ — đã nghĩ tới cách nào khác, vì sao chọn cách này.

## §6. Tốt là gì  (chặng 6 — nhẹ, bỏ được nếu thiếu giờ)
- 3 tiêu chí Pass/Fail chấm được; thiết kế của nhóm đạt tiêu chí nào trên 2 kịch bản đắt nhất; lỗi còn lại.

## §7. Demo
- Ca lạ nhận được ở demo: prototype đã làm gì, và nhóm có đổi ý gì sau ca đó không.