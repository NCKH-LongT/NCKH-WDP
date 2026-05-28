# Paper 01 Summary

## Citation
- **Tên bài:** Comparative Performance of Retrieval Augmented Generation Tourism Chatbots
- **Tác giả:** Amar Al Farizi, Primandani Arsi, Pungkas Subarkah
- **Năm:** 2026
- **Nguồn:** Indonesian Journal of Innovation Studies (IJINS), Vol. 27, No. 1
- **DOI/Link:** Trong drive

## Problem
Mô hình ngôn ngữ lớn (LLM) khi ứng dụng làm chatbot thường gặp hiện tượng halucination (ảo tưởng thông tin) khi phải xử lý dữ liệu động, cục bộ. Nghiên cứu thực nghiệm so sánh các cấu hình RAG khác nhau để tìm ra sự kết hợp tối ưu giữa mô hình Embedding và mô hình ngôn ngữ cho chatbot.

## Method
Xây dựng pipeline RAG sử dụng framework LangChain làm bộ điều phối (orchestrator) và Pinecone làm cơ sở dữ liệu vector. Phương pháp so sánh dựa trên việc đối đối sánh trực tiếp chéo giữa:
- 2 mô hình Embedding: Multilingual-E5-Large (1024-dim) và All-Indo-E5-Small-V4 (384-dim).
- 3 mô hình LLM: GPT-4.1-mini, GPT-4o-mini, và Claude Haiku 3.5.

## Dataset / Context
Ngữ cảnh thử nghiệm là hệ thống chatbot du lịch vùng Banyumas Regency. Bộ dữ liệu gồm thông tin của 49 địa điểm được chuẩn hóa dưới dạng JSON terstruktur (ID, tên, vị trí, giá vé, giờ mở cửa, hoạt động), tổng cộng 4.765 từ và được kiểm thử qua 215 câu hỏi.

## Evaluation & Metrics
Hệ thống được đánh giá toàn diện dựa trên:
- Khả năng rút trích (Retrieval): Precision, Recall, F1-Score.
- Chất lượng tạo văn bản (Generation): BERTScore F1, BLEU-2.
- Hiệu suất thời gian: Thời gian trễ trung bình (Avg Latency tính bằng giây).

## Results
- Mô hình Embedding đóng vai trò quyết định đến độ chính xác của pha rút trích thông tin, quan trọng hơn sự thay đổi của LLM.
- Mô hình Multilingual-E5-Large (1024 chiều) đạt hiệu suất tuyệt đối (Precision, Recall, F1-Score = 1.0000) trên mọi LLM thử nghiệm.
- Cấu hình tối ưu nhất: Kết hợp Multilingual-E5-Large và GPT-4.1-mini cho kết quả BERTScore F1 tốt nhất (0.7515) với độ trễ thấp nhất (1.555 giây). GPT-4o-mini là phương án tối ưu về mặt chi phí.
- Claude Haiku 3.5 cho kết quả BLEU-2 thấp (0.0929) nhưng BERTScore cao, cấu trúc câu tự nhiên nhưng độ trễ cao nhất (> 2.1 giây).

## Limitations
Nghiên cứu mới chỉ thử nghiệm trên các câu hỏi đơn lẻ (single-question), chưa đánh giá hệ thống trong kịch bản hội thoại phức tạp chứa chuỗi câu hỏi phụ thuộc (multi-question/contextual follow-ups).

## Relevance to our topic
Mức độ liên quan: Rất cao (Core-Method paper). Bài báo này cung cấp khung kiến trúc RAG, kết quả benchmark thực nghiệm chính xác cho các dòng mô hình ngôn ngữ nhỏ (GPT-4.1-mini, GPT-4o-mini) trực tiếp trên cấu trúc dữ liệu JSON. Đây là nền tảng kỹ thuật trực tiếp cho module Conversational AI Booking Assistant (FE-03, FE-04) của dự án SmartStay AI.

## Possible improvement for our system
Áp dụng trực tiếp vào Node AI Service của SmartStay AI:
1. Sử dụng mô hình embedding có kích thước từ 1024-dim trở lên (như cấu trúc mã nguồn Multilingual-E5-Large) để vector hóa thông tin phòng, giá và dịch vụ của khách sạn từ database JSON sang Pinecone nhằm đạt độ chính xác truy xuất tuyệt đối.
2. Lựa chọn mô hình GPT-4.1-mini làm lõi xử lý chatbot hội thoại để tối ưu hóa thời gian phản hồi cho khách hàng đặt phòng (đảm bảo độ trễ dưới 1.6 giây) mà vẫn giữ được độ chính xác ngữ nghĩa cao.