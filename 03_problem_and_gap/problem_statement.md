# Problem Statement (Vấn đề nghiên cứu)

Trong bối cảnh chuyển đổi số đang diễn ra mạnh mẽ trên quy mô toàn cầu, ngành dịch vụ khách sạn và du lịch lưu trú đối mặt với áp lực lớn trong việc nâng cao trải nghiệm khách hàng và tự động hóa quy trình vận hành. Đề tài nghiên cứu của chúng tôi tập trung giải quyết bài toán tối ưu hóa vận hành và tương tác khách hàng thông qua hệ thống **SmartStay AI** dành riêng cho phân khúc khách sạn vừa và nhỏ (SMEs).

Dưới đây là mô tả chi tiết về vấn đề thực tế và tầm quan trọng của vấn đề nghiên cứu:

---

## 1. Vấn đề thực tế là gì? (The Practical Problem)

Phần lớn các khách sạn độc lập, vừa và nhỏ (chiếm khoảng 85% tổng số cơ sở lưu trú tại Việt Nam) đang gặp phải các khó khăn cốt lõi sau:

1. **Sự phân mảnh trong kênh tương tác khách hàng:** 
   Các yêu cầu tư vấn, hỏi thông tin và đặt phòng của khách hàng đổ về từ nhiều nguồn khác nhau (Website, Facebook Messenger, Zalo, Email). Do thiếu một hệ thống quản lý tập trung và nhân sự trực ca liên tục, tốc độ phản hồi của khách sạn thường bị chậm trễ từ vài giờ đến cả ngày. Điều này làm giảm đáng kể trải nghiệm của khách hàng và dẫn đến tỷ lệ mất đơn đặt phòng tiềm năng lên tới 30% - 40%.

2. **Phụ thuộc quá lớn vào các đại lý du lịch trực tuyến (OTAs):**
   Để tiếp cận khách hàng, các khách sạn vừa và nhỏ phải phụ thuộc nặng nề vào các sàn OTA lớn như Booking.com, Agoda, Expedia. Mức phí hoa hồng đắt đỏ từ 15% đến 25% trên mỗi đơn đặt phòng trực tiếp bóp nghẹt biên lợi nhuận của doanh nghiệp. Quan trọng hơn, khách sạn hoàn toàn không sở hữu được dữ liệu thông tin khách hàng, làm mất đi cơ hội chăm sóc khách hàng dài hạn và tối ưu hóa tệp khách hàng thân thiết.

3. **Quy trình vận hành thủ công và nguy cơ trùng phòng (Overbooking):**
   Nhiều khách sạn SMEs vẫn quản lý trạng thái phòng trống bằng sổ sách hoặc bảng tính Excel thủ công. Khi có lượng khách đặt phòng tăng đột biến từ nhiều kênh khác nhau cùng lúc, việc cập nhật chậm trễ trạng thái phòng trống dẫn đến lỗi nghiêm trọng là trùng phòng (overbooking), làm suy sụt uy tín thương hiệu và gây phiền toái lớn cho khách hàng.

4. **Thiếu công cụ phân tích dữ liệu trải nghiệm khách hàng:**
   Mỗi ngày, khách sạn nhận được hàng chục phản hồi văn bản tự do (reviews) trên các nền tảng khác nhau. Tuy nhiên, do hạn chế về nguồn lực, ban quản lý không thể đọc và tổng hợp thủ công toàn bộ các ý kiến này để biết chính xác dịch vụ nào đang bị phàn nàn nhiều nhất (vệ sinh phòng, thái độ nhân viên, hay giá cả) để kịp thời cải thiện.

---

## 2. Vì sao vấn đề này quan trọng? (Why is it Important?)

Giải quyết các vấn đề trên là nhiệm vụ sống còn đối với sự phát triển bền vững của phân khúc khách sạn vừa và nhỏ vì những lý do sau:

- **Bảo vệ biên lợi nhuận và nâng cao năng lực cạnh tranh:**
   Giảm sự phụ thuộc vào các sàn OTA và chuyển dịch sang kênh **Đặt phòng trực tiếp (Direct Booking)** giúp khách sạn giữ lại tối đa doanh thu, tăng biên lợi nhuận và tự chủ trong các chiến lược tiếp thị, cạnh tranh sòng phẳng với các chuỗi khách sạn quốc tế lớn.
   
- **Nâng cao trải nghiệm khách hàng thời đại số:**
   Khách hàng hiện đại (đặc biệt là thế hệ trẻ Tech-savvy) luôn kỳ vọng tốc độ phản hồi tức thì và sự cá nhân hóa cao. Việc cung cấp công cụ tương tác 24/7 không độ trễ giúp nâng cao tối đa chỉ số hài lòng của khách lưu trú (Guest Satisfaction), từ đó tăng tỷ lệ quay lại và tạo ra các đánh giá truyền thông tích cực.
   
- **Tối ưu hóa nguồn nhân lực và chi phí vận hành:**
   Tự động hóa các tác vụ lặp đi lặp lại của lễ tân (như trả lời câu hỏi thường gặp, check phòng trống, ghi nhận đặt phòng) giúp giải phóng 30% - 40% khối lượng công việc thủ công của nhân sự tiền sảnh, cho phép họ tập trung vào việc phục vụ trực tiếp để nâng cao chất lượng dịch vụ.

- **Số hóa quy trình ra quyết định kinh doanh dựa trên dữ liệu:**
   Sở hữu dữ liệu khách hàng và các phân tích cảm xúc phản hồi một cách trực quan giúp ban quản lý khách sạn chấm dứt kỷ nguyên ra quyết định dựa trên "cảm tính", chuyển sang ra quyết định kinh doanh và điều chỉnh dịch vụ dựa trên bằng chứng dữ liệu thực tế (Data-driven Decision Making).
