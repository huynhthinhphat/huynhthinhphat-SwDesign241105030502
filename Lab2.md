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
  - Biểu đồ sequence:\
     ![Diagram](https://www.planttext.com/api/plantuml/png/X991ReCm44NtFiLS81TWKKLAgggBIbMZ7620KUlAUCXu78cpTT4ZzGerCP2cWC82OVlDd-y__7nzRuEYQ6oSmKfPuB5f7NT4fkJeQvGEtgXbqUEpgTYhi1isTddbI0nvjTh1g_0dLVg27j-fIPjxL2mnq0ZaGcF67h1vcDIXI9-dI451CZQTJDIrPQ8FiMoiGYLMIImQT3fWIU0KhL20DZk2EXana9wPJj9UjNsnf6BfJ7EbzQhDijya5SLd0VArMR8o-2zW9uHAjqdyHM-3Uo9FCkDpSbFM1UnjQ1rs8sMurUjnzS4SKcJA4F0yIVLNNHdNuHzsPrxZT1SQtBlV44jVLb-oswPN_yl-0W00__y30000)
  - Biểu đồ lớp:\
![Diagram](https://www.planttext.com/api/plantuml/png/b5CzJiCm5DvzYgSiI4WTM3kWIfIXGm7nSm0tjP8WnmdECo92dHbOO6QXGXK22R4mrQeOqelu15m1jqtTqhGWFCJAPty_xxtaItysCgGILSm9sOBndT6t8WGHXECN2dxHzu4R_P0IdzCiW_quvKdE65mJiAi6h0HQpJgSe8n4K1u86ZC7zKZ9FsPf8j6nvVJrD4_P2dkQgKdHufFdt4nqAvYV26G2grP7CZbdFhQfe06BxHLBeXsQBRBx8PK1Er1nXyaL_tH6RZAa4SysrR5dlMN2EPCBJGTLEZ8hzW_9ivQJKb55GcLMLwGArqeVAbm-waq6sZRwFe8BHGM4Hjz041dz_cEmRgJUZWUrsYvuszvyJdN8YrS5lXa-Ar9YxfhTD_Uu3fdHRz0rUc2ZLDgrBEAyq0px2LmMZpQl6Ju9uCLeJJn7iRtwXyrlML6g7AwiwG01m-93182H8AHXlxZ9d_4D003__mC0)
    - Giải thích:
       - Employee:
          - Thuộc tính:
             - employeeID: Mã số duy nhất của nhân viên.
             - name: Tên của nhân viên.
          - Mối quan hệ:
             - Một Employee có thể yêu cầu nhiều Report (mối quan hệ 1 - nhiều), tức là mỗi nhân viên có thể tạo nhiều báo cáo khác nhau.
       - Report:
          - Thuộc tính:
             - reportType: Loại báo cáo (ví dụ: báo cáo tổng số giờ làm việc, báo cáo lương…).
             - startDate: Ngày bắt đầu của báo cáo.
             - endDate: Ngày kết thúc của báo cáo.
             - content: Nội dung của báo cáo.
          - Mối quan hệ:
             - Mỗi Report sẽ truy xuất dữ liệu từ ProjectManagementDatabase để tạo báo cáo (mối quan hệ 1 - 1). Điều này có nghĩa là mỗi báo cáo sẽ có thông tin liên quan đến một dự án hoặc mã chi phí duy nhất trong cơ sở dữ liệu quản lý dự án.
       - ProjectManagementDatabase:
          - Thuộc tính:
             - chargeNumber: Mã chi phí hoặc mã dự án.
             - projectDetails: Thông tin chi tiết về dự án hoặc công việc.
          - Mối quan hệ:
             - Cơ sở dữ liệu này chỉ liên kết với một báo cáo duy nhất tại một thời điểm (mối quan hệ 1 - 1 với Report), vì mỗi báo cáo có thể liên quan đến một mã chi phí hoặc một dự án duy nhất.
       - ReportController:
          - Thuộc tính:
             - controllerID: Mã số điều phối viên báo cáo.
             - reportDetails: Chi tiết về báo cáo mà controller đang quản lý.
          - Mối quan hệ:
             - ReportController quản lý việc tạo và điều phối một Report duy nhất (mối quan hệ 1 - 1). Điều này có nghĩa là mỗi controller sẽ xử lý một báo cáo cho mỗi yêu cầu của nhân viên.
       - ReportUI (Giao diện báo cáo):
          - Thuộc tính:
             - uiID: Mã số của giao diện báo cáo.
             - userInput: Dữ liệu đầu vào từ người dùng (nhân viên).
             - reportOutput: Kết quả báo cáo được xuất ra sau khi nhân viên gửi yêu cầu.
          - Mối quan hệ:
             - Một Employee sử dụng ReportUI để nhập các tiêu chí báo cáo và nhận kết quả báo cáo (mối quan hệ 1 - 1). Điều này có nghĩa là mỗi nhân viên sử dụng một giao diện báo cáo duy nhất.
2. Maintain Purchase Order
 - Các lớp phân tích của ca sử dụng Maintain Purchase Order:
    - Entity:
       - CommissionedEmployee: Đại diện cho nhân viên có hoa hồng, bao gồm employeeID, name, commissionRate.
       - PurchaseOrder: Đại diện cho đơn hàng, gồm purchaseOrderID, customerDetails, productList, date.
    - Boundary:
       - PurchaseOrderUI: Giao diện để nhân viên hoa hồng tạo, cập nhật hoặc xóa đơn hàng.
    - Control:
       - PurchaseOrderController: Xử lý các yêu cầu từ PurchaseOrderUI, tương tác với PurchaseOrder để thực hiện thêm, sửa, xóa đơn hàng.
  - Quan hệ giữa các lớp phân tích:
     - CommissionedEmployee và PurchaseOrder:
        - Loại mối quan hệ: Một - Nhiều.
        - Giải thích: Mỗi CommissionedEmployee có thể tạo và liên kết với nhiều PurchaseOrder. Nghĩa là một nhân viên nhận hoa hồng có thể ghi lại nhiều đơn hàng khác nhau liên quan đến các giao dịch bán hàng.
     - PurchaseOrder và PurchaseOrderController:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: PurchaseOrderController quản lý từng PurchaseOrder cho mỗi yêu cầu từ nhân viên. Đảm bảo việc tạo, cập nhật và xóa đơn hàng được thực hiện đúng quy trình.
     - CommissionedEmployee và PurchaseOrderUI:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: CommissionedEmployee tương tác với PurchaseOrderUI để thêm mới, cập nhật hoặc xóa thông tin đơn hàng. PurchaseOrderUI là giao diện mà nhân viên sử dụng để nhập thông tin và nhận phản hồi.
  - Biểu đồ sequence:\
     ![Diagram](https://www.planttext.com/api/plantuml/png/Z951IWD144NtVOfQwa9cFmi990gk38e7QBj_iA6xAwcgHkPiBZnIhf0P38gJ4TmMzL_z_-luyRbIysAjPEU3iT2QIqcgYIlYNTbd7W3togr6BmDjcuGthtYK27bvS86h2UVVy_NNC4CSgYMRoPnRka4tjtDwJy-eaGI71ZMwyZ5sYCcwY0m3yRHsxMQg2z2FdPxkMTwzV3FT7uiNZ9wsa1rBeKKJ_-PCePvWJUfeGLiUKsaB0QhTpgVS18jvbWhhQPDqd_rm9hdLMDRqnnC0003__mC0)
  - Biểu đồ lớp:\
![Diagram](https://www.planttext.com/api/plantuml/png/X9BTIWCn48NlynJ3NgdGQcyNAOMkXOAWL7o0a0pTG7xMp8HIn2VpmaVo5SnsLztMBju4vfpCTp93Fjy_5iGoSd9MA2k9O1cSCqGcUDHthh5XZmYl0W2mhzPL2KySZT-sgfSEXxNwwTz8pixA1idYJVJunnHLBGaVeiROSPkXT0nNYJWuZ1MoD9Q6LXE3Jehl3N49xNdRUVFMr8VeAfyZoS_hBbiRQgpShq9q5vUjG7NORP2IvLoVxrq6pp5O-_r-5J477QoEaHfzB6Yq-2jawjab5xC29fCv53VJwLLnigcoZxbsqiij_aEO5N_6BS5unYWLmyvmBKxzqTx1k2KGUWqHNn8IYx5hewXsYkwQ48jCQd_T5m000F__0m00)
    - Giải thích:
       - CommissionedEmployee
          - Thuộc tính:
             - employeeID: Mã số duy nhất của nhân viên.
             - name: Tên của nhân viên.
             - commissionRate: Tỷ lệ hoa hồng của nhân viên.
          - Mối quan hệ:
             - CommissionedEmployee có thể tạo và quản lý nhiều PurchaseOrder. Nghĩa là mỗi nhân viên có thể tạo hoặc quản lý nhiều đơn hàng trong hệ thống.
       - PurchaseOrder
          - Thuộc tính:
             - purchaseOrderID: Mã số của đơn hàng.
             - customerDetails: Thông tin chi tiết về khách hàng.
             - productList: Danh sách các sản phẩm trong đơn hàng.
             - date: Ngày tạo đơn hàng.
          - Mối quan hệ:
             - PurchaseOrder được tạo ra hoặc quản lý bởi CommissionedEmployee và chịu sự điều khiển của PurchaseOrderController.
       - PurchaseOrderUI
          - Thuộc tính:
             - displayForm(): Phương thức hiển thị form nhập liệu cho nhân viên.
             - showResult(): Phương thức hiển thị kết quả của các thao tác như tạo, sửa hoặc xóa đơn hàng.
          - Mối quan hệ:
             - PurchaseOrderUI tương tác với CommissionedEmployee. Nghĩa là mỗi nhân viên sẽ có một giao diện người dùng duy nhất để nhập thông tin và thao tác với đơn hàng.
             - PurchaseOrderUI gửi yêu cầu đến PurchaseOrderController để thực hiện các thao tác tạo, sửa hoặc xóa đơn hàng.
       - PurchaseOrderController
          - Thuộc tính:
             - createOrder(): Phương thức để tạo một đơn hàng mới.
             - updateOrder(): Phương thức để cập nhật hoặc sửa đổi một đơn hàng hiện tại.
             - deleteOrder(): Phương thức để xóa một đơn hàng.
          - Mối quan hệ:
             - PurchaseOrderController điều khiển các hành động liên quan đến đơn hàng. Nó nhận yêu cầu từ PurchaseOrderUI và thao tác với PurchaseOrder để thực hiện thêm, sửa hoặc xóa đơn hàng.
3. Login
 - Các lớp phân tích của ca sử dụng Maintain Purchase Order:
    - Entity:
       - User: Đại diện cho người dùng hệ thống, gồm các thuộc tính như userID, name, password.
    - Boundary:
       - LoginUI: Giao diện nơi người dùng nhập thông tin đăng nhập.
    - Control:
       - LoginController: Điều khiển việc xác thực thông tin đăng nhập từ LoginUI, tương tác với User để xác minh thông tin.
  - Quan hệ giữa các lớp phân tích:
     - User và LoginController:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: LoginController xử lý việc xác thực cho một User cụ thể khi đăng nhập vào hệ thống.
     - LoginController và LoginUI:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: LoginController nhận dữ liệu từ LoginUI để xử lý việc đăng nhập, phản hồi kết quả lại LoginUI.
     - User và LoginUI:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: User tương tác trực tiếp với LoginUI để nhập thông tin đăng nhập (tên người dùng và mật khẩu).
  - Biểu đồ sequence:\
     ![Diagram](https://www.planttext.com/api/plantuml/png/R91DYW9134RtEKLMeZ0oUnVI8hCGPki1OdNKXkgg8J-8PtFXaRo2rQrjuymiFvBtFfBRvLgfaPYt4IXO5jmg2vBYgakmovvgaZD-vqEJjXi8EPda-CZhHuWimCaQE_SqGC_YV3bGkC2lPCNhPPoePPpW3wcUijGmx0phexHWwhksiRLmtHLGrEcW-7WPPl2RAwh-Z0MIsx4Z0nbFHw2Vplzj53QNX2REd_jIo7_jRuSzzzL3ODM2DD65eU9KTq-z0m00__y30000)
  - Biểu đồ lớp:\
![Diagram](https://www.planttext.com/api/plantuml/png/Z9512i8m44NtESNGLGLJS5j42dLJS2SU86s31j9CIIQw44_cmYDv1TjWeROYxiBFdta_Fy_x8tCaBFb6iqeBv-3Wf8Kh0-3WksEnJM5FLfbZa8nev8VGTZCNjFL8112UJjAGgWJ9UEfOf50YQYaCkx4tT8T7PGx5YDk32jDw-agRtW0uNpQASYlh7YoqYuSjWsqvozebEQEg9p5oD6HHwuyQqj1B8BKMA-bSyFu76JqtjBjEaXagXMZ52VagOaCPd6z-sJ9fwlxRNW000F__0m00)
    - Giải thích:
      - User: Chịu trách nhiệm xác thực thông tin đăng nhập.
      - LoginUI: Là nơi tiếp nhận và gửi dữ liệu đầu vào từ người dùng.
      - LoginController: Kết nối giữa giao diện người dùng (LoginUI) và logic nghiệp vụ (User).
     - Mối quan hệ:
      - LoginController - User: Tương tác để xác thực thông tin người dùng.
      - LoginController - LoginUI: Điều phối thông tin giữa giao diện và logic.
      - User - LoginUI: Kết nối gián tiếp qua LoginController.
4. Create Administrative Report
 - Các lớp phân tích của ca sử dụng Maintain Purchase Order:
    - Entity:
       - PayrollAdministrator: Đại diện cho người quản trị hệ thống trả lương, gồm adminID, name, và các thông tin liên quan khác.
       - AdministrativeReport: Đại diện cho báo cáo quản trị, bao gồm các thuộc tính như reportType, startDate, endDate, content.
    - Boundary:
       - ReportUI: Giao diện mà người quản trị sử dụng để nhập yêu cầu tạo báo cáo, xem báo cáo, và thực hiện các thao tác liên quan đến báo cáo.
    - Control:
       - ReportController: Điều khiển quá trình tạo báo cáo, xử lý dữ liệu từ ReportUI, truy xuất dữ liệu từ hệ thống và cung cấp kết quả báo cáo.
  - Quan hệ giữa các lớp phân tích:
     - PayrollAdministrator và AdministrativeReport:
        - Loại mối quan hệ: Một - Nhiều.
        - Giải thích: PayrollAdministrator có thể tạo và xem nhiều AdministrativeReport khác nhau. Điều này có nghĩa là người quản trị có thể yêu cầu nhiều loại báo cáo, ví dụ như báo cáo tổng số giờ làm việc hoặc tổng lương trong năm.
     - AdministrativeReport và ReportController:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: ReportController tạo và quản lý từng AdministrativeReport dựa trên yêu cầu từ PayrollAdministrator, đảm bảo báo cáo được tạo chính xác và đúng định dạng.
     - PayrollAdministrator và ReportUI:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: PayrollAdministrator sử dụng ReportUI để gửi yêu cầu và xem báo cáo. ReportUI là giao diện cho phép nhập tiêu chí báo cáo và hiển thị kết quả.
     - ReportController và ReportUI:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: ReportController nhận thông tin đầu vào từ ReportUI, xử lý yêu cầu tạo báo cáo và gửi kết quả trở lại ReportUI để hiển thị cho PayrollAdministrator.
  - Biểu đồ sequence:\
     ![Diagram](https://www.planttext.com/api/plantuml/png/V991RW8n34NtEOMN89KBi41KfOlk4883X1chYfHnfeu3ojcww95wXJepC2rgO9VyV3_RN_d-_5f7iIofyyOs4XYsDdFm_hdj7BaeR8je8mo2EOP4hUKCE-m3o-7DD8542ox2otZpo0P9d6Ju0t8d75t632eiLXC7bl1AWWmy2FlSunCCessiw16fBGSp-QVQtvRAYEdOEHaVTlYHCChiCN5k_c4KNPjQyGsZbW3XkRvNjUm-xXq9LSBIM-EQpUy0whioIcAw15RPuZRTchl4U9rEBQsBlRVvwbbhGkLV_0000F__0m00)
  - Biểu đồ lớp:\
![Diagram](https://www.planttext.com/api/plantuml/png/h9FFJiCm3CRlUGghfo4jXrrxG4ECmsveWmS8hJL5QfFESITLY2VZm2Fn2ZH_MBkrS85BgtwsF__if9_l7sl7YhYjAr5KoZbuL1tPghehQssqOr9i2Lu5W0JbjUqcXpsJDeUW6LNZI00WFBReU8UD9LvGU3rrpJbf2Q7XHd4l-USIq9J3vqqE9wjByIOIq8X4dp3w9g2fUv2l6WJjeaTG2ciO3L_07z1WtmVlOsmnWOdjdxS9G9kcJQDEA49iFuCI0WzNF02kVQbrCjl59Vx7-gAX7yWVAtwVPT4IzHF6Q3wxv43La2tGkJy1pPhtWBDNJShROSivP2l9LguoSTQ6XD5GayHHp1VCNg9HqOyelnRModIPMFVp-l_d2m00__y30000)
    - Giải thích:
      - PayrollAdministrator và AdministrativeReport:
        - Một người quản trị có thể yêu cầu nhiều báo cáo khác nhau.
        - Quan hệ 1-nhiều, đảm bảo mỗi báo cáo có thể được liên kết với người yêu cầu.
      - AdministrativeReport và ReportController:
        - Một đối tượng AdministrativeReport được tạo ra và quản lý bởi ReportController.
        - Quan hệ 1-1, mỗi báo cáo chỉ được tạo từ một yêu cầu cụ thể.
      - PayrollAdministrator và ReportUI:
        - Người quản trị sử dụng giao diện để thực hiện các thao tác liên quan đến báo cáo.
        - Quan hệ 1-1, vì mỗi người dùng chỉ tương tác với một phiên giao diện tại một thời điểm.
      - ReportController và ReportUI:
        - ReportController nhận thông tin từ ReportUI, xử lý và gửi kết quả.
        - Quan hệ 1-1, vì mỗi yêu cầu từ giao diện cần một phiên xử lý riêng.
5. Maintain Employee Information
 - Các lớp phân tích của ca sử dụng Maintain Purchase Order:
    - Entity:
       - Employee: Đại diện cho thông tin của nhân viên, gồm employeeID, name, address, classification, và các thông tin khác liên quan đến hồ sơ nhân viên.
    - Boundary:
       - EmployeeManagementUI: Giao diện cho phép người quản trị hoặc người dùng có thẩm quyền thực hiện các thao tác thêm mới, cập nhật, hoặc xóa thông tin nhân viên.
    - Control:
       - EmployeeController: Điều khiển việc xử lý các yêu cầu từ EmployeeManagementUI, quản lý việc thêm, cập nhật và xóa thông tin của Employee.
  - Quan hệ giữa các lớp phân tích:
     - Employee và EmployeeController:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: EmployeeController xử lý các thao tác liên quan đến một Employee cụ thể trong hệ thống, như thêm mới hoặc cập nhật thông tin.
     - EmployeeController và EmployeeManagementUI:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: EmployeeController nhận thông tin từ EmployeeManagementUI và thực hiện các hành động theo yêu cầu của người dùng.
     - Employee và EmployeeManagementUI:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: Employee có thể được thêm mới hoặc chỉnh sửa qua EmployeeManagementUI bởi người dùng có thẩm quyền.
  - Biểu đồ sequence:\
     ![Diagram](https://www.planttext.com/api/plantuml/png/n9J1JW8n48RlVOevGW8lOB860XmuU559l9Psa2Rj5DjP2Q_ZaSIJDprus2Vn2Nm5ouAxH9P4ZD5Jqqp__v__E_JzvRKNMGREdHLIiG_GrywGcFgSj0mh6Bc5zIl42qdo5XqIJyP2UUBWRJKSREyMWqWF3DSo8R8ChkV5sW7DYmU2UrEi2R9Cb3dGFMzCW3CO4MC0t0r18qjZesXylUTIhv8yOZvrXljQN-9TZf5RdtP3oR8j6ZHxJacl0af685pMXQfnzrXgGCu3fN2bCCR6bEEruzml8V6TcU0a6qybmS7Ry-CY4Km7dmfoij2R4hz1Sclr5UPus84JmUQbqPXcVjUoHT9X1wJM8J7hWB8oHZCpgfos_uVwJV4aJwLzXHOLrxJP9-0M6N_2UrWg3tb_W_0sjDhZxm7saFJcL_a0003__mC0)
  - Biểu đồ lớp:\
![Diagram](https://www.planttext.com/api/plantuml/png/d9DDQiCm48NtEiMGLGfs85jZGahTXHVPfEG0qsWI1FfnfN6Wb9wiYnwfLoXHwaPn_aXMGZDw7--Df9-lxsbWzDmQBPOQGu1dqsZtJWGV0Y07-jlMLG4lx9LTnx95GmS5bD9J20Ur25GhjKHMpYOjWBQHo5JRbVCcTeSfCUlZiZEiXm8sJadnANhkPsXnJOOiB-fUaWeP2vXXKtRitJg9naBxQXG_IZcdjvO23w_AEWzxzIA6wmFs4yokUpc6LgJf4lJiA9wSPU-q9Xy70TlPThtRqkqkxKXxTp0P8rtW9Pd-dsKv6fsALi1WdBFBnmDnyWta-UGUMPdgqjDJidBxQNu1003__mC0)
    - Giải thích:
      - Employee và EmployeeController:
        - EmployeeController quản lý tất cả các thao tác liên quan đến đối tượng Employee.
        - Quan hệ 1-1, mỗi yêu cầu quản lý chỉ áp dụng cho một nhân viên cụ thể.
      - EmployeeController và EmployeeManagementUI:
        - EmployeeManagementUI là giao diện, trong khi EmployeeController chịu trách nhiệm thực hiện logic nghiệp vụ.
        - Quan hệ 1-1, mỗi giao diện chỉ gửi thông tin cho một phiên điều khiển.
      - Employee và EmployeeManagementUI:
        - Giao diện cho phép người dùng nhập và xem thông tin nhân viên.
        - Quan hệ 1-1, mỗi thao tác từ giao diện áp dụng trên một nhân viên.
6. Run Payroll
 - Các lớp phân tích của ca sử dụng Maintain Purchase Order:
    - Entity:
       - Employee: Đại diện cho các nhân viên cần được tính lương.
       - PayrollRecord: Ghi nhận thông tin chi tiết về quá trình tính lương, gồm recordID, employeeID, payAmount, payDate, và các chi tiết khác.
    - Boundary:
       - PayrollUI: Giao diện báo cáo và hiển thị trạng thái trả lương.
    - Control:
       - PayrollProcessor: Điều khiển quá trình xử lý lương, tính toán các khoản chi trả cho nhân viên, dựa trên thông tin từ Employee và PayrollRecord.
  - Quan hệ giữa các lớp phân tích:
     - Employee và PayrollRecord:
        - Loại mối quan hệ: Một - Nhiều.
        - Giải thích: Mỗi Employee có thể có nhiều PayrollRecord ghi nhận các kỳ trả lương khác nhau.
     - PayrollProcessor và PayrollRecord:
        - Loại mối quan hệ: Một - Nhiều.
        - Giải thích: PayrollProcessor xử lý và cập nhật từng PayrollRecord để đảm bảo lương được tính chính xác.
     - PayrollProcessor và PayrollUI:
        - Loại mối quan hệ: Một - Một.
        - Giải thích: PayrollProcessor giao tiếp với PayrollUI để hiển thị kết quả sau khi xử lý lương.
  - Biểu đồ sequence:\
     ![Diagram](https://www.planttext.com/api/plantuml/png/X54nRW8n4Ept5Lj2mGSYNKIKf4Y7G3p0iLTmaczzhDUA_1n4co8rAL94uX-y85-8my591A9K8y_EQ6RNN-yVuwX6D3KUZDKWUEUQci46LWaU9oONy1C9bc8C0iHQQyR7flKX4vtUHzsKR107po6nCzBJyoU0giBxvNwxphXA6LK-NtbPOB_TeD-zxTQymAg2GpgERY-2yGQdYR7jQ6mx7YvanNhgLYmBqfdnfSa3gQbz70oXduwkfmXf4iPuiA7hV5TppdOkJYjab93fvTSvpeN_v2RxvsBzDOlSrR7r9X-fMMgQKdSGEnp2cDZz_Eat0000__y30000)
  - Biểu đồ lớp:\
![Diagram](https://www.planttext.com/api/plantuml/png/d9BFQeGm4CRlFiNWIQ4UzYf5jc0B2pr8fGymQ10X_qZYGbZwP3tqaVeAZJ6wpIxsq8iuNsRo_MOctvzVHsrGcOdHfAEeDJmpIOKb12u9G04aXAUwXDQeaGzUviX896Yag6m9BrIWSGh0G4phnPeO7AdEylNq8mbU3LebA7qZdL1zC5G-kB7ReP1edvYOkBdwUh56u-ZchoUPPEz-dTbASblt41SvqBCO-plEzrDWb4lSJepvfZSaW7xKag9jeenCnvbx1eqI7T5QgDXdcOykuNNKvZ4QMkLDvL8NJh9rMdDwA5gtMkNxjmo44xKCwZUx-iCzttfthMml9psaK1GLf0ovJUCj9tUj_ZFxa5xNaXm9x-Sd_0C00F__0m00)
    - Giải thích:
      - Employee và PayrollRecord:
        - Mỗi nhân viên có thể liên kết với nhiều bản ghi trả lương để lưu trữ lịch sử.
        - Quan hệ 1-nhiều.
      - PayrollProcessor và PayrollRecord:
        - PayrollProcessor chịu trách nhiệm tạo và cập nhật bản ghi trả lương.
        - Quan hệ 1-nhiều, mỗi phiên xử lý tạo nhiều bản ghi.
      - PayrollProcessor và PayrollUI:
        - PayrollProcessor gửi kết quả tóm tắt tới giao diện để hiển thị.
        - Quan hệ 1-1, mỗi phiên xử lý tương ứng với một báo cáo.

Code Java mô phỏng ca sử dụng Maintain Timecard:

**CommissionedEmployee.java**

    public class CommissionedEmployee {
        private String employeeID;
        private String name;
        private float commissionRate;

    public CommissionedEmployee(String employeeID, String name, float commissionRate) {
        this.employeeID = employeeID;
        this.name = name;
        this.commissionRate = commissionRate;
    }

    // Getters and setters
    public String getEmployeeID() {
        return employeeID;
    }

    public void setEmployeeID(String employeeID) {
        this.employeeID = employeeID;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public float getCommissionRate() {
        return commissionRate;
    }

    public void setCommissionRate(float commissionRate) {
        this.commissionRate = commissionRate;
    }
}

**PurchaseOrder.java**

    public class PurchaseOrder {

    private String purchaseOrderID;
    private String customerDetails;
    private List<String> productList;
    private Date date;
    
    public PurchaseOrder(String purchaseOrderID, String customerDetails, List<String> productList, Date date) {
        this.purchaseOrderID = purchaseOrderID;
        this.customerDetails = customerDetails;
        this.productList = productList;
        this.date = date;
    }

    // Getters and setters
    public String getPurchaseOrderID() {
        return purchaseOrderID;
    }

    public void setPurchaseOrderID(String purchaseOrderID) {
        this.purchaseOrderID = purchaseOrderID;
    }

    public String getCustomerDetails() {
        return customerDetails;
    }

    public void setCustomerDetails(String customerDetails) {
        this.customerDetails = customerDetails;
    }

    public List<String> getProductList() {
        return productList;
    }

    public void setProductList(List<String> productList) {
        this.productList = productList;
    }

    public Date getDate() {
        return date;
    }

    public void setDate(Date date) {
        this.date = date;
    }
    }


**PurchaseOrderUI.java**

    public class PurchaseOrderUI {
    public void displayForm() {
        System.out.println("Displaying purchase order form...");
    }

    public void showResult(String result) {
        System.out.println("Operation result: " + result);
    }
    }

**PurchaseOrderController.java**

    public class PurchaseOrderController {
        private Map<String, PurchaseOrder> purchaseOrderDatabase = new HashMap<>();

    public String createOrder(PurchaseOrder order) {
        if (purchaseOrderDatabase.containsKey(order.getPurchaseOrderID())) {
            return "Order already exists.";
        }
        purchaseOrderDatabase.put(order.getPurchaseOrderID(), order);
        return "Order created successfully.";
    }

    public String updateOrder(String orderID, PurchaseOrder updatedOrder) {
        if (!purchaseOrderDatabase.containsKey(orderID)) {
            return "Order not found.";
        }
        purchaseOrderDatabase.put(orderID, updatedOrder);
        return "Order updated successfully.";
    }

    public String deleteOrder(String orderID) {
        if (!purchaseOrderDatabase.containsKey(orderID)) {
            return "Order not found.";
        }
        purchaseOrderDatabase.remove(orderID);
        return "Order deleted successfully.";
    }
    }

**Main.java**

    public class Main {
        public static void main(String[] args) {
            CommissionedEmployee employee = new CommissionedEmployee("E123", "John Doe", 0.15f);
            PurchaseOrderUI ui = new PurchaseOrderUI();
            PurchaseOrderController controller = new PurchaseOrderController();

        // Employee interacts with UI to create a purchase order
        ui.displayForm();
        PurchaseOrder order = new PurchaseOrder(
                "PO001",
                "Customer A",
                Arrays.asList("Product 1", "Product 2"),
                new Date()
        );
        String result = controller.createOrder(order);
        ui.showResult(result);

        // Update the order
        order.setCustomerDetails("Updated Customer A");
        result = controller.updateOrder("PO001", order);
        ui.showResult(result);

        // Delete the order
        result = controller.deleteOrder("PO001");
        ui.showResult(result);
    }
    }
