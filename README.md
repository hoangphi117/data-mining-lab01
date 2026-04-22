## CSC14004 - Đồ án 01: Tiền xử lý dữ liệu

### 1) Thông tin nhóm

| STT | MSSV | Họ và tên |
|:---:|:---:|:---:|
| 1 | 23120272 | Lê Quốc Huy |
| 2 | 23120315 | Nguyễn Đăng Pha |
| 3 | 23120320 | Nguyễn Hoàng Phi |
| 4 | 23120339 | Nguyễn Minh Quân |

### 2) Mô tả tập dữ liệu

#### 2.1) Dữ liệu ảnh: NIH Chest X-ray
##### Hướng dẫn cài đặt
**Nguồn dữ liệu:** [NIH Chest X-rays on Kaggle](https://www.kaggle.com/datasets/nih-chest-xrays/data)
Tải về các file sau:
- [Data_Entry_2017.csv](https://www.kaggle.com/datasets/nih-chest-xrays/data?select=Data_Entry_2017.csv)
- [images_001](https://www.kaggle.com/datasets/nih-chest-xrays/data?select=images_001),  [images_002](https://www.kaggle.com/datasets/nih-chest-xrays/data?select=images_002), [images_003](https://www.kaggle.com/datasets/nih-chest-xrays/data?select=images_003)

Sau khi giải nén, đặt file vào đúng thư mục:

```
data/raw/
├── Data_Entry_2017.csv     ← đặt trực tiếp vào đây
└── images/
    ├── 00000001_000.png
    ├── 00000001_001.png
    └── ...                 ← toàn bộ ảnh .png đặt thẳng trong thư mục này
```

**Mô tả bộ dữ liệu**

Bộ dữ liệu **NIH Chest X-rays** là tập dữ liệu ảnh y khoa quy mô lớn gồm **112.120 ảnh X-quang ngực** từ **30.805 bệnh nhân**, dùng cho bài toán phát hiện bệnh từ ảnh y tế. Dữ liệu bao gồm ảnh X-ray kích thước 1024×1024 và file nhãn `Data_Entry_2017.csv` chứa thông tin bệnh, nhân khẩu học và đặc trưng ảnh. :contentReference[oaicite:0]{index=0}

Dataset hỗ trợ bài toán **multi-label classification**, trong đó mỗi ảnh có thể thuộc một hoặc nhiều trong **14 bệnh lồng ngực** (ví dụ: Atelectasis, Effusion, Pneumonia, Pneumothorax) hoặc lớp **No Finding**.

Ngoài ra, dữ liệu còn có file **BBox_list_2017.csv** chứa bounding box cho một số bất thường, hỗ trợ các bài toán **detection** và **localization**. Bộ dữ liệu phù hợp cho nghiên cứu deep learning trong chẩn đoán hình ảnh y khoa.

#### 2.2) Dữ liệu bảng: Student Placement Prediction

**Hướng dẫn cài đặt**

**Nguồn dữ liệu:** [Student Placement Prediction](https://www.kaggle.com/datasets/suhanigupta04/student-placement-prediction-dataset)
Tải về file: [student_placement_synthetic.csv](https://www.kaggle.com/datasets/suhanigupta04/student-placement-prediction-dataset?select=student_placement_synthetic.csv)

Sau khi tải về, đặt file vào đúng thư mục:

```
data/raw/
├── student_placement_raw.csv     ← đặt trực tiếp vào đây
```
**Mô tả bộ dữ liệu**

Bộ dữ liệu **Student Placement Prediction Dataset** là tập dữ liệu tổng hợp (synthetic) gồm **100.000 mẫu** với **18 thuộc tính**, dùng để dự đoán khả năng sinh viên được tuyển dụng. Dữ liệu bao gồm các đặc trưng về học tập (CGPA, backlogs, college tier), kỹ năng (coding, DSA, aptitude, communication), kinh nghiệm (internships, projects, certifications) và hoạt động ngoại khóa.

Dataset có hai biến mục tiêu:
- `placement_status`: dự đoán sinh viên có được tuyển dụng hay không (bài toán phân loại).
- `salary_package_lpa`: dự đoán mức lương đề xuất nếu được tuyển (bài toán hồi quy).

Bộ dữ liệu phù hợp cho các bài toán classification, regression và thực hành machine learning.

#### 2.3) Dữ liệu văn bản: fake-and-real-news

**Hướng dẫn cài đặt**

**Nguồn dữ liệu:** [fake-and-real-news](https://www.kaggle.com/datasets/clmentbisaillon/fake-and-real-news-dataset/data)

Tải về các file:
- [Fake.csv](https://www.kaggle.com/datasets/clmentbisaillon/fake-and-real-news-dataset/data?select=Fake.csv)
- [True.csv](https://www.kaggle.com/datasets/clmentbisaillon/fake-and-real-news-dataset/data?select=True.csv)

Sau khi tải về, đặt file vào đúng thư mục
```
data/raw/
├── Fake.csv
└── True.csv
```

**Mô tả bộ dữ liệu**

Bộ dữ liệu **Fake and Real News Dataset** gồm **44.919 bài báo**, bao gồm **23.502 tin giả (Fake.csv)** và **21.417 tin thật (True.csv)**, được sử dụng cho bài toán phát hiện tin giả (*fake news detection*). Mỗi mẫu dữ liệu là một bài báo với các thuộc tính: `title` (tiêu đề), `text` (nội dung), `subject` (chủ đề) và `date` (ngày đăng). :contentReference[oaicite:0]{index=0}

Dataset hỗ trợ bài toán **binary text classification**, với nhãn phân loại:
- Fake: tin giả
- True: tin thật

Bộ dữ liệu phù hợp cho các bài toán NLP như phân loại văn bản, phát hiện tin giả, phân tích đặc trưng ngôn ngữ và huấn luyện mô hình machine learning/deep learning.
### 3) Cấu trúc thư mục chính
```
data-mining-lab01/
├── data/
│   ├── raw/
│   │   ├── student_placement_raw.csv
│   │   ├── Data_Entry_2017.csv (tự tải)
│   │   ├── images/ (tự tải)
│   │   ├── Fake.csv
│   │   └── True.csv
│   └── processed/
├── notebooks/
│   ├── 01_EDA_image.ipynb
│   ├── 02_EDA_tabular.ipynb
│   └── 05_text_preprocessing.ipynb
├── requirements.txt
└── README.md
```
### 4) Hướng dẫn cài đặt môi trường và chạy notebook

#### 4.1) Yêu cầu

- Python 3.10+ (khuyến nghị 3.10 hoặc 3.11)
- VS Code + Jupyter extension

#### 4.2) Cài môi trường (Windows PowerShell)

```powershell
cd d:\data-mining-lab01
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install --upgrade pip
pip install -r requirements.txt
```

#### 4.3) Chạy notebook

```powershell
cd d:\data-mining-lab01
.\.venv\Scripts\Activate.ps1
jupyter notebook
```

Sau đó mở lần lượt:
- `notebooks/01_EDA_image.ipynb`
- `notebooks/02_EDA_tabular.ipynb`
- `notebooks/05_text_preprocessing.ipynb`

Khuyến nghị chạy từ trên xuống dưới theo thứ tự cell.

### 5) Bảng phân công công việc

| Họ và tên | MSSV | Nội dung đóng góp | Sản phẩm đầu ra |
|---|---|---|---|
| Lê Quốc Huy | 23120272 | Thực hiện 2.2 - Tiền xử lý dữ liệu dạng bảng, viết báo cáo| `02_EDA_tabular.ipynb` |
| Nguyễn Đăng Pha | 23120315 | Thực hiện 2.3 - Tiền xử lý dữ liệu văn bản, viết báo cáo | `05_text_preprocessing.ipynb` |
| Nguyễn Hoàng Phi | 23120320 | Thực hiện 2.1 – Tiền xử lý ảnh, viết báo cáo | `01_EDA_image.ipynb` |
| Nguyễn Minh Quân | 23120339 | Thực hiện 2.2 - Tiền xử lý dữ liệu dạng bảng, viết báo cáo| `02_EDA_tabular.ipynb`|

### 6) Link tài nguyên ngoài
#### Dữ liệu sau xử lí:

