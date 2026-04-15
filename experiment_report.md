# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600001
**Name:** Bùi Cao Chinh
**Date:** 15/04/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 10 | Dữ liệu sạch, đầy đủ và hợp lý nên Agent trả lời đúng. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 1 | Dữ liệu lỗi, sai kiểu và có outlier làm kết quả bị sai nghiêm trọng. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent trả lời sai vì Garbage Data làm mờ cái nhìn về dữ liệu đầu vào. Khi có Duplicate IDs, một sản phẩm có thể bị đếm nhiều lần, khiến Agent đánh giá sai độ phổ biến hoặc mức độ ưu tiên của nó. Wrong data types như giá trị số bị lưu thành chuỗi, hoặc cột giá bị sai định dạng, làm các phép so sánh và tính toán không còn chính xác. Outliers như Nuclear Reactor với giá quá lớn tạo ra các giá trị bất thường, có thể kéo mô hình hoặc logic lựa chọn lệch khỏi thực tế. Null values làm thiếu thông tin cần thiết để Agent suy luận, nên nó có thể bù thông tin sai hoặc đưa ra đáp án không phù hợp với bộ dữ liệu.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

Đồng ý. Một prompt tốt vẫn có thể trả về kết quả sai nếu dữ liệu đầu vào kém chất lượng. Ngược lại, dữ liệu sạch và được xử lý đúng giúp Agent suy luận ổn định hơn, giảm sai số và tạo ra đáp án thực tế hơn.
