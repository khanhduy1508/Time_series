# Time_series

Dự án này tập trung vào việc nghiên cứu và triển khai các mô hình dự báo chuỗi thời gian (time series forecasting), đặc biệt là trong lĩnh vực tài chính và chứng khoán. Mục tiêu là xây dựng, huấn luyện và đánh giá các mô hình học máy và học sâu để dự đoán xu hướng giá trong tương lai.

---

## Giới thiệu

Repository bao gồm mã nguồn, dữ liệu và notebook phục vụ cho quá trình huấn luyện và kiểm thử các mô hình dự báo. Dự án hướng tới việc so sánh các phương pháp truyền thống (ARIMA, Prophet) và các mô hình học sâu (LSTM, RNN, GRU).

---

## Cấu trúc thư mục

Time_series/
├── image/
│ └── ... (hình ảnh minh họa, biểu đồ kết quả)
├── predict-stock-market-using-machinglearning-deeplearning-master/
│ └── ... (mã nguồn mô hình Machine Learning / Deep Learning)
├── stock-historical-data/
│ └── ... (dữ liệu lịch sử, định dạng CSV)
├── VCB-History.csv
├── model.ipynb
└── README.md

- **image/**: chứa các biểu đồ, hình ảnh minh họa kết quả dự báo.  
- **predict-stock-market-using-machinglearning-deeplearning-master/**: chứa mã nguồn các mô hình học máy và học sâu.  
- **stock-historical-data/**: chứa dữ liệu lịch sử của các cổ phiếu hoặc chỉ số thị trường.  
- **VCB-History.csv**: ví dụ dữ liệu lịch sử của cổ phiếu VCB.  
- **model.ipynb**: notebook chính dùng để thử nghiệm và trực quan hóa kết quả mô hình.  

---

## Cài đặt và yêu cầu

1. Cài đặt Python 3.7 trở lên.  
2. Tạo môi trường ảo và kích hoạt:
   ```bash
   python -m venv venv
   source venv/bin/activate    # Linux/macOS
   venv\Scripts\activate       # Windows

Cài các thư viện cần thiết:

pip install -r requirements.txt


Nếu chưa có file requirements.txt, bạn có thể cài các thư viện chính:

pip install numpy pandas matplotlib scikit-learn tensorflow statsmodels

Hướng dẫn sử dụng

Đặt dữ liệu chuỗi thời gian vào thư mục stock-historical-data.

Mở notebook model(1).ipynb bằng Jupyter Notebook hoặc VSCode để chạy thử.

Thực hiện tiền xử lý dữ liệu, huấn luyện mô hình, và đánh giá kết quả.

Xuất biểu đồ và kết quả dự báo ra thư mục image/.

Kết quả

Các mô hình được huấn luyện sẽ tạo ra kết quả dự báo giá, sai số (RMSE, MAE) và đồ thị so sánh giữa dữ liệu thực tế và dự báo.
Bạn có thể thêm hình minh họa kết quả vào README như ví dụ sau:

![Kết quả dự báo cổ phiếu VCB](image/vcb_forecast_plot.png)

Ghi chú

Không nên commit dữ liệu lớn trực tiếp vào repository, có thể sử dụng Git LFS.

Có thể mở rộng dự án bằng cách bổ sung thêm các mô hình như Prophet, XGBoost hoặc Transformer.

Nên tạo file requirements.txt để người khác dễ dàng cài đặt môi trường.

Hướng phát triển

Bổ sung giao diện trực quan hóa kết quả dự báo.

Tự động cập nhật dữ liệu thời gian thực từ API tài chính.

So sánh hiệu năng giữa nhiều mô hình khác nhau.
