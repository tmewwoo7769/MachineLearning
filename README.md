<div align="center">

# Học máy ứng dụng — Bộ bài thực hành

**Trường Đại học Văn Lang · Khoa Công nghệ Thông tin**
Học phần: *Học máy ứng dụng* · Năm học 2026 – 2027

</div>

---

## Mục lục

1. [Giới thiệu](#-giới-thiệu)
2. [Mục tiêu học tập](#-mục-tiêu-học-tập)
3. [9 bài thực hành](#-lộ-trình-9-bài-thực-hành)
4. [Nội dung chi tiết từng bài](#-nội-dung-chi-tiết-từng-bài)
5. [Tổng hợp so sánh các mô hình](#-tổng-hợp-so-sánh-các-mô-hình)
6. [Những bài học xuyên suốt](#-những-bài-học-xuyên-suốt)
7. [Bài tập](#-bài-tập)
8. [Công nghệ sử dụng](#-công-nghệ-sử-dụng)
9. [Thông tin tác giả](#-thông-tin-tác-giả)

---

## Giới thiệu

Repository này lưu toàn bộ **mã nguồn, kết quả chạy và bài làm** của học phần **Học máy ứng dụng**, thực hiện theo bộ *Tài liệu thực hành* do **ThS. Nguyễn Thái Anh** biên soạn (Khoa Công nghệ Thông tin, Trường Đại học Văn Lang).

Học phần đi theo một mạch xuyên suốt: bắt đầu từ mô hình đơn giản nhất là **một đường thẳng** (hồi quy tuyến tính), rồi lần lượt mở rộng sang các mô hình **phân loại**, **phân cụm không nhãn** và cuối cùng là **mạng nơ-ron nhiều lớp**, nền móng của học sâu. Mỗi bài đều theo cùng một phương pháp:

> **Tự cài đặt bằng tay trước (NumPy) → đối chiếu với thư viện (scikit-learn) → đánh giá trung thực trên dữ liệu chưa từng thấy → rút ra bài học.**

Cách làm này nhằm một mục đích: người học không chỉ *gọi được hàm* mà còn **hiểu máy thật sự tính gì bên trong**.

### Điểm nổi bật

- **Tự viết thuật toán từ đầu** bằng NumPy: hồi quy tuyến tính (công thức và gradient descent), sigmoid, định lý Bayes, Naive Bayes, chỉ số Gini, KNN, K-Means, lan truyền tiến của mạng nơ-ron.
- **Kết quả có thể kiểm chứng**: mọi con số trong README đều lấy từ kết quả chạy thật của bộ tài liệu, tái lập được nhờ cố định `random_state`.
- **Đánh giá đúng cách**: luôn chia tập học / tập kiểm tra, dùng `stratify`, dùng `make_pipeline` để tránh rò rỉ dữ liệu, chọn siêu tham số bằng kiểm định chéo thay vì nhìn tập kiểm tra.
- **Nhấn mạnh các cái bẫy thực tế**: quên chuẩn hoá, accuracy đánh lừa trên dữ liệu lệch lớp, học vẹt, ngoại suy, khởi tạo xấu...

---

## Mục tiêu học tập

Sau khi hoàn thành 9 bài, người học có khả năng:

| # | Năng lực |
|---|----------|
| 1 | Phân biệt và áp dụng được bài toán **hồi quy**, **phân loại** và **phân cụm**. |
| 2 | Tự cài đặt các thuật toán cốt lõi bằng NumPy và đối chiếu với scikit-learn. |
| 3 | Đánh giá mô hình đúng chuẩn: tập học/kiểm tra, kiểm định chéo, MAE/RMSE/R², confusion matrix, precision/recall/F1, ROC/AUC. |
| 4 | Nhận diện **cẩu thả (underfitting)** và **học vẹt (overfitting)**, điều chỉnh bằng siêu tham số (k, độ sâu, C, gamma, alpha). |
| 5 | Biết khi nào **bắt buộc chuẩn hoá** dữ liệu và khi nào **không cần** (cây quyết định). |
| 6 | Chọn mô hình phù hợp với hình dạng dữ liệu thay vì chạy theo mô hình phức tạp nhất. |

---

## 9 bài thực hành

| Bài | Chủ đề | Loại bài toán | Bộ dữ liệu | Thư mục |
|:---:|--------|:-------------:|------------|---------|
| 1 | [Hồi quy tuyến tính](#bài-1--hồi-quy-tuyến-tính) | Hồi quy | `gia_nha.csv` (60 căn hộ) | `bai01_hoi_quy` |
| 2 | [Hồi quy logistic](#bài-2--hồi-quy-logistic) | Phân loại | `sinh_vien.csv` (120 sinh viên) | `bai02_hoi_quy_logistic` |
| 3 | [Naive Bayes](#bài-3--naive-bayes) | Phân loại | `tin_nhan.csv` (300 tin nhắn) | `bai03_naive_bayes` |
| 4 | [K láng giềng gần nhất (KNN)](#bài-4--k-láng-giềng-gần-nhất-knn) | Phân loại + Hồi quy | `sinh_vien_mo_rong.csv`, `hai_vang_trang.csv` | `bai04_knn` |
| 5 | [Cây quyết định & Rừng ngẫu nhiên](#bài-5--cây-quyết-định-và-rừng-ngẫu-nhiên) | Phân loại + Hồi quy | `khach_vay.csv` (600 hồ sơ) | `bai05_cay` |
| 6 | [Máy vectơ hỗ trợ (SVM)](#bài-6--máy-vectơ-hỗ-trợ-svm) | Phân loại | `hai_vang_trang.csv`, `load_digits` | `bai06_svm` |
| 7 | [Đánh giá mô hình](#bài-7--đánh-giá-mô-hình) | Phân loại (dữ liệu lệch lớp) | `sinh_vien_bo_hoc.csv` (1200 sinh viên) | `bai07_danh_gia` |
| 8 | [Phân cụm K-Means](#bài-8--phân-cụm-k-means) | Không giám sát | `khach_hang.csv` (210 khách) | `bai08_kmeans` |
| 9 | [Mạng nơ-ron nhiều lớp (MLP)](#bài-9--mạng-nơ-ron-nhiều-lớp-mlp) | Phân loại + Hồi quy | `xor.csv`, `load_digits`... | `bai09_mlp` |

> Tất cả bộ dữ liệu là **số liệu mô phỏng phục vụ giảng dạy**, riêng `load_digits` và `load_sample_image` là dữ liệu có sẵn trong scikit-learn.

---

##  Nội dung chi tiết từng bài

### Bài 1 — Hồi quy tuyến tính

**Bài toán:** dự đoán **giá căn hộ** (tỷ đồng) từ diện tích, số phòng, tuổi nhà trên 60 căn hộ.

**Nội dung thực hành**

| Tệp | Nội dung |
|-----|----------|
| `b1_doc_du_lieu.py` | Đọc CSV bằng pandas, kiểm tra kích thước và ô trống, vẽ biểu đồ phân tán |
| `b2_do_sai_so.py` | Đo sai số từng căn, gộp thành MSE |
| `b3_cong_thuc.py` | Tìm `w`, `b` bằng công thức bình phương tối thiểu (tính tay) |
| `b4_sklearn.py` | Dùng `LinearRegression`, đối chiếu với cách tính tay |
| `b5_danh_gia.py` | Chia tập học/kiểm tra, tính MAE, RMSE, R² |
| `b6_gradient_descent.py` | Tự cài gradient descent, khảo sát tốc độ học |
| `b7_nhieu_bien.py` | Mở rộng sang nhiều biến (diện tích, số phòng, tuổi nhà) |

**Kết quả chính**

| Đại lượng | Giá trị |
|-----------|---------|
| Hệ số góc `w` / hệ số chặn `b` | **0.078367** / **0.401752** (cách tính tay và scikit-learn trùng nhau) |
| MSE trên 60 căn | 0.1790 |
| Dự đoán căn 80 m² / 100 m² | 6.671 / 8.238 tỷ đồng |
| Chia dữ liệu | 48 căn học, 12 căn kiểm tra (`test_size=0.2`, `random_state=42`) |
| MAE / RMSE trên tập kiểm tra | **0.2578** / **0.3730** tỷ đồng |
| R² (một biến → ba biến) | 0.9622 → **0.9761** |

**Bài học:** mô hình chỉ đáng tin trong khoảng dữ liệu đã học (35.5 – 117.5 m²). Đưa vào 250 m² máy vẫn trả về ~20 tỷ mà không báo lỗi, đó là **ngoại suy**, không có căn thật nào để kiểm chứng.

---

### Bài 2 — Hồi quy logistic

**Bài toán:** dự đoán sinh viên **qua môn hay rớt môn** (nhãn 0/1) từ số giờ ôn tập, điểm giữa kỳ. Bộ dữ liệu 120 sinh viên (71 qua, 49 rớt).

**Nội dung thực hành**

| Tệp | Nội dung |
|-----|----------|
| `c1_doc_du_lieu.py` | Đọc và xem qua dữ liệu |
| `c2_sigmoid.py` | Tự cài hàm sigmoid, hiểu vì sao đầu ra luôn nằm trong (0, 1) |
| `c3_khop_mo_hinh.py` | Khớp `LogisticRegression`, đọc xác suất và đổi thành nhãn |
| `c4_danh_gia.py` | Ma trận nhầm lẫn, accuracy, precision, recall, F1 |
| `c5_doi_nguong.py` | Đổi ngưỡng quyết định, thấy precision và recall đi ngược chiều |
| `c6_hai_bien.py` | Thêm biến đầu vào thứ hai |

**Kết quả chính**

| Đại lượng | Giá trị |
|-----------|---------|
| Mô hình một biến | `w = 0.392819`, `b = −5.064890` |
| Số giờ ôn ứng với xác suất 0.5 | 12.89 giờ |
| Ma trận nhầm lẫn (30 mẫu kiểm tra) | TP = 17, TN = 9, FP = 3, FN = 1 |
| Accuracy / Precision | 0.8667 / 0.8500 |
| Recall / F1 | 0.9444 / 0.8947 |
| Accuracy mô hình hai biến | **0.9000** |

---

### Bài 3 — Naive Bayes

**Bài toán:** xây **bộ lọc tin nhắn rác** (300 tin: 120 rác, 180 thường) và so sánh Naive Bayes với hồi quy logistic trên dữ liệu liên tục.

**Nội dung thực hành**

| Tệp | Nội dung |
|-----|----------|
| `d1_bayes_tay.py` | Định lý Bayes bằng công thức và bằng cách đếm |
| `d2_tui_tu.py` | Biến văn bản thành bảng số (túi từ, `CountVectorizer`) |
| `d3_loc_thu_rac.py` | Huấn luyện `MultinomialNB`, chấm điểm bộ lọc |
| `d4_lam_tron.py` | Tự cài Naive Bayes để thấy vấn đề xác suất bằng 0 và vai trò làm trơn Laplace |
| `d5_gaussian.py` | `GaussianNB` cho số liệu liên tục, so với logistic |

**Kết quả chính**

| Đại lượng | Giá trị |
|-----------|---------|
| Hậu nghiệm ví dụ xét nghiệm "chính xác 99%" | **0.5000** (báo nhầm tới một nửa số ca) |
| Từ điển / chia dữ liệu | 40 từ / 225 học, 75 kiểm tra |
| Ma trận nhầm lẫn bộ lọc | TP = 26, TN = 45, FP = 0, FN = 4 |
| Accuracy / Precision / Recall | 0.9467 / **1.0000** / 0.8667 |
| Naive Bayes vs logistic (dữ liệu sinh viên) | Cùng đạt 0.9000 |
| Chỉ có 10 tin huấn luyện | Naive Bayes **0.9072** vs logistic 0.7808 |

**Bài học:** Naive Bayes mạnh khi dữ liệu ít; bỏ làm trơn Laplace khiến mô hình "gãy" vì xác suất bằng 0.

---

### Bài 4 — K láng giềng gần nhất (KNN)

**Bài toán:** mô hình "học lười", giữ nguyên dữ liệu và hỏi các mẫu cũ giống mẫu mới nhất. Áp dụng cho phân loại (sinh viên qua môn, hai vầng trăng) và hồi quy (giá nhà).

**Nội dung thực hành**

| Tệp | Nội dung |
|-----|----------|
| `e1_khoang_cach.py` | Tự tính khoảng cách Euclid và tự tìm k láng giềng bằng NumPy |
| `e2_chuan_hoa.py` | Đo hậu quả của việc quên chuẩn hoá |
| `e3_chon_k.py` | Chọn k bằng kiểm định chéo (chỉ thử k lẻ để tránh hoà phiếu) |
| `e4_so_sanh.py` | So KNN với logistic và Naive Bayes trên biên cong |
| `e5_knn_hoi_quy.py` | `KNeighborsRegressor` và giới hạn ngoại suy |

**Kết quả chính**

| Thí nghiệm | Kết quả |
|------------|---------|
| Khoảng cách A–C khi **chưa** chuẩn hoá | 3000.0 (máy cho rằng A giống B hơn) |
| Khoảng cách A–C sau chuẩn hoá | 1.79 (đúng trực giác, nhỏ hơn A–B = 3.85) |
| Ba cột, **không** chuẩn hoá | 0.5333 (thấp hơn cả đoán bừa 0.6000) |
| Ba cột, có chuẩn hoá | 0.8667 |
| Bỏ cột chi tiêu, có chuẩn hoá | **0.9000** |
| k tối ưu theo kiểm định chéo (hai vầng trăng) | k = 13, điểm CV 0.8667, kiểm tra **0.9200** |
| Hai vầng trăng: logistic / Naive Bayes / KNN | 0.8533 / 0.8533 / **0.9200** |
| Giá nhà, MAE: KNN (k=5) vs đường thẳng | 0.4030 vs **0.2578** |

**Bài học:** KNN **bắt buộc chuẩn hoá**; không ngoại suy được (căn 150 m² và 250 m² cùng nhận một dự đoán 9.32 tỷ); yếu khi có nhiều đặc trưng (lời nguyền số chiều).

---

### Bài 5 — Cây quyết định và Rừng ngẫu nhiên

**Bài toán:** đoán **khách vay có trả nợ đúng hạn không** từ thu nhập, tỷ lệ nợ, việc làm ổn định, số người phụ thuộc (600 hồ sơ). Cây quyết định đọc được như luật của nhân viên ngân hàng.

**Nội dung thực hành**

| Tệp | Nội dung |
|-----|----------|
| `f1_gini.py` | Tự tính Gini và chọn câu hỏi chia tốt nhất |
| `f2_cay_nam_la.py` | Học và đọc một cây năm lá |
| `f3_do_sau.py` | Cây học vẹt và chọn độ sâu bằng kiểm định chéo |
| `f4_khong_chuan_hoa.py` | Kiểm chứng cây không cần chuẩn hoá |
| `f5_rung.py` | Rừng ngẫu nhiên so với một cây đơn |
| `f6_do_quan_trong.py` | Độ quan trọng của đặc trưng và giới hạn của nó |
| `f7_cay_hoi_quy.py` | Cây cho bài toán hồi quy giá nhà |

**Kết quả chính**

| Đại lượng | Giá trị |
|-----------|---------|
| Gini nút gốc (10 khách) | 0.48 |
| Ngưỡng tốt nhất / mức Gini giảm | 12.0 / 0.1633 |
| Cây năm lá: học / kiểm tra | 0.7978 / 0.7467 |
| Cây tự do (độ sâu 13, 92 lá), kiểm tra | 0.7667 (học vẹt) |
| Độ sâu tốt nhất theo CV | 5, điểm 0.8333 → kiểm tra **0.8533** |
| Rừng 200 cây, kiểm tra | **0.9000** |
| Độ quan trọng: thu nhập / tỷ lệ nợ | 0.479 / 0.339 |
| Giá nhà, MAE: cây sâu 3 vs đường thẳng | 0.5039 vs **0.2578** |

---

### Bài 6 — Máy vectơ hỗ trợ (SVM)

**Bài toán:** tìm đường ranh giới có **lề rộng nhất**, chỉ cần nhớ vài vectơ hỗ trợ, và dùng **kernel** để vẽ biên cong.

**Nội dung thực hành**

| Tệp | Nội dung |
|-----|----------|
| `g1_le_rong_nhat.py` | Đường có lề rộng nhất và vectơ hỗ trợ trên 24 điểm |
| `g2_tham_so_c.py` | Tham số C (lề mềm) và việc chuẩn hoá |
| `g3_kernel.py` | Nâng chiều bằng tay (thêm cột x²) và so ba loại kernel |
| `g4_chon_tham_so.py` | Ảnh hưởng của gamma, dò lưới C và gamma bằng `GridSearchCV` |
| `g5_chu_so.py` | Nhận dạng chữ số viết tay (10 lớp) |

**Kết quả chính**

| Thí nghiệm | Kết quả |
|------------|---------|
| 24 điểm tách được | Lề rộng **2.21**, chỉ **3** vectơ hỗ trợ quyết định đường ranh giới |
| C = 0.01 → C = 100 (sinh viên) | Vectơ hỗ trợ giảm 74 → 27, lề thu hẹp 3.84 → 1.05 |
| Ba cột, kernel RBF: không / có chuẩn hoá | 0.6000 / **0.9000** |
| Hai vầng trăng: tuyến tính / đa thức bậc 3 / RBF | 0.8667 / 0.8667 / **0.9200** |
| gamma = 100 | Học 0.9422 nhưng kiểm tra chỉ 0.8133 (học vẹt) |
| Cặp tốt nhất qua `GridSearchCV` | `C = 10`, `gamma = 1`, CV 0.8711, kiểm tra 0.9200 |
| Chữ số viết tay, SVM RBF | **0.9911** (sai 4/450 ảnh) |

**Bài học:** không phải lúc nào cũng chuẩn hoá. Với `load_digits`, SVM có chuẩn hoá (0.9778) lại kém hơn không chuẩn hoá (0.9911) vì chuẩn hoá phóng to các ô mép ảnh gần như vô nghĩa.

---

### Bài 7 — Đánh giá mô hình

**Bài toán:** phát hiện sớm **sinh viên có nguy cơ bỏ học** trên 1200 sinh viên, chỉ khoảng 10% bỏ học (dữ liệu **lệch lớp**). Bài này cho thấy khi nào accuracy đánh lừa.

**Nội dung thực hành**

| Tệp | Nội dung |
|-----|----------|
| `h1_do_bua.py` | So mô hình với `DummyClassifier` (mức sàn) |
| `h2_ma_tran.py` | Tự đếm TP, FP, FN, TN và so với `confusion_matrix` |
| `h3_precision_recall.py` | Precision, recall, F1 bằng tay và bằng thư viện |
| `h4_nguong.py` | Đổi ngưỡng và chọn ngưỡng đúng cách bằng `cross_val_predict` |
| `h5_roc_auc.py` | Đường ROC, AUC và so sánh 6 mô hình |
| `h6_can_bang.py` | Kiểm định chéo nhiều thước đo, cân bằng lớp |

**Kết quả chính**

| Đại lượng | Giá trị |
|-----------|---------|
| Tỷ lệ bỏ học | 0.099 (119/1200) |
| Accuracy: mô hình lười vs logistic | 0.9000 (tìm ra **0**/30 bạn) vs 0.9467 (tìm ra 17/30) |
| TP, FP, FN, TN (logistic) | 17, 3, 13, 267 |
| Precision / Recall / F1 (ngưỡng 0.5) | 0.8500 / 0.5667 / 0.6800 |
| Ngưỡng chọn bằng kiểm định chéo | **0.25** → Precision 0.6571, Recall **0.7667**, F1 0.7077 |
| AUC của logistic | **0.9449** (cao nhất trong 6 mô hình) |
| Recall CV trên tập học | 0.4810 (accuracy CV 0.9289 che giấu việc bỏ sót) |
| `class_weight="balanced"` | Recall 0.5667 → **0.8667**, Precision 0.8500 → 0.4483 |

**Bài học:** accuracy 0.9 chỉ là *mức sàn* trên dữ liệu lệch lớp; chọn ngưỡng và tham số bằng tập học, không bằng tập kiểm tra.

---

### Bài 8 — Phân cụm K-Means

**Bài toán:** lần đầu **không có nhãn**. Phân khúc 210 khách hàng trung tâm thương mại theo thu nhập và điểm chi tiêu.

**Nội dung thực hành**

| Tệp | Nội dung |
|-----|----------|
| `k1_tu_viet.py` | Tự viết K-Means bằng NumPy, chạy từng vòng trên 7 điểm |
| `k2_khach_hang.py` | Phân khúc khách hàng, đọc tâm cụm theo đơn vị gốc, xếp khách mới vào cụm |
| `k3_chon_k.py` | Chọn K bằng phương pháp khuỷu tay và silhouette |
| `k4_ba_cai_bay.py` | Ba cái bẫy: quên chuẩn hoá, khởi tạo xấu, cụm không tròn |
| `k5_nen_anh.py` | Nén màu ảnh bằng K-Means |

**Kết quả chính**

| Đại lượng | Giá trị |
|-----------|---------|
| Bảy điểm | Dừng sau 3 vòng, inertia **8.5250** (trùng scikit-learn) |
| Khách hàng, K = 5 | Inertia 23.0, silhouette cao nhất **0.723** (K = 4: 0.626; K = 6: 0.651) |
| Năm cụm | Thu nhập thấp–chi nhiều (trẻ nhất, tuổi TB 24.9), thu nhập cao–chi ít, vừa–vừa (đông nhất, 60 khách), thu nhập thấp–chi ít, thu nhập cao–chi nhiều |
| Bẫy khởi tạo (20 lần `n_init=1`) | 10 lần kẹt ở cách chia kém, tệ nhất inertia **118.2** |
| Bẫy cụm không tròn (hai vầng trăng) | Chỉ khớp nhãn thật 0.7500 |
| Nén ảnh 427×640: 96 615 màu → 16 màu | Nhỏ hơn **6 lần**, sai lệch trung bình 7.97 mức sáng |

**Bài học:** số thứ tự cụm không có ý nghĩa, luôn đọc tâm cụm; K-Means chỉ cắt bằng đường thẳng nên không xử lý được cụm cong.

---

### Bài 9 — Mạng nơ-ron nhiều lớp (MLP)

**Bài toán:** ghép nhiều nơ-ron (mỗi nơ-ron là một hồi quy logistic) thành mạng nhiều lớp, vẽ được ranh giới cong tuỳ ý.

**Nội dung thực hành**

| Tệp | Nội dung |
|-----|----------|
| `m1_lan_truyen_tien.py` | Tự tính lan truyền tiến; mạng 2-2-1 với ReLU giải được XOR |
| `m2_xor.py` | Một nơ-ron không giải được XOR, một lớp ẩn thì được |
| `m3_do_lon_mang.py` | Độ lớn mạng, điều chuẩn L2 (`alpha`), chọn `alpha` bằng kiểm định chéo |
| `m4_chuan_hoa.py` | Mạng nơ-ron khi quên chuẩn hoá |
| `m5_chu_so.py` | Nhận dạng chữ số viết tay bằng `MLPClassifier` |

**Kết quả chính**

| Thí nghiệm | Kết quả |
|------------|---------|
| XOR: hồi quy logistic | 0.4500 (kém hơn tung đồng xu) |
| XOR: MLP 4 / 8 nơ-ron ẩn | 0.9300 / 0.9100 |
| Hai vầng trăng, mạng (100,100) không điều chuẩn | Học 1.0000, kiểm tra 0.7333 (học vẹt) |
| Cùng mạng với `alpha = 1.0` | Học 0.8800, kiểm tra **0.9067** |
| Sinh viên mở rộng: không / có chuẩn hoá | 0.4000 / **0.9000** |
| Chữ số viết tay | 7 510 tham số, 144 vòng học, accuracy **0.9844** (sai 7/450) |

**Bài học:** mạng nơ-ron nhạy với thang đo hơn cả KNN; trên bộ dữ liệu nhỏ (1797 ảnh) SVM và KNN vẫn nhỉnh hơn MLP.

---

## Tổng hợp so sánh các mô hình

### Trên dữ liệu có biên cong (hai vầng trăng, tập kiểm tra)

| Mô hình | Accuracy | Nhận xét |
|---------|:--------:|----------|
| Hồi quy logistic | 0.8533 | Chỉ vẽ được đường thẳng |
| Naive Bayes (Gaussian) | 0.8533 | Giả định độc lập, biên đơn giản |
| SVM kernel tuyến tính | 0.8667 | Vẫn là biên thẳng |
| MLP (100,100), `alpha=1` | 0.9067 | Cần điều chuẩn để tránh học vẹt |
| **KNN, k = 13** | **0.9200** | Tự uốn theo dữ liệu, nhưng phải giữ toàn bộ dữ liệu |
| **SVM kernel RBF** | **0.9200** | Chỉ nhớ vectơ hỗ trợ (89/225 điểm) |

### Trên nhận dạng chữ số viết tay (1797 ảnh, 10 lớp, tập kiểm tra 450 ảnh)

| Mô hình | Accuracy |
|---------|:--------:|
| **SVM kernel RBF** (mặc định) | **0.9911** |
| KNN, k = 5 | 0.9867 |
| MLP 1 lớp ẩn 100 nơ-ron | 0.9844 |
| Hồi quy logistic (có chuẩn hoá) | 0.9711 |

### Tác động của việc quên chuẩn hoá (bộ sinh viên mở rộng, 3 cột)

| Mô hình | Không chuẩn hoá | Có chuẩn hoá | Mức đoán bừa |
|---------|:---------------:|:------------:|:------------:|
| KNN (k = 7) | 0.5333 | 0.8667 | 0.6000 |
| SVM (RBF) | 0.6000 | 0.9000 | 0.6000 |
| MLP (20 nơ-ron) | 0.4000 | 0.9000 | 0.6000 |

### Trên dữ liệu giá nhà (hồi quy, MAE trên tập kiểm tra, tỷ đồng)

| Mô hình | MAE |
|---------|:---:|
| **Hồi quy tuyến tính** | **0.2578** |
| KNN (k = 5) | 0.4030 |
| Cây quyết định (sâu 3) | 0.5039 |

> **Không có mô hình nào tốt nhất cho mọi bài toán.** Hình dạng thật của dữ liệu quyết định mô hình nào phù hợp: biên cong thì KNN/SVM thắng, quan hệ gần như thẳng thì đường thẳng thắng.

---

## Những bài học xuyên suốt

1. **Luôn có mức sàn để so sánh.** Mô hình lười (đoán lớp đông nhất) cho biết accuracy bao nhiêu là "không có gì".
2. **Không bao giờ chấm điểm trên dữ liệu đã học.** Accuracy 1.0000 của KNN với k = 1 trên tập học là vô nghĩa.
3. **Tập kiểm tra chỉ mở một lần**, sau khi đã chọn xong k, độ sâu, C, gamma, alpha hay ngưỡng bằng kiểm định chéo trên tập học.
4. **Chuẩn hoá là bắt buộc** với mọi mô hình dựa vào khoảng cách hoặc gradient (KNN, SVM, K-Means, MLP) nhưng **không cần** với cây quyết định. Luôn dùng `make_pipeline(StandardScaler(), ...)` để tránh **rò rỉ dữ liệu**.
5. **Cẩu thả ↔ học vẹt** là một nút vặn chung: `k` của KNN, độ sâu của cây, `C` và `gamma` của SVM, `alpha` và kích thước mạng của MLP.
6. **Accuracy có thể đánh lừa** khi dữ liệu lệch lớp; hãy nhìn ma trận nhầm lẫn, precision, recall, F1 và AUC, rồi hỏi "báo nhầm hay bỏ sót, cái nào đắt hơn?".
7. **Mô hình chỉ đáng tin trong vùng dữ liệu đã học.** Hãy cảnh báo khi ngoại suy.
8. **Luôn vẽ dữ liệu ra trước khi chọn mô hình.**

---

## Bài tập

Mỗi bài có một bộ bài tập tự làm đặt trong thư mục `baitapXX/` (ví dụ `baitap04/bai1.py`), chạy từ thư mục gốc của bài. Bài nộp gồm **mã nguồn** và **ảnh chụp màn hình kết quả**.

| Bài | Số bài tập | Một số chủ đề |
|:---:|:---------:|---------------|
| 1 | 6 | Lọc dữ liệu, biểu đồ phân tán, đổi biến đầu vào, thêm biến, tốc độ học, hàm dự đoán có cảnh báo ngoại suy |
| 2 | 6 | Thống kê theo nhóm, vẽ hàm sigmoid, dự đoán cho một bạn cụ thể, tự tính bốn thước đo, dò ngưỡng tốt nhất theo F1, đổi lớp dương rồi chấm lại |
| 3 | 6 | Bayes với ba nguyên nhân, từ nào tố cáo mạnh nhất, đổi tham số làm trơn, tự viết bộ lọc không dùng thư viện, chọn sai biến thể Naive Bayes, lớp hiếm và xác suất tiên nghiệm |
| 4 | 6 | Tự viết KNN, khoảng cách Manhattan, đổi đơn vị đo, láng giềng có trọng số, chọn k cho hồi quy, đo thời gian dự đoán |
| 5 | 6 | Tự vẽ cây, tự tìm câu hỏi gốc trên dữ liệu thật, Gini hay entropy, cắt tỉa bằng số khách tối thiểu ở lá, độ quan trọng bằng cách xáo trộn, rừng cho bài toán hồi quy |
| 6 | 6 | Tính tay khoảng cách tới ranh giới, thêm điểm, kernel đa thức, dò lưới mịn, bảng nhầm lẫn chữ số, SVM trên dữ liệu lớn |
| 7 | 6 | Tự viết hàm đánh giá, `classification_report`, chọn ngưỡng theo yêu cầu, tự vẽ ROC, cân bằng lớp, MAE vs RMSE |
| 8 | 6 | Tự tính silhouette, thêm cột tuổi, K-Means++ vs ngẫu nhiên, lưu ảnh nén, DBSCAN, phân cụm chữ số |
| 9 | 6 | Tự dự đoán bằng trọng số đã học, mạng XOR khác, so hàm kích hoạt, tốc độ học, dò lưới, `MLPRegressor` |

**Tiêu chí chấm chung:** (1) mã chạy được không lỗi, (2) kết quả in ra đúng và khớp ảnh chụp, (3) có nhận xét bằng lời ở những bài yêu cầu, (4) tên biến đặt có nghĩa.

---

## Công nghệ sử dụng

| Công cụ | Vai trò |
|---------|---------|
| **Python 3.10+** | Ngôn ngữ chính |
| **NumPy** | Tự cài đặt thuật toán, tính toán ma trận |
| **pandas** | Đọc và xử lý dữ liệu CSV |
| **Matplotlib** | Vẽ biểu đồ, ranh giới quyết định, đường ROC, đường mất mát |
| **scikit-learn** | Mô hình, tiền xử lý, đánh giá, kiểm định chéo, dò lưới |

Các lớp và hàm chính của scikit-learn được dùng: `LinearRegression`, `LogisticRegression`, `MultinomialNB`, `GaussianNB`, `KNeighborsClassifier/Regressor`, `DecisionTreeClassifier/Regressor`, `RandomForestClassifier`, `SVC`, `KMeans`, `MLPClassifier/Regressor`, `StandardScaler`, `make_pipeline`, `train_test_split`, `cross_val_score`, `cross_val_predict`, `GridSearchCV`, `confusion_matrix`, `classification_report`, `roc_auc_score`, `silhouette_score`.

---

## Thông tin tác giả

| | |
|---|---|
| **Sinh viên thực hiện** | `[Nguyen Ngoc Han]` |
| **Mã số sinh viên** | `[2474802010533]` |
| **Lớp** | `[261_71ITAI41203_01]` |
| **Giảng viên** | ThS. Nguyễn Thái Anh |
| **Đơn vị** | Khoa Công nghệ Thông tin, Trường Đại học Văn Lang |
| **Năm học** | 2026 – 2027 |

<div align="center">

⭐ Nếu thấy repository hữu ích, hãy để lại một ngôi sao nhé!

</div>
