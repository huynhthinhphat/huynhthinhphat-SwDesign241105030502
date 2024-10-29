**LAB 1: PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG**

1. **Phân tích kiến trúc**
   - Đề xuất kiến trúc: Model - view - controller (MVC)
   - Lý do: Vì nó hỗ trợ tính linh hoạt, khả năng mở rộng, và dễ dàng bảo trì hệ thống khi có nhu cầu.
     + Phân tách rõ ràng các thành phần: Tách biệt các thành phần giúp hệ thống dễ bảo trì, mở rộng và cải thiện khi cần mà không ảnh hưởng đến các phần khác.
     + Dễ dàng bảo trì và mở rộng: Mỗi thành phần hoạt động độc lập, nên khi thay đổi một phần như View, logic Model, hoặc Controller không ảnh hưởng đến các phần còn lại.
     + Khả năng mở rộng: Khi có nhu cầu mở rộng chức năng, MVC cho phép thêm các View mới để cung cấp các tính năng khác mà không làm gián đoạn các thành phần khác.
     + Tái sử dụng mã nguồn: Các thành phần trong kiến trúc MVC có tính tái sử dụng cao, đặc biệt khi mở rộng hệ thống hoặc tích hợp với các hệ thống khác.
   - Ý nghĩa từng thành phần: Gồm 3 thành phần chính:\
         1. Model: Mô hình đại diện cho dữ liệu và logic kinh doanh của ứng dụng. Nó chứa các đối tượng, lớp và phương thức để xử lý dữ liệu, thường bao gồm việc truy xuất và lưu trữ dữ liệu từ cơ sở dữ liệu.\
         2. View: là phần hiển thị của ứng dụng, nơi người dùng tương tác với ứng dụng. Nó nhận dữ liệu từ mô hình và hiển thị chúng một cách trực quan.\
         3. Controller: là cầu nối giữa mô hình và view. Nó nhận các yêu cầu từ view (chẳng hạn như tương tác của người dùng), xử lý chúng, và sau đó cập nhật mô hình hoặc view theo nhu cầu.
   - Vẽ biểu đồ package mô tả kiến trúc:
     ![Diagram](https://www.planttext.com/api/plantuml/png/R96zIWGn58NxFCKb_Rw0XIo8Q3CWk0YMOUQw4pS_Q-OEEeYLXOMFOI48OZz1jjWdoHFu2YQhp6QOhGBdEpddtkJ7R-OD2KUjLapX3G5PS79P4rJIOKdI6iRMebo99G8lR8MAmoC3A9Le6ZZLQsKxn45OI8sbSDKWN8XEew42gRQPwknjJ2-4YRc9NtODeMPFMTc9DUIiKkZonfYNn3sSL1z0_qDa92-wadX_QAcaJz97ucYv7OcvwOJPx1ZsTN04_2puJmdTzgE5ClJlBMSPJ_RTuoRdzU21XtW9rFQRipywZetUXGlz6rJ1Vu6ImRzCOzCuqNWUwRC1geD_XLNeDmHtRRpBsHnDbRx_5m00__y30000)

     
**2. Cơ chế phân tích**

   
**3. Phân tích ca sử dụng Payment**
- Các lớp phân tích của ca sử dụng Payment:
  + Employee (Nhân viên):
    * Nhiệm vụ: Lớp này đại diện cho nhân viên trong hệ thống và chứa thông tin của họ bao gồm phương thức thanh toán.
    * Thuộc tính: employeeID, employeeName, employeeAddress, employeeNumberPhone, paymentMethod
  + PaymentMethod (Phương thức thanh toán):
    * Nhiệm vụ: Đại diện cho phương thức thanh toán được chọn bởi nhân viên. Có ba loại phương thức: Pick-up, Mail, và Direct Deposit.
    * Thuộc tính: paymentType, bankAccount, address
  + PaymentSystem (Hệ thống thanh toán):
    * Nhiệm vụ: Chịu trách nhiệm lưu trữ và cập nhật thông tin phương thức thanh toán của nhân viên.
    * Thuộc tính: paymentInfo
- Quan hệ giữa các lớp phân tích:
  * Employee: Có quan hệ với PaymentMethod qua thuộc tính paymentMethod.
  * PaymentMethod: Có các lớp con cụ thể như Pick-up, Mail, và DirectDeposit để quản lý các kiểu phương thức thanh toán khác nhau.
  * PaymentSystem: Liên kết với Employee và quản lý phương thức thanh toán của nhân viên.
- Biểu đồ\
    ![Diagram](https://www.planttext.com/api/plantuml/png/R90n3i8m34LtdyBgL8PUW04nmC1G2GakOBKVY4YJqBYLUZO6ZiGLY00L5NMq_T-pvUVziOughNQD9OfNuxZr4KHgr8Ap4Z7A6P4BFk3MmLNWZP5pAqr699NwbhTDi7u0c48IcSe4SShPNeO6JWz3LAJmtAo4NdoTHAEYMF64uoL7M5Gw8VBmgOv3m8AcmC_moIP3BzRKelZsT-xayn7xfcOMlx5ynZzUcuwJ_azBQxWwVVC5003__mC0)\
      * Giải thích:
     1. Nhân viên tương tác với hệ thống để chọn phương thức thanh toán.
     2. Hệ thống yêu cầu thông tin thanh toán dựa trên phương thức đã chọn.
     3. Nhân viên nhập thông tin (địa chỉ hoặc thông tin tài khoản ngân hàng).
     4. Hệ thống kiểm tra tính hợp lệ của thông tin thanh toán.
     5. Hệ thống lưu thông tin phương thức thanh toán đã cập nhật.\
        
**4. Phân tích ca sử dụng Maintain Timecard**
- Các lớp phân tích của ca sử dụng Payment:
   + Employee (Nhân viên):
     * Nhiệm vụ: Nhân viên nhập và cập nhật thông tin thời gian làm việc.
     * Thuộc tính: employeeID, name, timecard
   + Timecard (Bảng chấm công):
     * Nhiệm vụ: Lưu trữ thông tin về giờ làm việc của nhân viên cho kỳ lương hiện tại.
     * Thuộc tính: timecardID, hoursWorked, chargeNumbers, status
   + ProjectManagementSystem (Hệ thống quản lý dự án):
     * Nhiệm vụ: Cung cấp các mã dự án (charge numbers) mà nhân viên có thể chọn khi nhập giờ làm việc.
     * Thuộc tính: chargeNumbers
   + PayrollSystem (Hệ thống quản lý tiền lương):
     * Nhiệm vụ: Nhận bảng chấm công đã nộp và xử lý thanh toán cho nhân viên.
- Quan hệ giữa các lớp phân tích:
     * Employee: Có quan hệ với Timecard qua thuộc tính timecard.
     * Timecard: Liên kết với ProjectManagementSystem để lấy thông tin mã dự án.
     * PayrollSystem: Liên kết với Timecard để xử lý bảng chấm công.
- Biểu đồ\
    ![Diagram](https://www.planttext.com/api/plantuml/png/T95DIWD148NtTOfYLWRC1Ln8G0KtaK2yGANdCMdjdx6wHfYpkV18Ni5sCM4wuFRnVUyrNJzVtxjYeZR5G5JUVMBD1KJcBO2xFKgH0OMtVCJ7XEJ0Zru6bTWHYREi_1J7a6U0QQn5tlbHad5tqFm6Ptj9jI0YsN4kXgerrAkFSABzLNoGMNC8YqANZUqz_rFCTpp07iwY0rwcU8AMcqqZBbkLh1RqEK-LSIlZbiz_sOOkQAjzIl2z69ReQg1vTSNBT8hULd0BjDsZPbT_UqNJ3gclX_a5003__mC0)\
      * Giải thích:
     1. Employee và Timecard: Một nhân viên có thể có một hoặc nhiều bảng chấm công, nhưng tại một thời điểm chỉ có một bảng chấm công hiện tại (mối quan hệ 1-1).
     2. Timecard và ProjectManagementSystem: Timecard phụ thuộc vào ProjectManagementSystem để nhận các mã dự án hợp lệ.
     3. PayrollSystem và Timecard: PayrollSystem sẽ xử lý bảng chấm công sau khi nó được nộp bởi nhân viên.\
 
**5. Hợp nhất kết quả phân tích**
