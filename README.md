# viet_summarizer

## Giới thiệu
Dự án **viet_summarizer** xây dựng mô hình tóm tắt văn bản tiếng Việt dựa trên phương pháp trích xuất (extraction-based) với 3 mô hình chính:
- **Clustering (KMeans)**
- **TextRank** (ý tưởng cơ bản giống với pagerank)
- **LSA** (Latent Semantic Analysis)

Ứng dụng chạy trên nền web sử dụng [Streamlit](https://streamlit.io/), giúp người dùng dễ dàng tóm tắt văn bản tiếng Việt qua giao diện trực quan.

Luồng xử lý : https://www.mermaidchart.com/raw/e194e709-83e6-41b8-89d5-d0c3c779c6ad?theme=light&version=v0.1&format=svg

## Cách chạy ứng dụng
1. **Cài đặt các thư viện cần thiết:**
   - numpy, pandas, matplotlib
   - scikit-learn (sklearn)
   - nltk
   - gensim
   - pyvi
   - networkx
   - streamlit

   Bạn có thể cài đặt nhanh qua lệnh:
   ```sh
   pip install numpy pandas matplotlib scikit-learn nltk gensim pyvi networkx streamlit
   ```

2. **Chuẩn bị vector từ (word embeddings):**
   - Tải file vector từ trang [fastText Vietnamese pre-trained vectors](https://fasttext.cc/docs/en/crawl-vectors.html) (chọn **cc.vi.300.vec.gz**).
   - Để tăng tốc độ xử lý, bạn nên giảm chiều vector từ 300 xuống 100 chiều. Có thể sử dụng notebook Kaggle tại đây: [Giảm chiều vectors xuống 100D](https://www.kaggle.com/code/thonghutin/gi-m-chi-u/output).
   - Sau khi giảm chiều, lưu file vector 100D vào thư mục phù hợp (ví dụ: `data/cc.vi.100.vec`).

3. **Chạy ứng dụng:**
   - Mở terminal, di chuyển vào thư mục chứa file `main.py` (thường là `src/main.py`):
     ```sh
     cd src
     ```
   - Chạy ứng dụng với lệnh:
     ```sh
     streamlit run main.py
     ```

4. **Truy cập giao diện web:**  
   Mở trình duyệt và vào địa chỉ được streamlit cung cấp (thường là http://localhost:8501).

## Các mô hình tóm tắt
- **KMeans Clustering:** Nhóm các câu theo đặc trưng nội dung, chọn câu đại diện cho mỗi cụm.
- **TextRank:** Tính điểm quan trọng của từng câu dựa trên mối liên hệ với các câu khác trong văn bản (ý tưởng tương tự PageRank).
- **LSA:** Phân tích ngữ nghĩa tiềm ẩn để xác định các câu quan trọng.

## Tham khảo
- [fastText Pre-trained Vectors for Vietnamese](https://fasttext.cc/docs/en/crawl-vectors.html)
- [Notebook giảm chiều vector trên Kaggle](https://www.kaggle.com/code/thonghutin/gi-m-chi-u/output)
- [Hướng dẫn cài đặt Streamlit](https://docs.streamlit.io/library/get-started/installation)

---

**Lưu ý:**  
- Đảm bảo đã tải và chuyển đổi vector từ (word embeddings) sang 100 chiều trước khi chạy mô hình để đạt hiệu suất tốt nhất.
- Chi tiết các bước xử lý, giải thích mô hình và hướng dẫn cụ thể hơn có thể tham khảo thêm trong file `report`.
