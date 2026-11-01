# Đồ án Nhập môn Khoa học Dữ liệu — Thu thập và Xử lý Dữ liệu arXiv

Chào mừng bạn đến với tài liệu kỹ thuật chính thức của đồ án **Thu thập, Bóc tách và Đối sánh Dữ liệu arXiv** thuộc môn học **Nhập môn Khoa học Dữ liệu** tại Trường Đại học Khoa học Tự nhiên, ĐHQG-HCM (HCMUS).

---

## 1. Tổng quan Đồ án

Đồ án tập trung vào việc nghiên cứu, thiết kế và hiện thực hóa một quy trình (pipeline) hoàn chỉnh, có khả năng tái lập cao nhằm thu thập, chuẩn hóa và liên kết dữ liệu bài báo khoa học từ các nguồn học thuật hàng đầu thế giới: **arXiv**, **OAI-PMH**, và **Semantic Scholar**.

Quy trình được chia thành 3 giai đoạn chính:

1. **Giai đoạn 1 — Thu thập Dữ liệu và Đo lường Hiệu năng:**
   - Thu thập có kiểm soát siêu dữ liệu (metadata) và mã nguồn TeX từ arXiv (tuân thủ nghiêm ngặt giới hạn tốc độ $\\ge 3).
   - Khai thác đồ thị trích dẫn từ Semantic Scholar API.
   - Xây dựng hạ tầng đo lường hiệu năng hệ thống (Thời gian thực thi, Bộ nhớ đỉnh, Bộ nhớ trung bình, Dung lượng đĩa) và phát hành tài liệu tương tác qua Jupyter Book.
2. **Giai đoạn 2 — Bóc tách Cấu trúc Tài liệu và Chuẩn hóa Dữ liệu (Sắp triển khai):**
   - Phân tích cú pháp mã nguồn TeX (.tex, .bib), bóc tách cấu trúc tài liệu (Tiêu đề, Tóm tắt, Các đề mục, Công thức toán học, Danh mục trích dẫn).
   - Chuẩn hóa dữ liệu theo cấu trúc hợp nhất của đồ án.
3. **Giai đoạn 3 — Đối sánh Bài báo và Mạng lưới Trích dẫn:**
   - Xây dựng giải thuật đối sánh bài báo giữa các nguồn dữ liệu khác nhau.
   - Tái lập đồ thị mạng lưới trích dẫn khoa học.

---

## 2. Thông tin Nhóm Thực hiện (Nhóm 04)

| MSSV | Họ và tên | Trách nhiệm chính trong đồ án | Phân hệ phụ trách |
|---|---|---|---|
| **24120053** | Đặng Ngọc Hoàng | Nhóm trưởng, Điều phối quy trình và Thu thập siêu dữ liệu | Phân hệ A3 (OAI-PMH và Đối sánh Kaggle) |
| **24120144** | Dương Ngọc Minh Thư | Tải toàn văn mã nguồn bài báo | Phân hệ A1 (Tối ưu hóa luồng tải streaming) |
| **24120152** | Trần Ngọc Thanh Tú | Trích xuất và Tối ưu kho lưu trữ mã nguồn | Phân hệ A2 (Bộ kiểm định chất lượng dữ liệu) |
| **24120177** | Cáp Hửu Duy | Thu thập dữ liệu trích dẫn Semantic Scholar | Phân hệ C (Tiền xử lý TeX và Khảo sát hạn chế) |
| **24120153** | Nguyễn Lê Anh Tuấn | Đo lường hiệu năng và Hạ tầng Báo cáo Jupyter Book | Phân hệ B (Đo lường bộ nhớ đỉnh Kernel và Thống kê) |

---

## 3. Cấu trúc Tài liệu Báo cáo

Tài liệu được biên soạn dưới dạng sách tương tác (Jupyter Book), kết hợp giữa cơ sở lý thuyết kỹ thuật và mã nguồn phân tích thực tế:

- **Giai đoạn 1 — Thu thập Dữ liệu:**
  - [01. Phương pháp thu thập dữ liệu](milestone1/01-methodology.ipynb): Khảo sát chi tiết 4 nguồn dữ liệu (arXiv API, OAI-PMH, Kaggle, Semantic Scholar), phân tích giới hạn tốc độ (rate limits), giải thuật retry với exponential backoff, và quy tắc chuẩn hóa schema.
  - [02. Báo cáo thống kê dữ liệu thực nghiệm](milestone1/02-statistics.ipynb): Báo cáo thực nghiệm phân tích 4 chỉ số tài nguyên (Thời gian, Bộ nhớ đỉnh, Bộ nhớ trung bình, Dung lượng đĩa) và đối sánh chéo 10.000 bài báo.
  - [03. Phân tích hiệu năng chuyên sâu và kiểm định](milestone1/03-performance.ipynb): Phân tích sai lệch đo lường RAM nhân hệ điều hành (getrusage) so với lấy mẫu (psutil), tối ưu tải streaming, phân rã thời gian chờ pacing, kết quả bộ kiểm định chất lượng và tiền xử lý cấu trúc TeX.
- **Giai đoạn 2 — Bóc tách Dữ liệu:**
  - [Dành riêng cho Giai đoạn 2](milestone2/reserved.md): Phân hệ bóc tách mã nguồn TeX và chuẩn hóa dữ liệu (sẽ được cập nhật khi bắt đầu giai đoạn 2).

---

## 4. Hệ thống Lưu trữ Mã nguồn

Dự án duy trì hai kho lưu trữ tách biệt theo nguyên tắc phân tách trách nhiệm:
- **Kho lưu trữ Mã nguồn (Code Repository):** Chứa mã nguồn pipeline, công cụ benchmark, script thu thập và kiểm thử tự động.
- **Kho lưu trữ Tài liệu (Documentation Repository):** Chứa toàn bộ cấu hình Jupyter Book, notebook phương pháp, thống kê thực nghiệm và GitHub Actions tự động xuất bản lên GitHub Pages.
