# **Dự Đoán Thị Trường Chứng Khoán Sử Dụng Linear Regression và LSTM**
## Tổng Quan

Project này nhằm dự đoán giá thị trường chứng khoán sử dụng hai mô hình khác nhau:

- Linear Regression (mô hình Machine Learning).
- LSTM (Long Short-Term Memory, mô hình Deep Learning).

**Project này sẽ so sánh kết quả độ chính xác khi huấn luyện của 2 mô hình, cũng như hoàn thành môn học Maching Learning của chúng tôi.**

## Mục Lục
- Cài Đặt
- Dữ Liệu
- Tiền Xử Lý Dữ Liệu
- Xây Dựng Mô Hình, Huấn Luyện và Kiểm Thử
- Đánh Giá Mô Hình
- Kết luận
Để chạy dự án này, cần cài đặt các thư viện cần thiết bằng các lệnh sau:

```bash
pip install numpy pandas scikit-learn tensorflow matplotlib vnstock
```

## Dữ liệu:


Chúng ta sử dụng API VNStock để tải dữ liệu chứng khoán lịch sử. Bộ dữ liệu bao gồm các cột sau:

- time: Ngày giao dịch. Đây là cột chỉ ra ngày cụ thể mà các giao dịch này đã diễn ra, theo định dạng năm-tháng-ngày (YYYY-MM-DD).
- open: Giá mở cửa. Đây là mức giá đầu tiên được giao dịch vào ngày đó.
- high: Giá cao nhất. Đây là mức giá cao nhất mà cổ phiếu được giao dịch trong ngày.
- low: Giá thấp nhất. Đây là mức giá thấp nhất mà cổ phiếu được giao dịch trong ngày.
- close: Giá đóng cửa. Đây là mức giá cuối cùng được giao dịch vào ngày đó.
- volume: Khối lượng giao dịch. Đây là tổng số lượng cổ phiếu được giao dịch trong ngày.

## Tiền Xử Lý Dữ Liệu
1. Làm Sạch Dữ Liệu: Xử lý giá trị thiếu (nếu có) và loại bỏ các cột không cần thiết.
2. Thống Kê Mô Tả: Khám phá dữ liệu bằng các phương pháp thống kê để nắm được các xu hướng như giá trung bình, độ biến động và phân phối.
3. Chọn Đặc Trưng: Chọn các đặc trưng cần thiết (ví dụ: giá 'Close') để huấn luyện mô hình.
4. Chia Tập Train-Test: Chia dữ liệu thành tập huấn luyện và tập kiểm thử với tỉ lệ 80-20.
## Trực quan hóa
- Thấy được sự biến động và mối liên hệ của các thuộc tính có trong dataset.

## Chia tập train test

```bash
from sklearn.model_selection import train_test_split

train_data, test_data = train_test_split(stock_data, test_size=0.2, shuffle=False)
```

## Xây Dựng Mô Hình, Huấn Luyện và Kiểm Thử
- Linear Regression: Mô hình được huấn luyện dựa trên giá cổ phiếu trong quá khứ làm đặc trưng và giá 'Close' làm mục tiêu.
- LSTM: Mô hình được huấn luyện trên các chuỗi giá cổ phiếu, trong đó mỗi chuỗi đại diện cho một cửa sổ thời gian của dữ liệu lịch sử.
## Đánh Giá Mô Hình
Model  | Mean Squared Error | R^2 Score | Mean Absolute Error (MAE)
------|------------|------------|-------------
0 | Linear Regression     |   17154.434379  |  0.99942           |       83.171267
1       |        LSTM      | 297506.432290   | 0.98997      |           330.285670

## Kết luận
### **Ta có thể rút ra được kết luận từ bảng so sánh các độ đo ở trên như sau:**

Dựa trên các độ đo được cung cấp, ta có thể rút ra các kết luận so sánh về hai mô hình dự đoán thị trường chứng khoán bằng hai phương pháp máy học: Linear Regression (Hồi quy tuyến tính) và LSTM (Long Short-Term Memory).

- MSE đo lường trung bình bình phương của các sai số dự đoán. Mô hình Linear Regression có MSE nhỏ hơn rất nhiều so với LSTM, điều này cho thấy rằng sai số bình phương trung bình của các dự đoán từ mô hình Linear Regression nhỏ hơn so với LSTM. Nói cách khác, Linear Regression dự đoán gần đúng giá trị thực tế hơn so với LSTM.

- $R^2 Score$ (hệ số xác định) đo lường tỷ lệ biến thiên của dữ liệu có thể giải thích được bằng mô hình. $R^2 Score$ của Linear Regression gần bằng 1, cho thấy rằng mô hình này giải thích rất tốt biến thiên trong dữ liệu. $R^2 Score$ của LSTM cũng cao, nhưng thấp hơn so với Linear Regression, cho thấy rằng Linear Regression có khả năng giải thích biến thiên của dữ liệu tốt hơn.

- MAE đo lường trung bình giá trị tuyệt đối của các sai số dự đoán. MAE của Linear Regression nhỏ hơn rất nhiều so với LSTM, cho thấy rằng sai số trung bình của các dự đoán từ mô hình Linear Regression nhỏ hơn so với LSTM. Điều này cũng củng cố kết luận rằng Linear Regression dự đoán chính xác hơn so với LSTM.

> Dựa trên các độ đo đã phân tích (MSE, $R^2 Score$, MAE), có thể rút ra kết luận rằng mô hình Linear Regression có hiệu suất dự đoán tốt hơn mô hình LSTM trong bài toán dự đoán thị trường chứng khoán. Linear Regression có sai số nhỏ hơn và khả năng giải thích biến thiên của dữ liệu tốt hơn so với LSTM.
