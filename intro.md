# Đồ án Nhập môn Khoa học Dữ liệu — arXiv Crawling & Matching

Chào mừng bạn đến với tài liệu kỹ thuật chính thức của đồ án **arXiv Crawling, Parsing & Matching** thuộc môn học **Nhập môn Khoa học Dữ liệu (Introduction to Data Science)** tại Trường Đại học Khoa học Tự nhiên, ĐHQG-HCM (HCMUS).

---

## 1. Tổng quan đồ án

Đồ án tập trung vào việc nghiên cứu, thiết kế và hiện thực hóa một quy trình (pipeline) hoàn chỉnh, có khả năng tái lập cao nhằm thu thập, chuẩn hóa và liên kết dữ liệu bài báo khoa học từ các nguồn học thuật hàng đầu thế giới: **arXiv**, **OAI-PMH**, và **Semantic Scholar**.

Quy trình được chia thành 3 giai đoạn chính (Milestones):

1. **Milestone 1 — Data Crawling & Performance Benchmarking:**
   - Thu thập có kiểm soát metadata và source TeX từ arXiv (tuân thủ nghiêm ngặt pacing rate limit $\ge 3$s).
   - Khai thác đồ thị trích dẫn từ Semantic Scholar API.
   - Xây dựng hạ tầng đo lường hiệu năng hệ thống (Wall-clock time, Peak RAM, Average RAM, Disk usage) và phát hành tài liệu tương tác qua Jupyter Book.
2. **Milestone 2 — Document Parsing & Schema Normalization (Dành sẵn / Upcoming):**
   - Phân tích cú pháp source TeX (`.tex`, `.bib`), bóc tách cấu trúc tài liệu (Title, Abstract, Section headings, Mathematical equations, Citations).
   - Chuẩn hóa dữ liệu theo schema dữ liệu hợp nhất.
3. **Milestone 3 — Publication & Citation Matching:**
   - Xây dựng giải thuật đối sánh bài báo giữa các nguồn dữ liệu khác nhau.
   - Tái lập đồ thị mạng lưới trích dẫn khoa học.

---

## 2. Thông tin nhóm thực hiện (Group 04)

| MSSV | Họ và tên | Trách nhiệm chính trong đồ án | Phân hệ phụ trách |
|---|---|---|---|
| **24120053** | Nguyễn Ngọc Hoàng | Nhóm trưởng, Entry Discovery & Pipeline Integration | Module A3 (OAI-PMH & Kaggle Validation) |
| **24120144** | Nguyễn Minh Thư | Full-text Source Download | Module A1 (Tối ưu hiệu năng tải) |
| **24120152** | Trần Thanh Tú | Extraction & Corpus Builder | Module A2 (Data Validation Suite) |
| **24120177** | Bùi Hữu Duy | Semantic Scholar Reference Crawling | Module C (Tiền xử lý bắc cầu M2/M3) |
| **24120153** | Đặng Anh Tuấn | Performance Benchmarking & Jupyter Book Documentation | Module B (Phân tích thực nghiệm mở rộng) |

---

## 3. Cấu trúc tài liệu

Tài liệu được biên soạn dưới dạng sách tương tác (Jupyter Book), kết hợp giữa lý thuyết toán học/kỹ thuật và mã nguồn phân tích thực tế:

- **Milestone 1 — Crawling:**
  - [01. Phương pháp thu thập dữ liệu (Methodology)](milestone1/01-methodology.ipynb): Khảo sát chi tiết 4 nguồn dữ liệu (arXiv API, OAI-PMH, Kaggle, Semantic Scholar), phân tích giới hạn tốc độ (rate limits), giải thuật retry với exponential backoff, và quy tắc chuẩn hóa schema.
  - [02. Thống kê & Phân tích hiệu năng (Statistics)](milestone1/02-statistics.ipynb): Báo cáo thực nghiệm phân tích 4 chỉ số tài nguyên (Wall-clock time, Peak RAM, Average RAM, Disk usage) dựa trên schema benchmark thống nhất của nhóm.
- **Milestone 2 — Parsing:**
  - [Reserved for Milestone 2](milestone2/reserved.md): Phân hệ bóc tách source TeX và chuẩn hóa dữ liệu (sẽ được cập nhật khi giai đoạn 2 bắt đầu).

---

## 4. Hệ thống Repository

Dự án duy trì hai repository tách biệt theo nguyên tắc phân tách trách nhiệm:
- **Code Repository:** Chứa mã nguồn pipeline, công cụ benchmark, script thu thập và kiểm thử tự động.
- **Documentation Repository:** Chứa toàn bộ cấu hình Jupyter Book, notebook phương pháp, thống kê thực nghiệm và GitHub Actions tự động deploy lên GitHub Pages.
