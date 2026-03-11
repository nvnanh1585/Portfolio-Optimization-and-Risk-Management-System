# Portfolio Optimization & Risk Management System

## Tổng quan

Dự án này xây dựng một **framework tối ưu hóa danh mục đầu tư và quản trị rủi ro** cho thị trường chứng khoán Việt Nam, kết hợp các phương pháp định lượng hiện đại nhằm khắc phục những hạn chế của mô hình **Markowitz Mean-Variance** truyền thống.

Dự án sử dụng **1.827 quan sát lợi suất ngày** của 6 cổ phiếu niêm yết (**HPG, VCB, BMP, VEA, GVR, MVB**) trong giai đoạn **2018–2025** để xây dựng một pipeline phân tích nhiều tầng, bao gồm tối ưu danh mục, mô hình hóa biến động, mô hình hóa phụ thuộc và mô phỏng rủi ro.

Mục tiêu của dự án là phát triển một **hệ thống tối ưu danh mục đầu tư có khả năng phản ánh chính xác hơn đặc điểm rủi ro thực tế của thị trường tài chính** và hỗ trợ ra quyết định đầu tư dựa trên dữ liệu.

---

# Phương pháp luận

Framework này mở rộng mô hình **Markowitz Mean-Variance Optimization** bằng cách tích hợp nhiều kỹ thuật định lượng tiên tiến.

---

## 1. Tiền xử lý dữ liệu & phân tích khám phá

* Làm sạch và chuẩn hóa dữ liệu giá cổ phiếu (OHLC)
* Phân tích thống kê mô tả của chuỗi lợi suất
* Phân tích phân phối và đặc điểm biến động của dữ liệu

---

## 2. Ước lượng ma trận hiệp phương sai

Một hạn chế lớn của Markowitz là **nhiễu trong ước lượng ma trận hiệp phương sai**.
Dự án áp dụng:

**Ledoit–Wolf Shrinkage Estimator**

Lợi ích:

* Giảm nhiễu trong ước lượng
* Làm trơn ma trận hiệp phương sai
* Tránh hiện tượng trọng số danh mục cực đoan

---

## 3. Mô hình hóa biến động

Biến động của chuỗi lợi suất được mô hình hóa bằng:

**GJR-GARCH (1,1,1)**

Mô hình này cho phép:

* Nắm bắt **volatility clustering**
* Phản ánh **hiệu ứng bất đối xứng của cú sốc thị trường**
* Mô hình hóa **phương sai có điều kiện theo thời gian**

---

## 4. Mô hình hóa phụ thuộc giữa các tài sản

Thay vì sử dụng hệ số tương quan tuyến tính, dự án áp dụng:

**R-vine Copula**

Ưu điểm:

* Mô hình hóa **phụ thuộc phi tuyến**
* Bắt được **tail dependence**
* Phản ánh cấu trúc phụ thuộc phức tạp giữa các tài sản

---

## 5. Mô phỏng rủi ro danh mục

Rủi ro danh mục được ước lượng thông qua:

**Monte Carlo Simulation**

Các thước đo rủi ro được sử dụng:

* Value-at-Risk (VaR)
* Expected Shortfall (ES)
* Maximum Drawdown
* Calmar Ratio

---

## 6. Phát hiện chế độ thị trường

Để nắm bắt sự thay đổi cấu trúc của thị trường, dự án sử dụng:

**Hidden Markov Model (HMM)**

Mô hình giúp phát hiện các **market regimes**, từ đó hỗ trợ điều chỉnh chiến lược phân bổ danh mục.

---

# Kết quả chính

Phân tích thực nghiệm cho thấy một số kết quả quan trọng:

* **Chiến lược Min-CVaR** đạt hiệu suất tốt nhất trên tập **out-of-sample** với **Sharpe ratio = 0.659** và **tăng 31.36% giá trị danh mục**.
* **VaR backtesting** nằm trong **vùng xanh (BIS green zone)**, xác nhận độ tin cậy của mô hình đo lường rủi ro.
* Stress testing cho thấy danh mục chỉ gồm cổ phiếu dễ tổn thương trong các kịch bản **stagflation**, nhấn mạnh nhu cầu đa dạng hóa sang các tài sản phòng hộ.

---

# Công cụ sử dụng

* Python
* NumPy
* Pandas
* SciPy
* Statsmodels
* arch
* scikit-learn
* matplotlib / seaborn

---

# Các khái niệm định lượng được triển khai

* Markowitz Portfolio Optimization
* Ledoit–Wolf Covariance Shrinkage
* GJR-GARCH Volatility Modeling
* R-vine Copula Dependence Modeling
* Monte Carlo Risk Simulation
* Value-at-Risk (VaR)
* Expected Shortfall (ES)
* Hidden Markov Model cho market regime detection

---

# Kết luận

Dự án cho thấy việc kết hợp **ước lượng hiệp phương sai vững chắc, mô hình hóa biến động, mô hình hóa phụ thuộc và mô phỏng rủi ro** có thể cải thiện đáng kể hiệu quả của các phương pháp tối ưu danh mục truyền thống.

Framework được đề xuất cung cấp một nền tảng định lượng hữu ích cho **quản trị danh mục đầu tư và phân tích rủi ro trong các thị trường mới nổi như Việt Nam**.
