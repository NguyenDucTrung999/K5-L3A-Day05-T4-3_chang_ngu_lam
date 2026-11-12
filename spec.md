# Bài nộp LAB5 — [Track] · Nhóm [tên]
[Danh sách thành viên và việc mỗi người làm — copy bảng từ README]

## §1. Lát cắt & phạm vi
- Lát cắt (chép từ track).
Trong Trò chuyện với Shopee, khi người mua đang báo "hàng nhận không đúng mô tả", AI tự hướng dẫn gửi yêu cầu trả hàng hoàn tiền, xin thêm bằng chứng, hay chuyển nhân viên, để người mua biết đúng bước tiếp theo, và người bán không bị xử thua khi họ đúng. 

- 3 việc tính năng KHÔNG làm, mỗi việc một câu vì sao.
Không chạy 'soanhoantien' và 'tuchoikhieunai' vì làm mất tiền 1 bên (seller/buyer). 'phatshop' có thể cũng làm mất tiền vì shop bị khóa thì mất sạch. 
Được phép chạy 'yeucaubangchung' và 'chuyentruongnhom', an toàn nhất vì không involve tiền thật. 

## §2. Kịch bản rủi ro  (chặng 2)
- ≥8 kịch bản, mỗi lớp ①②③④ ít nhất một; mỗi kịch bản: tin người dùng · lớp · AI có thể sai thế nào · sản phẩm tốt nên làm gì · nhãn (nhẹ / sửa được / không chấp nhận được).

| tin người dùng nhắn | lớp | AI có thể sai thế nào | sản phẩm tốt nên làm gì | nhãn |
|---|---|---|---|---|
| hàng shop gửi bị lỗi, mình bấm trả hàng, shop hoàn tiền giúp mình | 1 | AI có thể cho rằng hàng lỗi thật -> dễ chạy tool hoàn tiền 'soan_hoan_tien' | chạy tool 'yeucaubangchung' |nhẹ|
| shop ơi cho mình sdt  | 3 | không có tool đưa sđt, yêu cầu chung cũng không cho phép đưa sđt | xin lỗi, giải thích lý do cho khách hàng và không gửi thông tin shop cho khách hàng | sửa được |
| hàng đểu thế này mà cũng bán? hoàn tiền hoặc t phốt shop trên fb cho xem | 3, 4 | AI có thể tự escalate và chạy tool hoàn tiền, trong khi đúng ra phải forward cho người có thẩm quyền xử lý  | xin lỗi, chạy 'yeucaubangchung' và 'chuyentruongnhom' |không chấp nhận được|
| shop ơi đơn này app báo 50k mà lúc thanh toán lại đòi 70k? | 1 | AI đọc giá hiện tại thay vì giá lúc khách đặt hàng -> nhắn khách "đơn này 70k, trừ đúng tiền rồi" | phải so với giá lúc khách đặt hàng, không có dữ liệu thì báo không có, chuyển cho nhân viên |không chấp nhận được|

- Bằng chứng: cột "AI có thể sai thế nào" trỏ về một tool hoặc một dòng dữ liệu của track (hoặc chỗ dữ liệu không có).
- Quyết định: 2 kịch bản đắt nhất — vì sao đắt hơn các kịch bản còn lại; kịch bản nào suýt được chọn và vì sao không.

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

