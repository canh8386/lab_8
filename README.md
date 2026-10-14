# lab_8
# Báo cáo Thực hành: Kiểm thử hiệu năng với Apache JMeter

**Thông tin sinh viên**
- **Họ và tên:** Lê Đình Đức Anh
- **Mã sinh viên:** [23010219]

---

## 1. Mục tiêu và Đối tượng kiểm thử
- **Mục tiêu:** Áp dụng công cụ Apache JMeter 5.6.3 để thực thi kiểm thử hiệu năng (Performance Testing), đánh giá thời gian phản hồi, thông lượng và độ ổn định của hệ thống dưới tải trọng giả lập.
- **Đối tượng kiểm thử:** Kịch bản kiểm thử HTTP Request (`Summary Report.jmx`).

---

## 2. Kịch bản kiểm thử (Test Scenario)
- **Tổng số request thực hiện (# Samples):** 100 requests.
- **Thành phần cấu hình trong Test Plan:**
  - **Thread Group:** Nhóm người dùng ảo gửi 100 request.
  - **HTTP Request:** Cấu hình phương thức và đường dẫn tới server kiểm thử.
  - **View Results Tree:** Giám sát trạng thái phản hồi của từng request chi tiết.
  - **Summary Report:** Thu thập và tổng hợp chỉ số hiệu năng hệ thống.

---

## 3. Kết quả kiểm thử thực tế

### 3.1. Trạng thái phản hồi (View Results Tree)
![View Results Tree](link-anh-view-results-tree.png)
*Hình 1: Danh sách các request xử lý trong View Results Tree.*

- **Nhận xét:** 100% request (100/100) đều hiển thị biểu tượng **màu xanh (Success)**, không có request nào bị timeout hoặc trả về lỗi HTTP.

---

### 3.2. Báo cáo thống kê hiệu năng (Summary Report)
![Summary Report](link-anh-summary-report.png)
*Hình 2: Bảng chỉ số hiệu năng chi tiết từ Summary Report.*

**Bảng tổng hợp dữ liệu đo lường:**

| Chỉ số (Metric) | Giá trị thực tế | Ý nghĩa |
| :--- | :--- | :--- |
| **# Samples** | `100` | Tổng số lượng request đã gửi |
| **Average** | `177 ms` | Thời gian phản hồi trung bình |
| **Min** | `151 ms` | Thời gian phản hồi nhanh nhất |
| **Max** | `223 ms` | Thời gian phản hồi chậm nhất |
| **Std. Dev.** | `14.94` | Độ lệch chuẩn (mức độ chênh lệch thời gian phản hồi) |
| **Error %** | `0.00%` | Tỉ lệ lỗi |
| **Throughput** | `83.1 / sec` | Thông lượng (số request hệ thống xử lý được/giây) |
| **Received KB/sec** | `75.78 KB/s` | Tốc độ nhận dữ liệu từ server |
| **Sent KB/sec** | `9.25 KB/s` | Tốc độ gửi dữ liệu lên server |
| **Avg. Bytes** | `933.5 Bytes` | Kích thước dữ liệu trung bình của 1 response |

---

## 4. Đánh giá và Kết luận
1. **Độ tin cậy (Reliability):** Hệ thống đạt độ ổn định tuyệt đối với **Tỉ lệ lỗi Error % = 0.00%**.
2. **Thời gian phản hồi (Response Time):** Thời gian xử lý trung bình đạt **177 ms** (dao động từ 151 ms đến 223 ms). Độ lệch chuẩn thấp (**14.94**) chứng tỏ phản hồi giữa các request rất đều và không bị giật lag.
3. **Năng lực xử lý (Throughput):** Mức thông lượng đạt **83.1 request/giây**, đáp ứng tốt khối lượng tải 100 request thử nghiệm.

---

## 5. Hướng dẫn chạy lại file kịch bản (.jmx)
1. Cài đặt **Apache JMeter 5.6.3** và môi trường **Java JDK 17+**.
2. Mở JMeter, chọn **File > Open** và mở file `Summary Report.jmx`.
3. Nhấn nút **Start (mũi tên màu xanh)** trên thanh công cụ để chạy lại bài test.
