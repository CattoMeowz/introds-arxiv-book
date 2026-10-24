# Documentation Repository — HCMUS IntroDS (arXiv Project)

Repository riêng biệt chứa tài liệu dự án và website báo cáo xây dựng bằng **Jupyter Book**, tự động build và deploy lên **GitHub Pages**.

## 1. Cấu trúc

```text
├── .github/workflows/
│   └── deploy-book.yml     # Workflow GitHub Actions deploy Pages
├── _config.yml             # Cấu hình Jupyter Book
├── _toc.yml                # Mục lục sách
├── intro.md                # Trang giới thiệu
├── milestone1/
│   ├── 01-methodology.ipynb # Báo cáo phương pháp thu thập
│   └── 02-statistics.ipynb  # Báo cáo phân tích hiệu năng benchmark
├── milestone2/
│   └── reserved.md         # Dành sẵn cho Milestone 2
├── requirements.txt        # Thư viện build sách
└── README.md
```

## 2. Hướng dẫn Build Local

1. Cài đặt môi trường Python (>= 3.10 khuyến nghị):
   ```bash
   python -m venv .venv
   source .venv/bin/activate   # Windows: .venv\Scripts\activate
   pip install -r requirements.txt
   ```

2. Build sách HTML:
   ```bash
   jupyter-book build .
   ```

3. Mở xem kết quả trên trình duyệt:
   ```bash
   # Mở file: _build/html/index.html
   ```

## 3. Kích hoạt GitHub Pages

1. Tạo một repository mới trên GitHub (ví dụ: `introds-arxiv-book`).
2. Khởi tạo Git và push mã nguồn:
   ```bash
   git init
   git add .
   git commit -m "Initial commit of Jupyter Book documentation"
   git branch -M main
   git remote add origin https://github.com/<your-username>/introds-arxiv-book.git
   git push -u origin main
   ```
3. Trên giao diện GitHub của repository:
   - Vào **Settings** -> **Pages** (cột trái).
   - Tại mục **Build and deployment** -> **Source**, chọn **GitHub Actions**.
4. GitHub Actions sẽ tự động kích hoạt workflow `deploy-book` và xuất bản website.
