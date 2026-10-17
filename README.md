# Fitness Menu Recommendation 🍱💪

> Đồ án Sinh viên Khoa Công nghệ Thông tin  
> Hệ thống gợi ý thực đơn dinh dưỡng cá nhân hóa dựa trên mục tiêu sức khỏe, chỉ số cơ thể và mức độ vận động.

Dự án này xây dựng một ứng dụng web giúp người dùng nhập thông tin cá nhân như độ tuổi, cân nặng, chiều cao, giới tính, mức độ vận động và mục tiêu tập luyện, sau đó đề xuất các bữa ăn phù hợp nhờ mô hình K-Nearest Neighbors (KNN). Ứng dụng hỗ trợ người dùng lựa chọn thực đơn theo nhu cầu giảm mỡ, tăng cơ hoặc duy trì cân nặng.

---

## 1. Tổng quan dự án

Fitness Menu Recommendation là một hệ thống web ứng dụng trong lĩnh vực sức khỏe và dinh dưỡng, tập trung vào việc:

- Tính toán nhu cầu năng lượng hàng ngày dựa trên BMR và TDEE
- Gợi ý các thực đơn phù hợp với mục tiêu tập luyện
- Hạn chế các nguyên liệu gây dị ứng như thịt heo, bò, hải sản, đậu phộng
- Hiển thị danh sách thực đơn theo từng bữa: sáng, trưa, tối
- Tổng hợp tổng lượng calo, protein, carb và chất béo của một ngày

Mô hình đề xuất sử dụng dữ liệu thực phẩm và cách tính toán khoảng cách KNN để tìm ra những thực đơn có đặc tính dinh dưỡng gần nhất với mục tiêu người dùng.

---

## 2. Tính năng chính

- Nhập thông tin cá nhân: tuổi, chiều cao, cân nặng, giới tính
- Chọn mức độ vận động: ít vận động, nhẹ, vừa, nhiều
- Chọn mục tiêu: tăng cơ, giảm mỡ, giữ cân
- Chọn loại dị ứng nếu có: không ăn thịt lợn, bò, hải sản, đậu phộng
- Gợi ý tối đa 5 thực đơn phù hợp
- Chọn khẩu phần cho từng bữa ăn trong ngày
- Hiển thị kết quả tổng hợp dinh dưỡng theo ngày
- Giao diện web thân thiện và dễ sử dụng

---

## 3. Công nghệ sử dụng

- Python
- Flask
- HTML/CSS/JavaScript
- Pandas
- SQLite
- Scikit-learn (KNN)
- NumPy

---

## 4. Cấu trúc thư mục dự án

```text
fitness-menu-recommendation/
├── README.md
├── docs/
│   └── baocaoDSS.docx
├── slides/
├── source/
│   ├── app.py
│   ├── database.py
│   ├── evaluation.py
│   ├── knn_model.py
│   ├── requirements.txt
│   ├── .gitignore
│   ├── data/
│   │   ├── DataDSS_labeled.csv
│   │   ├── DataDSS_labeled.xls
│   │   ├── fitness_menus.db
│   │   └── VTN_FCT_2007.pdf
│   ├── static/
│   └── templates/
│       ├── index.html
│       ├── meals.html
│       └── result.html
└──
```

---

## 5. Quy trình hoạt động

1. Người dùng nhập dữ liệu cá nhân và mục tiêu dinh dưỡng.
2. Hệ thống tính toán mục tiêu calo, protein, carb và chất béo dựa trên BMR và TDEE.
3. Ứng dụng lọc dữ liệu thực đơn theo các tiêu chí dị ứng và giới hạn dinh dưỡng.
4. Mô hình KNN tìm kiếm các thực đơn có đặc tính gần nhất với mục tiêu người dùng.
5. Người dùng chọn thực đơn cho bữa sáng, trưa và tối.
6. Hệ thống tổng hợp lượng dinh dưỡng của cả ngày và hiển thị kết quả.

---

## 6. Hướng dẫn cài đặt và chạy trên Windows

### 6.1. Yêu cầu

- Python 3.10+ hoặc 3.11+
- Git
- Trình duyệt web (Chrome, Edge, Firefox)

### 6.2. Clone dự án

```bash
git clone https://github.com/pvb-05/fitness-menu-recommendation.git
cd fitness-menu-recommendation
```

### 6.3. Tạo môi trường ảo

```bash
cd source
python -m venv venv
venv\Scripts\activate
```

### 6.4. Cài đặt thư viện

```bash
pip install -r requirements.txt
```

### 6.5. Khởi tạo database thực đơn (nếu cần)

Nếu bạn muốn tạo lại file SQLite chứa dữ liệu thực đơn:

```bash
python database.py
```

### 6.6. Chạy ứng dụng

```bash
python app.py
```

Sau khi chạy, mở trình duyệt và truy cập:

```text
http://127.0.0.1:5000/
```

---

## 7. Dữ liệu sử dụng

Dự án sử dụng bộ dữ liệu thực phẩm có tên:

- `source/data/DataDSS_labeled.csv`

Bộ dữ liệu này chứa các thông tin về:

- Tên thực phẩm
- Nhóm thực phẩm
- Hàm lượng calo
- Protein
- Carb
- Chất béo
- Phân loại nhóm dinh dưỡng

Ngoài ra, dự án còn có file SQLite `fitness_menus.db` được dùng để lưu trữ các thực đơn đã được tạo ra để phục vụ truy vấn nhanh trong quá trình gợi ý.

---

## 8. Một số lưu ý

- Nếu gặp lỗi khi khởi động, hãy kiểm tra lại phiên bản Python và cài đặt đầy đủ các package trong `requirements.txt`.
- Nếu dữ liệu SQLite không tồn tại hoặc đã lỗi, hãy chạy lệnh `python database.py` để tạo lại.
- Mô hình là một bản prototype phục vụ mục đích học tập và demo, nên vẫn có thể tiếp tục cải tiến về độ chính xác và trải nghiệm người dùng.

---

## 9. Ứng dụng có thể mở rộng

Dự án này có thể được nâng cấp bằng các tính năng như:

- Hỗ trợ đăng nhập người dùng
- Lưu lịch sử thực đơn cá nhân
- Tích hợp API dinh dưỡng thực tế
- Hỗ trợ thay đổi khẩu phần theo thể trạng và bệnh lý
- Tạo giao diện mobile hoặc ReactJS
- So sánh các thực đơn khác nhau theo tỷ lệ dinh dưỡng

---

## 10. Liên hệ

Tác giả: Bac Phan  
Email: phanvanbac15112005@gmail.com

Nếu bạn muốn đóng góp hoặc cải thiện dự án, hãy liên hệ qua email trên để trao đổi và hợp tác.
