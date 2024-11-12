Tiến hành phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System.
1. Create Employee
   - Các lớp phân tích của ca sử dụng Create Employee:
    - Entity:
       - Employee: Lớp này đại diện cho nhân viên yêu cầu báo cáo và chứa thông tin nhân viên như employeeID, name.
       - Report: Lưu trữ thông tin về các loại báo cáo được tạo, bao gồm các thuộc tính như reportType, startDate, endDate, và content.
       - ProjectManagementDatabase: Cơ sở dữ liệu chứa các thông tin về số mã chi phí (charge numbers) để phục vụ cho báo cáo dự án.
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
2. Maintain Purchase Order
3. Login
4. Create Administrative Report
5. Maintain Employee Information
6. Run Payroll
