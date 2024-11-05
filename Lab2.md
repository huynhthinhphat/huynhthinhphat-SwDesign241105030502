Tiến hành phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System.
- Create Employee
   - Các lớp phân tích của ca sử dụng Create Employee:
    - Entity:
     - Employee: 
     - Report: Lưu thông tin cơ bản của báo cáo như Loại báo cáo (Tổng giờ làm việc, Tổng giờ làm việc cho một dự án, Nghỉ phép/Nghỉ ốm, Tổng lương tính đến nay), Ngày bắt đầu và Ngày kết thúc.
     - CreateEmployeeRecord: Lưu báo cáo.
    - Boundary:
     - CreateEmployeeUI
    - Control:
     - CreateEmployeeController
  - Quan hệ giữa các lớp phân tích:
  - Biểu đồ sequence:
    ![Diagram]()
  - Biểu đồ lớp:
  ![Diagram]()
    - Giải thích:
- Maintain Purchase Order
- Login
- Create Administrative Report
- Maintain Employee Information
- Run Payroll
