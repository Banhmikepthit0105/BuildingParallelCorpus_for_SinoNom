# AutoBuilding Parallel Corpus for SinoNôm/Chinese OCR

![Banner](https://img.shields.io/badge/Project-AutoBuilding_Parallel_Corpus-blueviolet) ![License](https://img.shields.io/badge/License-MIT-green) ![Python](https://img.shields.io/badge/Python-3.8+-yellow)

## Giới thiệu

**AutoBuilding Parallel Corpus for SinoNôm/Chinese OCR** 
Dự án nhằm tự động hóa việc xây dựng tập dữ liệu song song (parallel corpus) cho nhận diện ký tự quang học (OCR) của văn bản Hán Nôm và tiếng Trung. Dự án tận dụng kỹ thuật thu thập dữ liệu từ web, xử lý hình ảnh, và căn chỉnh văn bản để tạo ra một tập dữ liệu chất lượng cao, phục vụ cho việc huấn luyện các mô hình OCR.

Dự án tập trung vào việc xử lý văn bản từ tác phẩm **Tây Du Ký** (Journey to the West), một tiểu thuyết cổ điển nổi tiếng, bằng cách:
- Thu thập hình ảnh từ file PDF hoặc dữ liệu trực tuyến.
- Trích xuất văn bản gốc từ web.
- Căn chỉnh văn bản OCR với văn bản gốc để tạo tập dữ liệu song song.

---

## Mục tiêu

- **Tự động hóa**: Giảm thiểu công sức thủ công trong việc xây dựng tập dữ liệu OCR.
- **Chất lượng cao**: Đảm bảo độ chính xác trong việc căn chỉnh văn bản OCR và văn bản gốc.
- **Hỗ trợ nghiên cứu**: Cung cấp tài nguyên cho các nhà nghiên cứu và kỹ sư trong lĩnh vực xử lý ngôn ngữ tự nhiên (NLP) và thị giác máy tính.

---

## Tính năng chính

1. **Thu thập dữ liệu**:
   - Trích xuất hình ảnh từ file PDF (`extract_pdf.py`).
   - Thu thập văn bản gốc từ trang web (`extract_text_from_web.py`).
2. **Xử lý hình ảnh**:
   - Tăng cường chất lượng ảnh để cải thiện hiệu suất OCR (`extract_pdf.py`).
   - Sử dụng API OCR để trích xuất văn bản từ ảnh (`extract_multiple.py`).
3. **Căn chỉnh văn bản**:
   - Sử dụng thuật toán căn chỉnh để so khớp văn bản OCR với văn bản gốc (`align_boxes.py`, `alignment_process.py`).
4. **Xuất kết quả**:
   - Lưu kết quả dưới dạng JSON và CSV (`align_boxes.py`).
   - Xuất file Excel với định dạng màu sắc để dễ dàng phân tích (`write_output.py`).

---

## Hướng dẫn cài đặt

### Yêu cầu
- Python 3.8 trở lên
- Các thư viện cần thiết:
  pip install requests beautifulsoup4 pandas opencc-python-reimplemented rapidfuzz opencv-python pillow fitz xlsxwriter



Các bước thực hiện
1. Clone repository:


2. Cài đặt thư viện:

3. Chuẩn bị dữ liệu:

Đặt file PDF (ví dụ: TayDuKy.pdf) vào thư mục gốc.

Đảm bảo có file từ điển Hán Nôm (SinoNom_similar_Dic.xlsx) trong thư mục gốc.

4. Chạy pipeline:

Trích xuất hình ảnh từ PDF: python extract_pdf.py
Thu thập văn bản từ web: python extract_text_from_web.py
Chạy OCR trên hình ảnh: python extract_multiple.py
Căn chỉnh văn bản: + python align_boxes.py
                   + python alignment_process.py
Xuất kết quả: python write_output.py





### Ví dụ kết quả

| Image_name          | ID              | Image Box                  | Text OCR | Text Char |
|---------------------|------------------|-----------------------------|----------|-----------|
| TayDuKy_page048.png | TayDuKy.048.001  | [(10, 20), (50, 20), ...]   | 玉帝聞言     | 玉帝聞言      |

- **Text OCR**: Văn bản trích xuất từ OCR.  
- **Text Char**: Văn bản gốc đã căn chỉnh.

---

## Đóng góp

Dự án được phát triển bởi:

- **Nguyen Thanh Thai (Team Leader)**: Căn chỉnh bounding box (`align_boxes.py`), thu thập dữ liệu web (`extract_text_from_web.py`).
- **Dang Thanh Tu**: Xử lý hình ảnh và OCR (`extract_pdf.py`, `extract_multiple.py`, `extract_zip.py`).
- **Vo Thinh Vuong**: Xử lý bounding box (`BBox.py`).
- **Le Phuoc Phat**: Căn chỉnh ký tự (`alignment_process.py`), xuất kết quả (`write_output.py`).
