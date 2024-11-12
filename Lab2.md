Tiến hành phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System.
1. Create Employee Report
   - Các lớp phân tích của ca sử dụng Create Employee:
    - Entity:
       - Employee: Lớp này đại diện cho nhân viên yêu cầu báo cáo và chứa thông tin nhân viên như employeeID, name.
       - Report: Lưu trữ thông tin về các loại báo cáo được tạo, bao gồm các thuộc tính như reportType, startDate, endDate, và content.
       - ProjectManagementDatabase: Cơ sở dữ liệu chứa các thông tin về số mã chi phí (charge numbers) để phục vụ cho báo cáo dự án.
    - Boundary:
       - ReportUI: Giao diện mà nhân viên sử dụng để chọn loại báo cáo, nhập thông tin thời gian, và lưu báo cáo nếu cần.
    - Control:
       - ReportController: Điều phối quá trình tạo báo cáo. Nó lấy thông tin từ ReportUI, truy xuất dữ liệu từ ProjectManagementDatabase, xử lý yêu cầu báo cáo và gửi kết quả về ReportUI.
  - Quan hệ giữa các lớp phân tích:
     - Employee và Report:
        - Loại mối quan hệ: Một - Nhiều.
        - Giải thích: Mỗi Employee có thể tạo và liên kết với nhiều Report. Điều này có nghĩa là một nhân viên có thể yêu cầu nhiều báo cáo khác nhau, chẳng hạn như báo cáo tổng số giờ làm việc, giờ làm cho một dự án cụ thể, thời gian nghỉ phép, hoặc tổng lương năm.
     - Report và ProjectManagementDatabase:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: Report có thể truy cập thông tin từ ProjectManagementDatabase khi cần thiết để tạo báo cáo liên quan đến các dự án. 
     - ReportController và Report:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: ReportController tạo ra và quản lý một Report cho mỗi yêu cầu báo cáo từ Employee. Nó chịu trách nhiệm thu thập thông tin, xử lý dữ liệu và đảm bảo báo cáo được tạo đúng theo yêu cầu của nhân viên.
     - Employee và ReportUI:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: Employee tương tác với ReportUI để gửi yêu cầu và nhận thông tin báo cáo. ReportUI là giao diện nơi nhân viên nhập các tiêu chí báo cáo và nhận kết quả, tạo ra một mối liên kết rõ ràng giữa người dùng và giao diện đầu vào.
     - ReportController và ProjectManagementDatabase:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: ReportController kết nối với ProjectManagementDatabase để lấy thông tin cần thiết về mã chi phí khi nhân viên yêu cầu báo cáo.
  - Biểu đồ sequence:
    ![Diagram](https://www.planttext.com/api/plantuml/png/X991ReCm44NtFiLS81TWKKLAgggBIbMZ7620KUlAUCXu78cpTT4ZzGerCP2cWC82OVlDd-y__7nzRuEYQ6oSmKfPuB5f7NT4fkJeQvGEtgXbqUEpgTYhi1isTddbI0nvjTh1g_0dLVg27j-fIPjxL2mnq0ZaGcF67h1vcDIXI9-dI451CZQTJDIrPQ8FiMoiGYLMIImQT3fWIU0KhL20DZk2EXana9wPJj9UjNsnf6BfJ7EbzQhDijya5SLd0VArMR8o-2zW9uHAjqdyHM-3Uo9FCkDpSbFM1UnjQ1rs8sMurUjnzS4SKcJA4F0yIVLNNHdNuHzsPrxZT1SQtBlV44jVLb-oswPN_yl-0W00__y30000)
  - Biểu đồ lớp:
  ![Diagram](https://www.planttext.com/api/plantuml/png/b5CzJiCm5DvzYgSiI4WTM3kWIfIXGm7nSm0tjP8WnmdECo92dHbOO6QXGXK22R4mrQeOqelu15m1jqtTqhGWFCJAPty_xxtaItysCgGILSm9sOBndT6t8WGHXECN2dxHzu4R_P0IdzCiW_quvKdE65mJiAi6h0HQpJgSe8n4K1u86ZC7zKZ9FsPf8j6nvVJrD4_P2dkQgKdHufFdt4nqAvYV26G2grP7CZbdFhQfe06BxHLBeXsQBRBx8PK1Er1nXyaL_tH6RZAa4SysrR5dlMN2EPCBJGTLEZ8hzW_9ivQJKb55GcLMLwGArqeVAbm-waq6sZRwFe8BHGM4Hjz041dz_cEmRgJUZWUrsYvuszvyJdN8YrS5lXa-Ar9YxfhTD_Uu3fdHRz0rUc2ZLDgrBEAyq0px2LmMZpQl6Ju9uCLeJJn7iRtwXyrlML6g7AwiwG01m-93182H8AHXlxZ9d_4D003__mC0)
    - Giải thích:
2. Maintain Purchase Order
3. Login
4. Create Administrative Report
5. Maintain Employee Information
6. Run Payroll
