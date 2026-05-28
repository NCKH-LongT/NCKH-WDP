# Paper 04 Summary

## Citation

- **Tên bài:** Research on Hotel Management System (Domain khách sạn)
- **Tác giả:** Nghiên cứu viên / Tác giả thuộc lĩnh vực Hệ thống thông tin (ResearchGate)
- **Năm:** 2022
- **Nguồn:** ResearchGate / International Journal of Scientific Research
- **DOI/Link:** [Link](https://www.researchgate.net/publication/365151133_Research_on_Hotel_Management_System)

## Problem

Bài báo tập trung giải quyết bài toán số hóa và tối ưu hóa các quy trình vận hành thủ công của khách sạn. Đối với các khách sạn vừa và nhỏ, việc quản lý phòng trống, đặt phòng thủ công của khách hàng và quy trình thanh toán giấy tờ tốn nhiều thời gian, dễ gây ra sai sót, trùng lịch (overbooking) và khó khăn cho ban quản lý trong việc theo dõi báo cáo doanh thu theo thời gian thực.

## Method

Nghiên cứu đề xuất một **Hệ thống Quản lý Khách sạn (Hotel Management System - HMS)** hoàn chỉnh, được xây dựng theo kiến trúc Client-Server hoặc kiến trúc 3 lớp (3-tier architecture):
- **Phân hệ Client (Frontend):** Giao diện tương tác trực quan cho khách lưu trú đặt phòng và nhân viên lễ tân vận hành.
- **Phân hệ Server (Backend):** Xử lý các quy tắc nghiệp vụ (Business logic) như kiểm tra phòng trống, cấu hình giá, xử lý giao dịch.
- **Phân hệ Database (Cơ sở dữ liệu):** Lưu trữ tập trung thông tin phòng, thông tin khách hàng và lịch sử giao dịch.

## Dataset

Hệ thống được thử nghiệm trên dữ liệu danh mục phòng giả lập cùng với kịch bản đặt phòng thực tế của các khách hàng tại một khách sạn vừa và nhỏ để kiểm thử hiệu năng và tính đúng đắn của các tính năng.

## Evaluation

Đánh giá hệ thống dựa trên:
- **Độ chính xác (Accuracy):** Tính nhất quán của việc đồng bộ trạng thái phòng trống theo thời gian thực khi có giao dịch đặt phòng.
- **Thời gian xử lý (Processing Time):** Tốc độ hoàn tất một đơn đặt phòng và xuất hóa đơn hành chính.
- **Khả năng sử dụng (Usability):** Khảo sát ý kiến của lễ tân và quản lý về mức độ tối ưu công việc hành chính.

## Results

- Số hóa thành công toàn bộ quy trình đặt phòng, check-in, check-out và quản lý phòng trống.
- Loại bỏ hoàn toàn lỗi trùng phòng (overbooking) nhờ cơ chế khóa bản ghi phòng trống tức thời trong cơ sở dữ liệu khi có giao dịch đặt phòng đang diễn ra.
- Giảm thiểu 40% thời gian xử lý thủ tục hành chính tại quầy lễ tân và tự động xuất hóa đơn chính xác.

## Limitations

- Hệ thống mang tính chất quản lý truyền thống (CRUD), chưa tích hợp các giải pháp trí tuệ nhân tạo (AI) hay mô hình học máy để tối ưu giá phòng (Dynamic Pricing) hoặc tự động tương tác với khách hàng qua Chatbot.

## Relevance to our topic

- **Mức độ liên quan:** Cao (Domain Reference).
- **Lý do:** Bài báo cung cấp cấu trúc luồng nghiệp vụ cốt lõi (Core Business Flow) của một hệ thống quản lý khách sạn tiêu chuẩn. Đây chính là khung xương vận hành (Backbone) để hệ thống **SmartStay AI** tích hợp thêm các module thông minh như Chatbot đặt phòng và AI Marketing.

## Possible improvement

Áp dụng trực tiếp vào **SmartStay AI**:
1. Kế thừa sơ đồ luồng dữ liệu (Data Flow) và cấu trúc cơ sở dữ liệu quan hệ quản lý phòng (Room Inventory) nhằm đảm bảo hệ thống vận hành trơn tru và nhất quán.
2. Tích hợp OpenAI API lên trên nền tảng quản lý truyền thống này để biến một HMS thông thường thành một **AI-Powered HMS** (SmartStay AI), nơi trợ lý AI tự động trò chuyện, gợi ý phòng dựa trên dữ liệu phòng trống thực tế của hệ thống.