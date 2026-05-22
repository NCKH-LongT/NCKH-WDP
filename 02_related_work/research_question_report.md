# Research Question Report

## Bối cảnh hình thành câu hỏi nghiên cứu

Theo [đề cương đề tài](/D:/Study/FPTU/WDP301/projects/NCKH-WDP/01_topic_proposal/topic_proposal_vn.md), nhóm đang hướng tới việc xây dựng một nền tảng proof-of-concept cho giám sát và bảo trì hạ tầng trong môi trường trung tâm dữ liệu mô phỏng, trong đó `AR` đóng vai trò là lớp tương tác chính còn `AI` được sử dụng như lớp phân tích hỗ trợ. Điểm nhấn của đề tài không nằm ở việc tái tạo một hệ thống trung tâm dữ liệu doanh nghiệp hoàn chỉnh, mà ở việc kiểm chứng xem liệu dữ liệu telemetry thời gian thực, khi được kết hợp với giao diện AR và mô hình AI phù hợp, có thể tạo ra một quy trình vận hành trực quan và hữu ích hơn hay không.

Từ định hướng đó, phần câu hỏi nghiên cứu cần làm rõ hai vấn đề. Thứ nhất, AI trong đề tài này thực sự sẽ giải quyết điều gì: chỉ phát hiện bất thường, dự báo xu hướng, hay đi xa hơn đến hỗ trợ quyết định bảo trì. Thứ hai, phạm vi nào là hợp lý trong bối cảnh một hệ thống mô phỏng ở quy mô học thuật, để câu hỏi nghiên cứu vừa có ý nghĩa học thuật, vừa có khả năng triển khai và đánh giá được bằng thực nghiệm.

## Nhận xét về hướng nghiên cứu hiện tại

Sau khi đối chiếu proposal với nhóm 12 bài báo đã rà soát, có thể thấy hướng nghiên cứu của đề tài là hợp lý, nhưng phần AI cần được phát biểu cẩn trọng hơn để tránh ôm đồm. Các tài liệu liên quan hiện nay cho thấy ba xu hướng chính.

Thứ nhất, ở nhóm nghiên cứu về `AR-assisted maintenance`, các công trình như Nagy et al. (2024), Xu et al. (2023), Wang et al. (2022) và Zhao et al. (2025) đều cho thấy AR đặc biệt hữu ích khi cần gắn dữ liệu vận hành với bối cảnh không gian và quy trình thao tác tại chỗ. Tuy nhiên, phần lớn các bài này tập trung vào cách trình bày hướng dẫn, trải nghiệm người dùng, hoặc khả năng hỗ trợ thao tác, thay vì đi sâu vào xây dựng một mô hình phân tích telemetry phức tạp.

Thứ hai, ở nhóm nghiên cứu về `data-center anomaly detection`, các công trình của Decker et al. (2020), Viola et al. (2022) và Vajda et al. (2024) nhấn mạnh rằng bài toán trung tâm không chỉ là hiển thị trạng thái hệ thống mà là nhận diện bất thường từ log, monitoring data và telemetry trong điều kiện thời gian thực. Nhóm bài này gần với phần backend của đề tài hơn cả, vì chúng trực tiếp xử lý dữ liệu hạ tầng và quan tâm đến các yếu tố thực tế như độ trễ phát hiện, tính thích nghi và khả năng kết hợp nhiều nguồn tín hiệu.

Thứ ba, ở nhóm bài phương pháp luận, các mô hình như `Isolation Forest`, `LSTM Autoencoder`, `Anomaly Transformer` và `Temporal Fusion Transformer` cung cấp nền tảng để lựa chọn mô hình AI phù hợp cho proof-of-concept. Trong đó, `Isolation Forest` thích hợp cho một baseline gọn nhẹ; `LSTM Autoencoder` phù hợp nếu muốn khai thác đặc trưng chuỗi thời gian; `Anomaly Transformer` và `TFT` có giá trị nghiên cứu cao hơn nhưng đòi hỏi chi phí triển khai và đánh giá lớn hơn.

Từ ba nhóm bằng chứng trên, có thể rút ra một nhận xét quan trọng: đối với đề tài của nhóm, phần được hậu thuẫn tốt nhất từ literature không phải là một tuyên bố rộng về "predictive maintenance", mà là khả năng phát hiện và cảnh báo sớm các trạng thái bất thường trên hạ tầng mô phỏng, sau đó chuyển các tín hiệu đó thành thông tin có ngữ cảnh trên dashboard và giao diện AR.

## Câu hỏi nghiên cứu được đề xuất

Dựa trên bối cảnh đề tài và mức độ hỗ trợ của các tài liệu liên quan, câu hỏi nghiên cứu chính nên được phát biểu lại theo hướng chặt hơn như sau:

**RQ1: Các mô hình AI có thể phát hiện và cảnh báo sớm đến mức nào các trạng thái hạ tầng bất thường dựa trên dữ liệu telemetry thời gian thực và các mẫu hành vi vận hành của hệ thống trong môi trường trung tâm dữ liệu mô phỏng?**

Nếu cần trình bày bản tiếng Anh trong proposal hoặc slide:

**RQ1: To what extent can AI models detect and provide early warning of abnormal infrastructure states based on real-time telemetry and operational behavior patterns in a simulated data center environment?**

Cách phát biểu này phù hợp hơn với phạm vi thực tế của đề tài vì nó giữ được trọng tâm AI, đồng thời không đẩy nghiên cứu đi quá xa sang bài toán dự báo bảo trì toàn diện, vốn đòi hỏi nhãn dữ liệu, kịch bản hỏng hóc và quy trình đánh giá phức tạp hơn đáng kể.

## Vì sao câu hỏi này phù hợp hơn

Điểm mạnh đầu tiên của câu hỏi trên là nó bám sát đúng cấu trúc hệ thống mà nhóm đang xây dựng. Ở proposal, telemetry được thu thập liên tục từ các node và dịch vụ container hóa; AI được dùng như một lớp phân tích bổ sung; còn AR được dùng để hiển thị trạng thái, cảnh báo và hướng dẫn bảo trì theo ngữ cảnh. Với cấu trúc đó, việc hỏi về khả năng phát hiện và cảnh báo sớm bất thường là hoàn toàn tự nhiên, vì đây là khâu nối trực tiếp giữa dữ liệu vận hành và giao diện hỗ trợ người dùng.

Điểm mạnh thứ hai là câu hỏi này phù hợp với bằng chứng nghiên cứu hiện có. Các bài của Decker et al. (2020), Viola et al. (2022) và Vajda et al. (2024) đều cho thấy dữ liệu hạ tầng có thể được xử lý để tìm ra bất thường hoặc mẫu vận hành đáng chú ý. Trong khi đó, các bài như Xu et al. (2023) hay Wang et al. (2022) lại cho thấy đầu ra phân tích có thể tiếp tục được chuyển hóa thành hỗ trợ thao tác hoặc hỗ trợ bảo trì trong lớp AR. Nói cách khác, câu hỏi này đứng đúng ở điểm giao nhau giữa hai nhánh nghiên cứu mà đề tài đang muốn kết hợp.

Điểm mạnh thứ ba là nó khả thi trong khuôn khổ một đồ án học thuật. Nhóm có thể chủ động thiết kế các kịch bản bất thường trong môi trường mô phỏng, chẳng hạn như tăng tải bất thường, vòng lặp restart container, suy giảm tài nguyên theo thời gian hoặc mất cân bằng giữa các chỉ số. Từ đó, nhóm có thể tạo ground truth ở mức sự kiện để đánh giá mô hình tương đối rõ ràng. Nếu chuyển ngay sang mục tiêu "dự báo rủi ro bảo trì", bài toán sẽ khó hơn đáng kể vì cần định nghĩa thêm thế nào là rủi ro, khoảng thời gian dự báo bao lâu, và tiêu chí đánh giá nào phản ánh đúng ý nghĩa vận hành.

## Phạm vi khái niệm cần làm rõ

Để câu hỏi nghiên cứu không trở nên mơ hồ, hai khái niệm trong RQ1 cần được hiểu rõ.

Thứ nhất là `trạng thái hạ tầng bất thường`. Trong phạm vi đề tài, điều này không nhất thiết chỉ là một lỗi phần cứng hay sự cố nghiêm trọng, mà có thể bao gồm các điều kiện vận hành lệch khỏi mẫu bình thường đã được xác lập trong môi trường mô phỏng. Ví dụ, CPU tăng cao kéo dài không tương xứng với workload, bộ nhớ suy giảm bất thường, số lần restart container tăng liên tục, hoặc trạng thái dịch vụ không ổn định trong khi các chỉ số khác vẫn dao động.

Thứ hai là `mẫu hành vi vận hành`. Cụm từ này nên được hiểu là các dạng biến thiên có ý nghĩa của telemetry theo thời gian, thay vì chỉ là các điểm dữ liệu rời rạc. Nói cách khác, hệ thống không chỉ quan sát một giá trị CPU hay memory tại một thời điểm, mà quan tâm đến xu hướng, dao động, chu kỳ, mối tương quan giữa các chỉ số và cách chúng thay đổi trước khi một bất thường xuất hiện.

Việc làm rõ hai khái niệm này rất quan trọng, vì nó ảnh hưởng trực tiếp đến cách nhóm trích đặc trưng, gán nhãn dữ liệu mô phỏng và lựa chọn mô hình AI.

## Các câu hỏi phụ nên đi kèm

Để RQ1 có thể triển khai thành một kế hoạch thực nghiệm mạch lạc, nên tách thêm một số câu hỏi phụ:

**RQ1a.** Những đặc trưng telemetry và mẫu hành vi vận hành nào đóng góp nhiều nhất vào việc phát hiện trạng thái bất thường?

**RQ1b.** Trong các mô hình được xem xét, mô hình nào cho sự cân bằng tốt nhất giữa độ chính xác phát hiện, tỷ lệ cảnh báo sai và thời gian cảnh báo?

**RQ1c.** Kết quả phát hiện bất thường có thể được chuyển hóa như thế nào thành thông tin vận hành có ngữ cảnh để hiển thị hiệu quả trên dashboard và giao diện AR?

Ba câu hỏi phụ này giúp liên kết phần AI với phần hệ thống tổng thể của đề tài. Nếu chỉ dừng ở việc so sánh mô hình theo độ chính xác, nghiên cứu sẽ dễ nghiêng về một bài toán machine learning thuần túy, trong khi giá trị thực sự của đề tài nằm ở chỗ đầu ra phân tích phải phục vụ được quy trình giám sát và bảo trì.

## Định hướng phương pháp nghiên cứu

Xét về bản chất, đây là một nghiên cứu thực nghiệm theo hướng thiết kế và đánh giá hệ thống. Dữ liệu không đến từ một trung tâm dữ liệu thật mà được sinh ra từ môi trường mô phỏng có kiểm soát, vì vậy nhóm có điều kiện chủ động hơn trong việc xây dựng kịch bản và quan sát hành vi hệ thống.

Một hướng triển khai hợp lý là tổ chức nghiên cứu theo ba lớp. Lớp thứ nhất là lớp sinh dữ liệu, nơi các node, dịch vụ và container trong môi trường Docker tạo ra telemetry như CPU, bộ nhớ, mạng, lưu trữ, trạng thái dịch vụ và log liên quan. Lớp thứ hai là lớp phân tích, nơi các mô hình AI được áp dụng để phát hiện bất thường hoặc sinh ra điểm cảnh báo. Lớp thứ ba là lớp trình bày, nơi dashboard và AR sử dụng các kết quả này để hỗ trợ người vận hành theo hai chế độ khác nhau: giám sát tập trung và kiểm tra tại chỗ.

Với cấu trúc đó, nghiên cứu không cần theo đuổi một mô hình quá phức tạp ngay từ đầu. Một chiến lược phù hợp là xây dựng tối thiểu một baseline đơn giản, một mô hình chuỗi thời gian, và nếu còn đủ nguồn lực thì bổ sung một mô hình nâng cao để so sánh.

## Gợi ý về mô hình và thiết kế thực nghiệm

Từ proposal và literature hiện tại, có thể đề xuất một lộ trình tương đối cân bằng.

Ở mức cơ sở, nhóm nên có một baseline dựa trên ngưỡng hoặc luật đơn giản để làm mốc tham chiếu. Điều này quan trọng vì trong các hệ thống giám sát thực tế, nhiều cảnh báo vẫn khởi đầu từ logic đơn giản, và việc chứng minh mô hình AI tốt hơn baseline là yêu cầu cần thiết về mặt học thuật.

Tiếp theo, `Isolation Forest` là một lựa chọn hợp lý cho baseline học máy không giám sát vì mô hình này nhẹ, dễ triển khai và phù hợp với telemetry đa biến ở quy mô proof-of-concept. Nếu mục tiêu là nắm bắt được động học theo thời gian rõ hơn, `LSTM Autoencoder` là lựa chọn phù hợp hơn vì có thể học mẫu bình thường từ chuỗi dữ liệu và phát hiện sai lệch thông qua lỗi tái tạo.

Các mô hình nâng cao hơn như `Anomaly Transformer` hoặc `TFT` có thể được xem như hướng mở rộng. Chúng giúp tăng chiều sâu nghiên cứu, nhưng không nên trở thành điều kiện bắt buộc của phiên bản đầu tiên, bởi chi phí huấn luyện, tinh chỉnh và giải thích kết quả có thể vượt quá phạm vi hợp lý của đề tài.

Về kịch bản thực nghiệm, môi trường mô phỏng nên có cả trạng thái bình thường lẫn những bất thường được thiết kế có chủ đích. Chẳng hạn, nhóm có thể tạo các pha tải ổn định, tải tăng đột biến nhưng hợp lệ, suy giảm tài nguyên kéo dài, lỗi restart lặp lại, hoặc sai lệch giữa các chỉ số tưởng như không liên quan. Chính các kịch bản này sẽ quyết định giá trị thực chất của bộ dữ liệu thực nghiệm.

## Thước đo đánh giá nên sử dụng

Với câu hỏi nghiên cứu đã đề xuất, việc đánh giá mô hình không nên chỉ dừng ở độ chính xác tổng quát. Vì đề tài hướng tới một nền tảng hỗ trợ vận hành, các chỉ số đánh giá cần phản ánh được cả chất lượng phát hiện lẫn giá trị sử dụng trong bối cảnh thực tế.

Các chỉ số như `Precision`, `Recall`, `F1-score` và `MCC` vẫn cần thiết để đánh giá năng lực phân loại hoặc phát hiện bất thường. Tuy nhiên, đối với đề tài này, `detection delay` cũng rất quan trọng vì một cảnh báo đến muộn sẽ ít ý nghĩa hơn trong quy trình kiểm tra bằng AR. Ngoài ra, tỷ lệ cảnh báo sai cũng cần được quan tâm, bởi nếu hệ thống liên tục cảnh báo sai, người dùng sẽ nhanh chóng mất niềm tin vào lớp phân tích AI.

Nếu nhóm xây dựng được nhãn ở mức sự kiện thay vì chỉ ở từng điểm dữ liệu, việc đánh giá ở mức sự kiện sẽ có giá trị hơn cho phần báo cáo học thuật. Điều này đặc biệt phù hợp với các bất thường kéo dài theo một khoảng thời gian nhất định, thay vì chỉ xuất hiện chớp nhoáng ở một timestamp đơn lẻ.

## Khoảng trống nghiên cứu mà đề tài có thể khai thác

Từ phần tổng hợp tài liệu hiện có, có thể thấy chưa nhiều công trình kết nối đầy đủ bốn yếu tố trong cùng một hệ thống: telemetry hạ tầng thời gian thực, phát hiện bất thường bằng AI, giao diện AR gắn theo không gian và quy trình bảo trì trong một môi trường mô phỏng có thể kiểm soát.

Các nghiên cứu về AR thường mạnh ở khía cạnh tương tác và hỗ trợ thao tác. Các nghiên cứu về anomaly detection lại mạnh ở xử lý telemetry, log hoặc chuỗi thời gian. Điều đề tài của nhóm có thể đóng góp là đưa hai nhánh này gặp nhau trong một proof-of-concept có cấu trúc rõ ràng: dữ liệu hạ tầng được sinh ra có chủ đích, bất thường được phát hiện bằng AI, sau đó kết quả được trực quan hóa không chỉ trên dashboard mà còn ngay trên node hoặc rack mô phỏng thông qua AR.

Nói cách khác, điểm mới của đề tài không nhất thiết nằm ở việc sáng tạo ra một thuật toán phát hiện bất thường hoàn toàn mới, mà nằm ở cách tổ chức một quy trình vận hành có ngữ cảnh hơn, trong đó đầu ra của AI thực sự trở thành thành phần có ích cho người vận hành.

## Kết luận và khuyến nghị cuối cùng

Từ proposal và bối cảnh related work hiện tại, có thể khẳng định rằng hướng nghiên cứu của nhóm là hợp lý, nhưng phần câu hỏi nghiên cứu cần được phát biểu theo cách chặt chẽ và thực tế hơn. So với các diễn đạt trước đó, câu hỏi nhấn vào "predictive maintenance" một cách rộng sẽ dễ tạo cảm giác tham vọng quá mức và khó chứng minh bằng thực nghiệm trong phạm vi đồ án.

Vì vậy, câu hỏi nên được chốt theo hướng:

**Các mô hình AI có thể phát hiện và cảnh báo sớm đến mức nào các trạng thái hạ tầng bất thường dựa trên dữ liệu telemetry thời gian thực và các mẫu hành vi vận hành của hệ thống trong môi trường trung tâm dữ liệu mô phỏng?**

Đây là cách đặt vấn đề vừa bám sát kiến trúc đề tài, vừa có cơ sở từ literature, vừa cho phép nhóm triển khai một kế hoạch thực nghiệm rõ ràng. Nếu sau này nhóm vẫn muốn mở rộng sang dự báo hoặc ước lượng rủi ro bảo trì, phần đó nên được xem như một hướng phát triển tiếp theo hoặc một câu hỏi phụ nâng cao, thay vì trở thành gánh nặng ngay từ trung tâm của RQ1.

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
