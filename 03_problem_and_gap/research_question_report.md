# Research Question Report

## Bối cảnh hình thành câu hỏi nghiên cứu

Theo [đề cương đề tài](/D:/Study/FPTU/WDP301/projects/NCKH-WDP/01_topic_proposal/topic_proposal_vn.md), nhóm đang hướng tới việc xây dựng một nền tảng proof-of-concept cho giám sát và bảo trì hạ tầng trong môi trường trung tâm dữ liệu mô phỏng, trong đó `AR` đóng vai trò là lớp tương tác chính còn `AI` được sử dụng như lớp phân tích hỗ trợ. Điểm nhấn của đề tài không nằm ở việc tái tạo một hệ thống trung tâm dữ liệu doanh nghiệp hoàn chỉnh, mà ở việc kiểm chứng xem liệu dữ liệu telemetry thời gian thực, khi được kết hợp với giao diện AR và mô hình AI phù hợp, có thể tạo ra một quy trình vận hành trực quan và hữu ích hơn hay không.

Từ định hướng đó, phần câu hỏi nghiên cứu đặt ra hai vấn đề nghiên cứu cần được xác định rõ: (i) vai trò cụ thể của AI trong hệ thống là gì (phát hiện bất thường, dự báo xu hướng, hay hỗ trợ quyết định bảo trì), và (ii) ranh giới phạm vi nào là khả thi trong bối cảnh một hệ thống mô phỏng ở quy mô học thuật để có thể triển khai và đánh giá thực nghiệm.

## Nhận xét về hướng nghiên cứu hiện tại

Sau khi đối chiếu proposal với nhóm 12 bài báo đã rà soát, tổng hợp cho thấy hướng tiếp cận AR + AI theo framing “AR-first, AI-as-augmentation” có cơ sở trong literature, nhưng phần AI cần được mô tả với phạm vi rõ ràng để tránh mở rộng mục tiêu vượt quá năng lực đánh giá thực nghiệm. Các tài liệu liên quan hiện nay cho thấy ba xu hướng chính.

Thứ nhất, ở nhóm nghiên cứu về `AR-assisted maintenance`, các công trình như Nagy et al. (2024), Xu et al. (2023), Wang et al. (2022) và Zhao et al. (2025) đều cho thấy AR đặc biệt hữu ích khi cần gắn dữ liệu vận hành với bối cảnh không gian và quy trình thao tác tại chỗ. Tuy nhiên, phần lớn các bài này tập trung vào cách trình bày hướng dẫn, trải nghiệm người dùng, hoặc khả năng hỗ trợ thao tác, thay vì đi sâu vào xây dựng một mô hình phân tích telemetry phức tạp.

Thứ hai, ở nhóm nghiên cứu về `data-center anomaly detection`, các công trình của Decker et al. (2020), Viola et al. (2022) và Vajda et al. (2024) nhấn mạnh rằng bài toán trung tâm không chỉ là hiển thị trạng thái hệ thống mà là nhận diện bất thường từ log, monitoring data và telemetry trong điều kiện thời gian thực. Nhóm bài này gần với phần backend của đề tài hơn cả, vì chúng trực tiếp xử lý dữ liệu hạ tầng và quan tâm đến các yếu tố thực tế như độ trễ phát hiện, tính thích nghi và khả năng kết hợp nhiều nguồn tín hiệu.

Thứ ba, ở nhóm bài phương pháp luận, các mô hình như `Isolation Forest`, `LSTM Autoencoder`, `Anomaly Transformer` và `Temporal Fusion Transformer` cung cấp nền tảng để lựa chọn mô hình AI phù hợp cho proof-of-concept. Trong đó, `Isolation Forest` thích hợp cho một baseline gọn nhẹ; `LSTM Autoencoder` phù hợp nếu muốn khai thác đặc trưng chuỗi thời gian; `Anomaly Transformer` và `TFT` có giá trị nghiên cứu cao hơn nhưng đòi hỏi chi phí triển khai và đánh giá lớn hơn.

Từ ba nhóm bằng chứng trên, có thể rút ra một nhận xét quan trọng: đối với đề tài của nhóm, phần được hậu thuẫn tốt nhất từ literature không phải là một tuyên bố rộng về "predictive maintenance", mà là khả năng phát hiện và cảnh báo sớm các trạng thái bất thường trên hạ tầng mô phỏng, sau đó chuyển các tín hiệu đó thành thông tin có ngữ cảnh trên dashboard và giao diện AR.

## Câu hỏi nghiên cứu được đề xuất

Dựa trên bối cảnh đề tài và mức độ hỗ trợ của các tài liệu liên quan, câu hỏi nghiên cứu chính được đặc tả như sau:

**RQ1: Các mô hình AI có thể phát hiện và cảnh báo sớm đến mức nào các trạng thái hạ tầng bất thường dựa trên dữ liệu telemetry thời gian thực và các mẫu hành vi vận hành của hệ thống trong môi trường trung tâm dữ liệu mô phỏng?**

Nếu cần trình bày bản tiếng Anh trong proposal hoặc slide:

**RQ1: To what extent can AI models detect and provide early warning of abnormal infrastructure states based on real-time telemetry and operational behavior patterns in a simulated data center environment?**

Cách phát biểu này giữ trọng tâm vào năng lực phát hiện/cảnh báo bất thường từ telemetry (phần được hậu thuẫn trực tiếp từ literature), đồng thời tránh kéo mục tiêu sang “predictive maintenance” theo nghĩa đầy đủ (vốn thường đòi hỏi nhãn dữ liệu hỏng hóc, horizon dự báo, và quy trình đánh giá phức tạp hơn).

## Cơ sở lập luận cho RQ1

Lập luận thứ nhất xuất phát từ cấu trúc hệ thống được nêu trong proposal: telemetry được thu thập liên tục từ các node và dịch vụ container hóa; AI đóng vai trò lớp phân tích bổ sung; AR trình bày trạng thái/cảnh báo/hướng dẫn theo ngữ cảnh. Theo cấu trúc này, câu hỏi về “phát hiện và cảnh báo sớm bất thường” là điểm nối trực tiếp giữa dữ liệu vận hành và lớp tương tác hỗ trợ người dùng.

Lập luận thứ hai dựa trên bằng chứng nghiên cứu hiện có: các bài của Decker et al. (2020), Viola et al. (2022) và Vajda et al. (2024) cho thấy telemetry/log/monitoring data có thể được xử lý để nhận diện bất thường hoặc mẫu vận hành đáng chú ý theo thời gian thực; trong khi đó, các bài như Xu et al. (2023) và Wang et al. (2022) cho thấy đầu ra phân tích có thể được chuyển hoá thành hỗ trợ thao tác/bảo trì ở lớp AR. Do đó, RQ1 được đặt ở giao điểm giữa hai nhánh (telemetry analytics và AR-assisted maintenance) mà đề tài đang kết hợp.

Lập luận thứ ba liên quan đến tính khả thi của đánh giá thực nghiệm trong môi trường mô phỏng: các kịch bản bất thường có thể được thiết kế có chủ đích (tăng tải bất thường, vòng lặp restart container, suy giảm tài nguyên theo thời gian, hoặc mất cân bằng giữa các chỉ số), từ đó tạo ground truth ở mức sự kiện để đánh giá. Ngược lại, nếu mục tiêu được mở rộng ngay sang “dự báo rủi ro bảo trì” theo nghĩa rộng, nghiên cứu sẽ phải định nghĩa thêm khái niệm rủi ro, horizon dự báo, và thước đo gắn với ý nghĩa vận hành.

## Phạm vi khái niệm cần làm rõ

Để câu hỏi nghiên cứu không trở nên mơ hồ, hai khái niệm trong RQ1 cần được hiểu rõ.

Thứ nhất là `trạng thái hạ tầng bất thường`. Trong phạm vi đề tài, điều này không nhất thiết chỉ là một lỗi phần cứng hay sự cố nghiêm trọng, mà có thể bao gồm các điều kiện vận hành lệch khỏi mẫu bình thường đã được xác lập trong môi trường mô phỏng. Ví dụ, CPU tăng cao kéo dài không tương xứng với workload, bộ nhớ suy giảm bất thường, số lần restart container tăng liên tục, hoặc trạng thái dịch vụ không ổn định trong khi các chỉ số khác vẫn dao động.

Thứ hai là `mẫu hành vi vận hành`. Trong báo cáo này, khái niệm này được operationalize như các dạng biến thiên có ý nghĩa của telemetry theo thời gian (xu hướng, dao động, chu kỳ, mối tương quan giữa các chỉ số), thay vì chỉ xét các điểm dữ liệu rời rạc tại từng thời điểm.

Việc làm rõ hai khái niệm này rất quan trọng, vì nó ảnh hưởng trực tiếp đến cách nhóm trích đặc trưng, gán nhãn dữ liệu mô phỏng và lựa chọn mô hình AI.

## Các câu hỏi phụ nên đi kèm

Để RQ1 có thể triển khai thành một kế hoạch thực nghiệm mạch lạc, nên tách thêm một số câu hỏi phụ:

**RQ1a.** Những đặc trưng telemetry và mẫu hành vi vận hành nào đóng góp nhiều nhất vào việc phát hiện trạng thái bất thường?

**RQ1b.** Trong các mô hình được xem xét, mô hình nào cho sự cân bằng tốt nhất giữa độ chính xác phát hiện, tỷ lệ cảnh báo sai và thời gian cảnh báo?

**RQ1c.** Kết quả phát hiện bất thường có thể được chuyển hóa như thế nào thành thông tin vận hành có ngữ cảnh để hiển thị hiệu quả trên dashboard và giao diện AR?

Ba câu hỏi phụ này giúp liên kết phần AI với phần hệ thống tổng thể của đề tài. Nếu chỉ dừng ở việc so sánh mô hình theo độ chính xác, nghiên cứu sẽ dễ nghiêng về một bài toán machine learning thuần túy, trong khi giá trị thực sự của đề tài nằm ở chỗ đầu ra phân tích phải phục vụ được quy trình giám sát và bảo trì.

## Định hướng phương pháp nghiên cứu

Xét về bản chất, đây là một nghiên cứu thực nghiệm theo hướng thiết kế và đánh giá hệ thống. Dữ liệu không đến từ một trung tâm dữ liệu thật mà được sinh ra từ môi trường mô phỏng có kiểm soát, do đó nghiên cứu có điều kiện chủ động hơn trong việc xây dựng kịch bản và quan sát hành vi hệ thống.

Một hướng triển khai hợp lý là tổ chức nghiên cứu theo ba lớp. Lớp thứ nhất là lớp sinh dữ liệu, nơi các node, dịch vụ và container trong môi trường Docker tạo ra telemetry như CPU, bộ nhớ, mạng, lưu trữ, trạng thái dịch vụ và log liên quan. Lớp thứ hai là lớp phân tích, nơi các mô hình AI được áp dụng để phát hiện bất thường hoặc sinh ra điểm cảnh báo. Lớp thứ ba là lớp trình bày, nơi dashboard và AR sử dụng các kết quả này để hỗ trợ người vận hành theo hai chế độ khác nhau: giám sát tập trung và kiểm tra tại chỗ.

Với cấu trúc đó, thiết kế thực nghiệm có thể được tổ chức theo hướng tăng dần độ phức tạp: (i) một baseline đơn giản, (ii) một mô hình khai thác tính chuỗi thời gian, và (iii) một mô hình nâng cao (nếu nguồn lực cho phép) để đối chiếu.

## Thiết kế mô hình và thực nghiệm (dạng đề xuất nghiên cứu)

Từ proposal và literature hiện tại, một cấu hình nghiên cứu khả dĩ có thể được mô tả như sau.

Ở mức cơ sở, baseline dựa trên ngưỡng hoặc luật đơn giản có thể đóng vai trò mốc tham chiếu. Lý do là trong nhiều hệ thống giám sát thực tế, cảnh báo thường khởi đầu từ logic đơn giản; đồng thời, so sánh với baseline là điều kiện cần để diễn giải giá trị gia tăng của mô hình AI.

Ở lớp học máy không giám sát, `Isolation Forest` là một lựa chọn baseline phù hợp vì nhẹ và có thể áp dụng cho telemetry đa biến ở quy mô proof-of-concept. Nếu mục tiêu là nắm bắt động học theo thời gian rõ hơn, `LSTM Autoencoder` là một cấu hình khả thi do có thể học mẫu bình thường từ chuỗi dữ liệu và phát hiện sai lệch thông qua lỗi tái tạo.

Các mô hình nâng cao hơn như `Anomaly Transformer` hoặc `TFT` có thể được xem như nhánh mở rộng để tăng chiều sâu nghiên cứu. Trong khuôn khổ PoC học thuật, chúng có thể được đặt ở trạng thái optional extension vì chi phí huấn luyện, tinh chỉnh và diễn giải kết quả có thể vượt quá phạm vi đánh giá.

Về kịch bản thực nghiệm, môi trường mô phỏng có thể bao gồm cả trạng thái bình thường lẫn những bất thường được thiết kế có chủ đích (pha tải ổn định, tải tăng đột biến nhưng hợp lệ, suy giảm tài nguyên kéo dài, lỗi restart lặp lại, hoặc sai lệch giữa các chỉ số). Các kịch bản này quyết định độ đa dạng của hành vi hệ thống và giá trị diễn giải của bộ dữ liệu thực nghiệm.

## Thước đo đánh giá

Với RQ1, đánh giá mô hình không chỉ dừng ở độ chính xác tổng quát. Vì mục tiêu là hỗ trợ vận hành, các chỉ số đánh giá cần phản ánh cả chất lượng phát hiện lẫn giá trị sử dụng theo ngữ cảnh thời gian thực.

Các chỉ số như `Precision`, `Recall`, `F1-score` và `MCC` vẫn cần thiết để đánh giá năng lực phân loại hoặc phát hiện bất thường. Tuy nhiên, đối với đề tài này, `detection delay` cũng rất quan trọng vì một cảnh báo đến muộn sẽ ít ý nghĩa hơn trong quy trình kiểm tra bằng AR. Ngoài ra, tỷ lệ cảnh báo sai cũng cần được quan tâm, bởi nếu hệ thống liên tục cảnh báo sai, người dùng sẽ nhanh chóng mất niềm tin vào lớp phân tích AI.

Nếu nhóm xây dựng được nhãn ở mức sự kiện thay vì chỉ ở từng điểm dữ liệu, việc đánh giá ở mức sự kiện sẽ có giá trị hơn cho phần báo cáo học thuật. Điều này đặc biệt phù hợp với các bất thường kéo dài theo một khoảng thời gian nhất định, thay vì chỉ xuất hiện chớp nhoáng ở một timestamp đơn lẻ.

## Khoảng trống nghiên cứu mà đề tài có thể khai thác

Từ phần tổng hợp tài liệu hiện có, có thể thấy chưa nhiều công trình kết nối đầy đủ bốn yếu tố trong cùng một hệ thống: telemetry hạ tầng thời gian thực, phát hiện bất thường bằng AI, giao diện AR gắn theo không gian và quy trình bảo trì trong một môi trường mô phỏng có thể kiểm soát.

Các nghiên cứu về AR thường mạnh ở khía cạnh tương tác và hỗ trợ thao tác. Các nghiên cứu về anomaly detection lại mạnh ở xử lý telemetry, log hoặc chuỗi thời gian. Điều đề tài của nhóm có thể đóng góp là đưa hai nhánh này gặp nhau trong một proof-of-concept có cấu trúc rõ ràng: dữ liệu hạ tầng được sinh ra có chủ đích, bất thường được phát hiện bằng AI, sau đó kết quả được trực quan hóa không chỉ trên dashboard mà còn ngay trên node hoặc rack mô phỏng thông qua AR.

Nói cách khác, điểm mới của đề tài không nhất thiết nằm ở việc sáng tạo ra một thuật toán phát hiện bất thường hoàn toàn mới, mà nằm ở cách tổ chức một quy trình vận hành có ngữ cảnh hơn, trong đó đầu ra của AI thực sự trở thành thành phần có ích cho người vận hành.

## Kết luận

Từ proposal và bối cảnh related work hiện tại, báo cáo này định vị câu hỏi nghiên cứu trung tâm theo hướng có thể kiểm chứng thực nghiệm trong môi trường mô phỏng: phát hiện và cảnh báo sớm bất thường từ telemetry, sau đó chuyển hoá đầu ra phân tích thành thông tin có ngữ cảnh trên dashboard và giao diện AR. So với diễn đạt “predictive maintenance” theo nghĩa rộng, đặc tả này tránh yêu cầu dữ liệu/horizon/tiêu chí đánh giá phức tạp ngay từ giai đoạn PoC.

Theo đó, RQ1 được phát biểu như sau:

**Các mô hình AI có thể phát hiện và cảnh báo sớm đến mức nào các trạng thái hạ tầng bất thường dựa trên dữ liệu telemetry thời gian thực và các mẫu hành vi vận hành của hệ thống trong môi trường trung tâm dữ liệu mô phỏng?**

Phát biểu này bám sát kiến trúc đề tài, có cơ sở từ literature đã tổng hợp, và hỗ trợ thiết kế một kế hoạch thực nghiệm rõ ràng. Các mục tiêu như dự báo hoặc ước lượng rủi ro bảo trì có thể được đặt như hướng mở rộng hoặc câu hỏi phụ ở giai đoạn sau, khi dữ liệu và tiêu chí đánh giá đã được chuẩn hoá tốt hơn.

## Tài liệu tham khảo chính

1. Nagy, A., Spyridis, Y., Mills, G. J., & Argyriou, V. (2024). *User Experience Evaluation of AR Assisted Industrial Maintenance and Support Applications*. arXiv.
2. Xu, F., Nguyen, T., & Du, J. (2023). *Augmented Reality for Maintenance Tasks with ChatGPT for Automated Text-to-Action*. arXiv.
3. Wang, L., Tang, D., Liu, C., Nie, Q., Wang, Z., & Zhang, L. (2022). *An Augmented Reality-Assisted Prognostics and Health Management System Based on Deep Learning for IoT-Enabled Manufacturing*. *Sensors, 22*(17), 6472.
4. Zhao, A. Y., Gunturu, A., Do, E. Y.-L., & Suzuki, R. (2025). *Guided Reality: Generating Visually-Enriched AR Task Guidance with LLMs and Vision Models*. arXiv.
5. Decker, L., Leite, D., Giommi, L., & Bonacorsi, D. (2020). *Real-Time Anomaly Detection in Data Centers for Log-based Predictive Maintenance using an Evolving Fuzzy-Rule-Based Approach*. arXiv.
6. Viola, L., Ronchieri, E., & Cavallaro, C. (2022). *Combining Log Files and Monitoring Data to Detect Anomaly Patterns in a Data Center*. *Computers, 11*(8), 117.
7. Vajda, D. L., Do, T. V., Berczes, T., & Farkas, K. (2024). *Machine learning-based real-time anomaly detection using data pre-processing in the telemetry of server farms*. *Scientific Reports, 14*, 23288.
8. Liu, F. T., Ting, K. M., & Zhou, Z.-H. (2012). *Isolation-based anomaly detection*. *ACM Transactions on Knowledge Discovery from Data, 6*(1), 1-39.
9. Wei, Y., Jang-Jaccard, J., Xu, W., Sabrina, F., Camtepe, S., & Boulic, M. (2022). *LSTM-Autoencoder based Anomaly Detection for Indoor Air Quality Time Series Data*. arXiv.
10. Xu, J., Wu, H., Wang, J., & Long, M. (2021). *Anomaly Transformer: Time Series Anomaly Detection with Association Discrepancy*. arXiv.
11. Lim, B., Arik, S. O., Loeff, N., & Pfister, T. (2019). *Temporal Fusion Transformers for Interpretable Multi-horizon Time Series Forecasting*. arXiv.
