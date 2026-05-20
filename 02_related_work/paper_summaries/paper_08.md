# Paper 08 Summary

## Citation

* **Tên bài:** Boundary-Aware Texture Region Segmentation for Manga Digitization
* **Tác giả:** Minshan Xie, Tien-Tsin Wong
* **Năm:** 2016
* **Nguồn:** Computational Visual Media (Springer)
* **DOI/Link:** https://doi.org/10.1007/s41095-016-0069-x

## Problem

* Khi số hóa truyện tranh (Manga Digitization) để hiển thị trên màn hình kỹ thuật số, các vùng dán **screentone (kết cấu trame chấm bi/kẻ sọc)** có tần số cao thường gây ra hiện tượng **nhiễu sọc Moiré** rất nhức mắt cho người đọc.
* Các phương pháp phân vùng kết cấu truyền thống khi cố gắng tách hoặc làm mịn lớp trame này thường làm **lẹm, mờ hoặc đứt gãy các đường nét vẽ cấu trúc (line art)** của nhân vật và khung truyện, do kết cấu trame nằm sát rạt hoặc đè lên các đường biên này.

## Method

* Bài báo đề xuất thuật toán phân vùng kết cấu nhận thức ranh giới (**Boundary-Aware Texture Region Segmentation**).
* Thuật toán sử dụng các đặc trưng hình học thấp (low-level vision features) để tự động bóc tách một trang manga thành 3 lớp (layers) độc lập:
  1. **Nét vẽ cấu trúc (Structure/Lines):** Các nét mực liền mạch, chạy dài tạo khung và hình dáng (ví dụ: viền nhân vật, viền bong bóng thoại).
  2. **Vùng kết cấu (Texture/Screentones):** Các mảng chấm, sọc luân phiên có tần số cao (ví dụ: họa tiết áo, bầu trời, bóng râm).
  3. **Vùng trơn (Solid regions):** Các mảng trắng tinh (nền giấy, lòng bong bóng thoại) hoặc đen đặc (tóc, bóng tối bệt).
* Thuật toán tích hợp một cơ chế **nhận thức ranh giới (Boundary-Aware)** giúp lần theo sự liên kết liên tục của pixel đen để bảo vệ các "sợi dây" nét vẽ cấu trúc không bị xóa nhầm trong quá trình tách lọc kết cấu trame xung quanh.

## Dataset

* Bài báo sử dụng tập dữ liệu gồm các trang truyện Manga Nhật Bản truyền thống được scan với độ phân giải cao, bao gồm nhiều phong cách vẽ và các loại giấy dán trame (screentone) đa dạng từ chấm bi, kẻ sọc cho đến vân lưới (tương đương các bộ dữ liệu trích xuất từ Manga109).

## Evaluation

* **Độ chính xác phân vùng (Segmentation Accuracy):** Sử dụng các chỉ số toán học Precision, Recall và F-measure trên từng điểm ảnh (pixel-level) để đo hiệu quả tách biệt 3 lớp.
* **Chất lượng thị giác (Visual Quality):** Đánh giá định tính khả năng triệt tiêu nhiễu Moiré khi thực hiện thu phóng ảnh và độ sắc nét của nét vẽ sau khi lọc trame.

## Results

* Thuật toán bóc tách thành công lớp kết cấu trame phức tạp ra khỏi trang truyện mà vẫn giữ được đường viền nhân vật và khung tranh hoàn hảo, sắc nét, không bị răng cưa hay đứt đoạn.
* Triệt tiêu hoàn toàn hiện tượng nhiễu Moiré khi hiển thị manga trên các thiết bị di động, tạo tiền đề tốt cho các tác vụ xử lý đồ họa nâng cao.

## Limitations

* Do sử dụng các thuật toán tối ưu hóa toán học truyền thống dựa trên bộ lọc tần số vẽ tay (hand-crafted features), hệ thống yêu cầu cấu hình các ngưỡng thông số (thresholds) thủ công cho từng loại truyện.
* Gặp khó khăn hoặc giảm độ chính xác đối với các vùng kết cấu quá dị biệt, các mảng vẽ nghệ thuật phi quy luật, hoặc các phần chữ hiệu ứng (SFX) nghệ thuật nằm chồng chéo lên các mẫu trame.

## Relevance to our topic

* **Vị trí trong dự án:** Thuộc nhóm **Bài báo về AI và Mô hình (AI/model papers)**, đóng vai trò là khâu **Tiền xử lý dữ liệu ảnh (Image Preprocessing)**.
* **Mối liên hệ trực tiếp:** Bằng cách tách biệt hoàn toàn *Vùng trơn (Solid regions)* – nơi chứa lòng bong bóng thoại trắng tinh – và *Nét vẽ cấu trúc (Structure/Lines)* – nơi chứa đường viền bong bóng thoại – ra khỏi các vùng bối cảnh kết cấu (Texture), thuật toán này giúp làm sạch nhiễu nền. Qua đó, các mô hình AI cốt lõi của nhóm như **YOLO** (nhận diện khung) và **U-Net** (phân vùng bong bóng thoại/chữ) sẽ không bị bối rối bởi các chấm trame, giúp tăng tỷ lệ nhận diện chính xác bong bóng thoại lên rất cao.

## Possible improvement

* **Hướng cải tiến cho nhóm:** Thay vì sử dụng thuật toán tối ưu hóa toán học truyền thống của bài báo (đòi hỏi chỉnh thông số bằng tay), nhóm có thể **đưa tư duy chia 3 lớp (Structure - Texture - Solid) này vào một kiến trúc mạng học sâu (Deep Learning)** như CNN cải tiến hoặc U-Net/SegFormer.
* Việc huấn luyện một model AI học cách tự động phân tách 3 lớp này dựa trên dữ liệu lớn sẽ giúp hệ thống chạy hoàn toàn tự động, thích ứng được với mọi chất lượng ảnh scan (dù mờ hay rõ) mà không cần con người tinh chỉnh tham số cho từng tập truyện khác nhau.