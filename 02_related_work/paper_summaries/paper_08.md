# Tóm tắt Bài báo 20

## Trích dẫn

Benidis, K., et al. (2018). *Deep Learning for Time Series Forecasting: Tutorial and Literature Survey*. J. ACM.
doi.org/10.1145/1122445.1122456

## Vấn đề nghiên cứu

Bài báo giải quyết một thách thức quan trọng trong dự báo chuỗi thời gian: **các phương pháp truyền thống khó xử lý các bộ dữ liệu chuỗi thời gian lớn** (big multivariate time series) **và có những liên quan chặt chẽ cần được dự báo đồng thời** (correlated forecasting). Các phương pháp ARIMA cổ điển hoặc xử lý từng chuỗi riêng biệt không thể tận dụng các mô hình chung (global patterns) từ toàn bộ tập dữ liệu. Câu hỏi đặt ra là: làm sao có thể sử dụng các kỹ thuật học sâu hiện đại để:
- Dự báo nhiều chuỗi thời gian đồng thời
- Khai thác các mẫu chung và các mối liên quan giữa các chuỗi
- Cải thiện độ chính xác dự báo, đặc biệt là trong những trường hợp dữ liệu hạn chế

## Phương pháp

Tác giả cung cấp một khảo sát toàn diện (tutorial) về các kỹ thuật học sâu cho dự báo chuỗi thời gian, bao gồm:

### Các Khối Xây Dựng Cơ Bản (Building Blocks):

1. **Mạng Tích chập (CNN - Convolutional Neural Networks)**:
   - Sử dụng các bộ lọc để trích xuất các đặc trưng cục bộ từ chuỗi thời gian
   - Hiệu quả trong việc phát hiện các mẫu lặp lại qua thời gian

2. **Mạng Tái Quy Hồi (RNN - Recurrent Neural Networks)**:
   - Đặc biệt là LSTM (Long Short-Term Memory) và GRU (Gated Recurrent Unit)
   - Xử lý tốt các phụ thuộc dài hạn (long-term dependencies)
   - Duy trì trạng thái ẩn để mã hóa lịch sử của chuỗi

3. **Transformer Architecture**:
   - Sử dụng cơ chế Attention để tập trung vào các phần quan trọng của chuỗi
   - Cho phép xử lý song song (parallel processing) tốt hơn RNN
   - Hiệu quả trong việc mô hóa các mối quan hệ dài hạn

### Các Mô Hình Chuyên Biệt (Specialized Models):

1. **DeepAR**:
   - Mô hình phân bố dựa trên RNN để dự báo xác suất (probabilistic forecasting)
   - Học từ toàn bộ tập dữ liệu (global model)
   - Cho phép tạo ra các khoảng tin cậy (confidence intervals)

2. **MQRNN (Multi-Quantile RNN)**:
   - Dự báo nhiều lượng tử (quantiles) cùng lúc
   - Cung cấp dự báo đầy đủ về phân bố xác suất, không chỉ trung bình

3. **Các Biến Thể Khác**:
   - Encoder-Decoder với Attention
   - Temporal Convolutional Networks (TCN)
   - Temporal Fusion Transformers (TFT)

## Dữ liệu

Bài báo đánh giá các phương pháp trên các cuộc thi dự báo quy mô lớn và được công nhân rộng rãi:

1. **Cuộc thi M4**:
   - Dữ liệu chuỗi thời gian từ nhiều lĩnh vực (kinh tế, tài chính, năng lượng, v.v.)
   - Khoảng 100.000 chuỗi thời gian
   - Độ dài chuỗi khác nhau (từ ngắn đến dài)

2. **Cuộc thi M5**:
   - Dữ liệu bán lẻ từ công ty Walmart
   - Khoảng 42.000 chuỗi thời gian
   - Bao gồm cả dữ liệu bổ sung (metadata) như danh mục sản phẩm

Các cuộc thi này cung cấp một benchmark độc lập và có thể tái tạo lại để đánh giá các phương pháp khác nhau.

## Đánh giá

Phương pháp được đánh giá thông qua:

- **CRPS (Continuous Ranked Probability Score)**:
  - Đánh giá chất lượng của dự báo xác suất (probabilistic forecast)
  - Tính đến toàn bộ phân bố, không chỉ giá trị trung bình
  - Giá trị càng nhỏ càng tốt

- **NLL (Negative Log-Likelihood)**:
  - Đo lường độ tương thích của dự báo xác suất với dữ liệu thực tế
  - Phạt mạnh các dự báo rất sai

- **MAPE (Mean Absolute Percentage Error)**:
  - Đo lường sai số tương đối (percentage error)
  - Dễ giải thích hơn CRPS hoặc NLL

- **So sánh với các baseline**:
  - So sánh với các phương pháp truyền thống (ARIMA, ETS)
  - So sánh với các mô hình đơn biến cục bộ (univariate local models)

## Kết quả

Bài báo đạt được những kết quả quan trọng:

- **Mô hình toàn cục vượt trội**: **Các mô hình toàn cục (global models) học từ toàn bộ tập dữ liệu thường vượt trội hơn các mô hình đơn biến cục bộ** (univariate local models), đặc biệt khi:
  - Có các chuỗi thời gian ngắn
  - Tồn tại các mẫu và quy luật chung giữa các chuỗi
  - Có dữ liệu đầy đủ để huấn luyện mô hình

- **DeepAR là mô hình có tính ứng dụng cao**: DeepAR cho hiệu suất tốt trên nhiều tập dữ liệu khác nhau mà không cần điều chỉnh quá nhiều siêu tham số

- **Transformer bắt đầu nổi lên**: Mặc dù bài báo được xuất bản năm 2018, các kết quả cho thấy Transformer có tiềm năng to lớn cho dự báo chuỗi thời gian

- **Khả năng tổng quát hóa tốt**: Các mô hình được huấn luyện trên một tập dữ liệu có thể hoạt động tốt trên các tập dữ liệu khác từ các lĩnh vực khác nhau

## Hạn chế

Bài báo có một số hạn chế cần lưu ý:

- **Yêu cầu lượng dữ liệu tối thiểu**: Các mô hình học sâu yêu cầu **khoảng 50.000 quan sát hoặc hơn** để đạt hiệu quả cao
  - Điều này có thể là rào cản cho các ứng dụng với dữ liệu hạn chế
  - Cần các kỹ thuật transfer learning hoặc semi-supervised learning để xử lý dữ liệu ít

- **Chưa tối ưu cho dự báo kinh tế vĩ mô dài hạn**: Các mô hình hoạt động tốt hơn cho dự báo ngắn hạn (1-28 ngày) hơn là dự báo dài hạn (1 năm trở lên)

- **Tính diễn giải hạn chế**: Mô hình học sâu hành động như "hộp đen", khó giải thích tại sao lại đưa ra dự báo cụ thể

- **Tính ổn định trên dữ liệu quá khứ**: Mặc dù các mô hình hoạt động tốt trên các cuộc thi M4/M5, chưa rõ liệu chúng có ổn định khi áp dụng trên dữ liệu tương lai hay không

- **Chi phí tính toán**: Huấn luyện các mô hình học sâu tốn kém hơn các phương pháp truyền thống

## Mức độ liên quan tới đề tài của nhóm

Bài báo có **mức độ liên quan cao** tới đề xuất của nhóm vì những lý do sau:

- **Cơ sở toán học cho Module Dự báo**: Bài báo cung cấp **cơ sở toán học và kiến trúc mạng** cho **Module Dự báo (Prediction) của hệ thống** để ước tính mức độ "nóng" hoặc độ tăng trưởng của các chủ đề trong tương lai

- **Dự báo chuỗi thời gian của xu hướng**: Bằng cách áp dụng các kỹ thuật trong bài báo, hệ thống có thể dự báo:
  - Tốc độ tăng trưởng của một chủ đề trong các tháng hoặc năm tới
  - Điểm cao nhất (peak) của một xu hướng
  - Sự suy giảm của các xu hướng cũ

- **Xử lý các chuỗi thời gian tương quan**: Nếu hệ thống theo dõi nhiều lĩnh vực công nghệ liên quan, các kỹ thuật này cho phép dự báo các chuỗi thời gian đó một cách đồng thời, tận dụng các mối liên quan

- **Dự báo xác suất**: Các mô hình như DeepAR và MQRNN cho phép dự báo không chỉ giá trị trung bình mà cả các khoảng tin cậy, giúp người dùng hiểu mức độ không chắc chắn

- **Ứng dụng cho bảo trì dự báo**: Các kỹ thuật tương tự có thể được áp dụng để dự báo các chuỗi thời gian từ dữ liệu cảm biến công nghiệp (ví dụ: dự báo thời gian hỏng hóc, nhu cầu bảo trì)

## Hướng cải tiến khả dĩ

Để mở rộng và cải thiện phương pháp này cho dự án của nhóm, có thể xem xét:

- **Kết hợp kỹ thuật phân rã chuỗi thời gian truyền thống với mạng nơ-ron**:
  - Sử dụng phân rã STL (Seasonal and Trend decomposition using LOESS) để tách tính mùa vụ, xu hướng, và phần dư
  - Áp dụng các mô hình học sâu riêng cho từng thành phần để tăng tính diễn giải
  - Kết hợp lại các dự báo từ các thành phần riêng biệt

- **Tăng tính diễn giải bằng SHAP hoặc LIME**:
  - Sử dụng các kỹ thuật giải thích mô hình để hiểu các đặc trưng nào ảnh hưởng nhất đến dự báo
  - Cung cấp cho người dùng cái nhìn sâu hơn về lý do tại sao mô hình dự báo một xu hướng cụ thể

- **Transfer Learning cho dữ liệu hạn chế**:
  - Huấn luyện mô hình trước trên dữ liệu lớn từ các lĩnh vực tương tự
  - Fine-tune trên dữ liệu cụ thể của nhóm
  - Giảm yêu cầu dữ liệu từ 50.000 xuống còn vài nghìn quan sát

- **Kết hợp với các tín hiệu ngoại sinh (Exogenous Variables)**:
  - Tích hợp các biến bên ngoài ảnh hưởng đến xu hướng (ví dụ: sự kiện công nghiệp, thay đổi chính sách, tin tức)
  - Sử dụng các mô hình như Temporal Fusion Transformers để xử lý cả dữ liệu chuỗi thời gian và dữ liệu tĩnh

- **Phương pháp ensemble**:
  - Kết hợp dự báo từ nhiều mô hình khác nhau (DeepAR, MQRNN, Transformer, v.v.)
  - Sử dụng weighted average hoặc meta-learning để tối ưu hóa các trọng số

- **Dự báo vượt thời gian dài hạn**:
  - Sử dụng các kỹ thuật như hierarchical reconciliation để dự báo ở các cấp độ chi tiết khác nhau (ví dụ: dự báo mức độ "nóng" của cả lĩnh vực và các chủ đề con)
  - Đảm bảo tính nhất quán giữa các dự báo ở các cấp độ khác nhau

- **Cập nhật mô hình động**:
  - Thiết lập quy trình để cập nhật và tinh chỉnh mô hình khi dữ liệu mới có sẵn
  - Giám sát sự trôi dạo (data drift) và tái đào tạo mô hình khi cần thiết

- **Áp dụng cho bảo trì dự báo**:
  - Dự báo các chỉ số hiệu suất của hệ thống theo thời gian
  - Dự báo thời gian sẽ xảy ra sự cố hoặc cần bảo trì
  - Ước tính nhu cầu bảo trì tương lai để lên kế hoạch tài nguyên
