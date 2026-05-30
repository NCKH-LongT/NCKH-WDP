# Research Question Report

## Thông Tin Nhóm

**Học kỳ:** SU26  
**Lớp:** SE1822  
**Môn học:** WDP391  
**Nhóm:** 04  
**Thành viên:** Trần Đình Phong, Phạm Đức Thanh Phương, Đặng Thanh Tú, Ngô Nhật Minh

---

## Tên Đề Tài

**Hệ thống Theo dõi Xu hướng Công bố Bài báo Khoa học**

---

## Bối Cảnh và Hướng Nghiên Cứu

Theo [đề cương đề tài](d:\WDP%20REPORT\NCKH-WDP\01_topic_proposal\topic_proposal_vn.md), nhóm đang hướng tới việc xây dựng một nền tảng proof-of-concept cho phát hiện và theo dõi xu hướng công bố bài báo từ tài liệu khoa học, trong đó `khai thác thông tin từ API học thuật` đóng vai trò là lớp thu thập dữ liệu chính còn `AI (burst detection, topic modeling, trend analysis)` được sử dụng như lớp phân tích hỗ trợ. Điểm nhấn của đề tài không nằm ở việc tái tạo một công cụ phân tích bibliometric toàn diện như CiteSpace hay VOSviewer, mà ở việc kiểm chứng xem liệu metadata bài báo từ các API học thuật (Semantic Scholar, OpenAlex, Crossref), khi được kết hợp với các phương pháp phát hiện burst, phân tích chuỗi thời gian, xây dựng knowledge graph và trực quan hóa tương tác, có thể tạo ra một quy trình khám phá và dự báo xu hướng nghiên cứu trực quan, hữu ích và dễ tiếp cận hơn hay không.

---

## Vấn Đề Nghiên Cứu

Sự tăng trưởng nhanh chóng về số lượng bài báo khoa học đã khiến việc theo dõi xu hướng nghiên cứu ngày càng trở nên khó khăn. Các nền tảng tìm kiếm học thuật hiện tại (Google Scholar, Scopus, Web of Science) chủ yếu được thiết kế để tra cứu bài báo chứ không phải để phân tích xu hướng. Các thách thức chính bao gồm:

- Nhà nghiên cứu khó quan sát sự phát triển của một chủ đề qua các năm
- Thiếu công cụ để trực quan hóa sự xuất hiện, tăng trưởng hay suy giảm của các chủ đề theo thời gian
- Giảng viên và sinh viên phải duyệt thủ công qua tập tài liệu lớn để xác định chủ đề nào đang hot
- Chưa có công cụ nhẹ, dễ tiếp cận kết hợp tổng hợp metadata, phân tích xu hướng và trực quan hóa trong một nền tảng

---

## Sự Thay Đổi Hướng Nghiên Cứu

Sau khi rà soát các bài báo mới về phát hiện xu hướng công nghệ từ tài liệu khoa học, hướng nghiên cứu của đề tài đã được làm rõ thêm. Từ một hệ thống tổng quát "theo dõi xu hướng công bố", đề tài đã xác định ba trụ cột chính:

1. **Thu thập dữ liệu (Data Collection)**: Tích hợp các API học thuật mở (Semantic Scholar, OpenAlex, Crossref) để thu thập metadata
2. **Phân tích xu hướng (Trend Analysis)**: Sử dụng các kỹ thuật phát hiện burst, phân tích chuỗi thời gian, topic modeling để xác định xu hướng mới nổi
3. **Trực quan hóa và khám phá (Visualization & Discovery)**: Xây dựng dashboard tương tác, network visualization và hệ thống theo dõi cá nhân hóa

## Bối Cảnh Hình Thành Câu Hỏi Nghiên Cứu

Theo các bài báo trong rà soát hiện tại (10 bài báo về phát hiện xu hướng công nghệ), việc phát hiện và theo dõi xu hướng công bố từ tài liệu khoa học đang được hỗ trợ tốt bởi các phương pháp mới như:

1. **Các thuật toán phát hiện burst**: Kleinberg (2003) cung cấp nền tảng cho việc phát hiện sự bùng nổ của tần suất từ khóa
2. **Các chỉ số đánh giá mức độ mới nổi**: Liu & Porter (2020) đề xuất EScore, Liu & Tan (2023) đề xuất hệ thống 7-chiều
3. **Topic modeling hiện đại**: BERTopic và các phương pháp NLP giúp xác định chủ đề từ metadata
4. **LLM cho giải thích**: Các công cụ như DiTTO-LLM (Kim et al. 2025) cho phép giải thích ý nghĩa của các xu hướng
5. **Các công cụ thực tiễn**: CiteSpace (Chen 2006) đã chứng minh khả năng phát hiện xu hướng từ tài liệu học thuật

Tuy nhiên, cơ hội nghiên cứu nằm ở việc kết hợp đầy đủ các phương pháp này và tối ưu hóa cho metadata từ các API học thuật mở, thay vì chỉ dựa trên trích dẫn (có độ trễ 1-2 năm)

## Câu Hỏi Nghiên Cứu Chính

**RQ_Main: Làm thế nào có thể xây dựng một nền tảng web tích hợp để phát hiện, đánh giá mức độ mới nổi, và trực quan hóa các xu hướng công bố bài báo từ metadata API học thuật, nhằm hỗ trợ nhà nghiên cứu, giảng viên và sinh viên khám phá xu hướng nghiên cứu một cách hiệu quả?**

Bản tiếng Anh:

**RQ_Main: How can we build an integrated web platform to detect, assess emergence level, and visualize emerging publication trends from academic API metadata to support researchers, lecturers, and students in discovering research trends effectively?**

## Các Câu Hỏi Phụ

**RQ1_DataCollection:** Những API học thuật nào (Semantic Scholar, OpenAlex, Crossref) phù hợp nhất để thu thập metadata bài báo, và làm sao để chuẩn hóa dữ liệu từ các nguồn khác nhau?

**RQ2_TrendDetection:** Phương pháp kết hợp nào (burst detection + time-series analysis + topic modeling) hiệu quả nhất để phát hiện xu hướng công bố mới nổi mà **giảm độ trễ thời gian** so với các phương pháp dựa trên trích dẫn?

**RQ3_Evaluation:** Hệ thống chỉ số nào (EScore 3-chiều, framework 7-chiều, hoặc các chỉ số tùy chỉnh) phù hợp nhất để xếp hạng và so sánh **mức độ mới nổi thực sự** của các xu hướng khác nhau?

**RQ4_Visualization:** Cách trực quan hóa nào (trend timeline, network graph, heatmap, dashboard) giúp người dùng (nhà nghiên cứu, giảng viên, sinh viên) khám phá và hiểu rõ xu hướng công bố một cách trực quan nhất?

**RQ5_Personalization:** Hệ thống theo dõi (watch, bookmark, notification) nào giúp người dùng theo dõi các journal, từ khóa hoặc chủ đề quan tâm và nhận thông báo khi có bài báo mới liên quan một cách hiệu quả?

## Phạm Vi Khái Niệm Cần Làm Rõ

### Định Nghĩa "Xu Hướng Công Bố Bài Báo Mới Nổi" (Emerging Publication Trend)

Trong bối cảnh của đề tài, một **xu hướng công bố bài báo mới nổi** được định nghĩa là:
- Một **chủ đề, khóa, hoặc lĩnh vực nghiên cứu** mà tần suất các bài báo xảy ra
- Có **tần suất xuất hiện tăng đột ngột** (burst) so với mức độ bình thường
- Có **cộng đồng tác giả tích cực** đang nghiên cứu về vấn đề
- Có **liên kết ngữ nghĩa** giữa các bài báo và được nhóm thành các chủ đề tương quan

**Không bao gồm:**
- Các xu hướng tạm thời chỉ bùng nổ rồi biến mất
- Các chủ đề cũ được tái phát hiện nhưng không có sự phát triển ý nghĩa

### Định Nghĩa "Người Dùng Mục Đích" (Target Users)

Hệ thống hướng tới ba nhóm người dùng chính:
- **Nhà nghiên cứu (Researcher)**: Phân tích xu hướng chuyên sâu, theo dõi journal và từ khóa cụ thể
- **Giảng viên / Sinh viên (Lecturer / Student)**: Tìm kiếm bài báo tham khảo, khám phá chủ đề trending
- **Quản trị viên hệ thống (Administrator)**: Cấu hình API, quản lý người dùng, giám sát hệ thống

---

## Khoảng Trống Nghiên Cứu Mà Đề Tài Khai Thác

1. **Kết hợp đầy đủ phương pháp**: Rất ít công trình kết hợp:
   - Burst detection (Kleinberg 2003) + 
   - Emerging assessment (Liu & Porter 2020 EScore, Liu & Tan 2023 7D) + 
   - Knowledge Graph (Luan et al. 2018 SciIE) + 
   - LLM interpretation (Kim et al. 2025 DiTTO-LLM) + 
   - Time-series forecasting (Benidis et al. 2018 DeepAR, Lim et al. 2021 TFT)
   
   Trong **cùng một nền tảng web**, đặc biệt là ở cấp độ proof-of-concept có khả năng triển khai trên các API học thuật mở

2. **Giảm độ trễ thời gian**: Hầu hết các công cụ hiện tại (CiteSpace, VOSviewer) phụ thuộc vào trích dẫn, vốn có độ trễ tự nhiên 1-2 năm. Đề tài có thể khai thác:
   - **Metadata metadata từ API**: Các bài báo mới được công bố liên tục, không cần chờ trích dẫn tích lũy
   - **Co-occurrence keywords** từ abstract: Cho phép phát hiện sự kết hợp ý tưởng mới
   - **Burst trong publication patterns**: Có thể phát hiện được trong vài tháng

3. **Cạnh tranh lành mạnh so với CiteSpace**: Mặc dù CiteSpace là công cụ hùng mạnh, nhưng:
   - CiteSpace chủ yếu là desktop tool, không phải web platform
   - CiteSpace phụ thuộc vào WoS hoặc Scopus (trả phí)
   - Đề tài có thể tập trung vào API mở + user experience + personalization

---

## Đề Xuất Cấu Trúc Hệ Thống

```
┌──────────────────────────────────────────────────────────────┐
│                    Data Collection Layer                      │
│  - API: Semantic Scholar, OpenAlex, Crossref                 │
│  - Metadata: title, abstract, keywords, year, author, journal│
└───────────────────────┬──────────────────────────────────────┘
                        │
┌───────────────────────▼──────────────────────────────────────┐
│              Data Processing & Analysis Layer                │
│  - Metadata normalization & deduplication                   │
│  - TF-IDF keyword ranking                                    │
│  - Co-occurrence analysis                                    │
└───────────────────────┬──────────────────────────────────────┘
                        │
┌───────────────────────▼──────────────────────────────────────┐
│        Trend Detection & Ranking Layer                       │
│  - Time-series analysis (papers per year/quarter)           │
│  - Burst detection (Kleinberg algorithm)                    │
│  - Growth rate scoring                                       │
│  - EScore or 7-dimensional emergence metrics                │
└───────────────────────┬──────────────────────────────────────┘
                        │
┌───────────────────────▼──────────────────────────────────────┐
│     User Interface & Discovery Layer                         │
│  - Search & filter papers                                    │
│  - Trending topics dashboard                                 │
│  - Keyword co-occurrence network visualization              │
│  - Bookmark & watch functionality                           │
└───────────────────────┬──────────────────────────────────────┘
                        │
┌───────────────────────▼──────────────────────────────────────┐
│    Notification & Reporting Layer                            │
│  - Personalized notifications                                │
│  - Trend reports (PDF/CSV export)                           │
│  - Admin dashboard & monitoring                              │
└──────────────────────────────────────────────────────────────┘
```

---

## Thước Đo Đánh Giá Đề Xuất

### Phần Thu Thập & Xử Lý (Data Collection & Processing)
- **Metadata quality**: Tần suất thành công của trích xuất metadata từ API
- **Data freshness**: Thời gian độ trễ giữa API và cơ sở dữ liệu
- **Deduplication accuracy**: Tần suất xác định chính xác các bài trùng lặp

### Phần Phát Hiện Xu Hướng (Trend Detection)
- **Precision@K**: Tỷ lệ xu hướng phát hiện thực sự là xu hướng mới nổi
- **Lead time**: Bao nhiêu tháng sớm hơn so với phương pháp baseline (CiteSpace)
- **Recall**: Tỷ lệ xu hướng thực sự được phát hiện

### Phần Đánh Giá (Evaluation)
- **EScore/Emergence metric accuracy**: Độ chính xác của các chỉ số emergence trong việc xếp hạng xu hướng
- **Ranking consistency**: Độ ổn định của các chỉ số khi dữ liệu được cập nhật

### Phần Trực Quan Hóa & Khám Phá (Visualization & Discovery)
- **User engagement**: Số lượng người dùng sử dụng các tính năng chính
- **Search effectiveness**: Thời gian tìm kiếm trung bình, tỷ lệ tìm thấy kết quả
- **Bookmark/Watch activity**: Mức độ sử dụng tính năng cá nhân hóa

---

## Kết Luận & Định Hướng Phương Pháp

Đề tài "Hệ thống Theo dõi Xu hướng Công bố Bài báo Khoa học" hướng tới việc xây dựng một nền tảng web integrated để:

✅ **Mục tiêu Chính:**
- Tích hợp metadata từ các API học thuật mở (Semantic Scholar, OpenAlex, Crossref)
- Phát hiện xu hướng công bố mới nổi bằng kết hợp burst detection, time-series analysis, topic modeling
- Đánh giá mức độ mới nổi của các xu hướng sử dụng EScore hoặc metrics 7-chiều
- Cung cấp dashboard tương tác, visualization network, và tính năng theo dõi cá nhân hóa

✅ **Lợi ích của Hướng Này:**
- Có nền tảng lý thuyết vững chắc từ 10 bài báo rà soát về phát hiện xu hướng công nghệ
- Có khả năng ứng dụng rộng rãi hơn CiteSpace (web-based, mở rộng được, dễ tiếp cận)
- Phù hợp với sở thích của nhóm về NLP/AI/Web development
- Giải quyết một bài toán thực tế: khó khăn của nhà nghiên cứu, giảng viên, sinh viên trong theo dõi xu hướng

⚠️ **Thách Thức Cần Giải Quyết:**
- Kết hợp nhiều thành phần công nghệ (API integration, burst detection, topic modeling, network visualization)
- Đảm bảo chất lượng dữ liệu khi tích hợp từ nhiều API khác nhau
- Xác định metrics phù hợp để đánh giá "mức độ mới nổi" một cách khách quan
- Cần xác thực kết quả từ chuyên gia miền lĩnh vực

## Định Hướng Thực Hiện

1. **Giai Đoạn 1 - Thu thập & Xử Lý Dữ Liệu**:
   - Cấu hình kết nối với 2-3 API học thuật chính
   - Xây dựng pipeline chuẩn hóa metadata và phát hiện trùng lặp
   - Lưu trữ vào cơ sở dữ liệu

2. **Giai Đoạn 2 - Phát Hiện Xu Hướng**:
   - Triển khai time-series analysis cho từ khóa/chủ đề
   - Implement Kleinberg burst detection algorithm
   - Tính toán growth rate và các chỉ số xu hướng

3. **Giai Đoạn 3 - Đánh Giá & Xếp Hạng**:
   - So sánh EScore (Liu & Porter) vs. framework 7-chiều (Liu & Tan)
   - Xác định metric phù hợp nhất cho bối cảnh bài báo khoa học
   - Xây dựng ranking system

4. **Giai Đoạn 4 - Giao Diện Người Dùng**:
   - Xây dựng dashboard hiển thị trending topics
   - Network visualization cho keyword co-occurrence
   - Tính năng search, filter, bookmark, watch
   - Hệ thống notification

## Phạm Vi Đề Tài Proof-of-Concept

Với đặc thù của một đồ án học thuật, đề tài sẽ tập trung vào:
- **Đầu vào**: Metadata từ 1-2 API chính và một khoảng thời gian ý định (ví dụ 3-5 năm)
- **Xử lý**: Các phương pháp đã được chứng minh trong 10 bài báo rà soát
- **Đầu ra**: Một web platform với các chức năng cốt lõi, chứ không phải một hệ thống production-grade
- **Đánh giá**: Kết hợp định lượng (precision, recall, lead time) và định tính (expert feedback)


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
