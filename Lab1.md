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
 - Persistency (Lưu trữ lâu dài):
   + Mô tả: Hệ thống cần có cơ chế để đảm bảo dữ liệu như thông tin nhân viên, bảng lương và các dữ liệu liên quan được lưu trữ an toàn và tồn tại lâu dài, ngay cả khi ứng dụng tắt.
   + Lý do: Để đảm bảo rằng dữ liệu quan trọng không bị mất và có thể được truy xuất khi cần thiết.
 - Distribution (Phân phối):
   + Mô tả: Hệ thống sẽ phân phối logic nghiệp vụ trên nhiều nút trong hệ thống, cho phép xử lý đồng thời.
   + Lý do: Điều này giúp tăng tốc độ xử lý tính toán lương cho nhiều nhân viên, giảm thiểu quá tải cho một máy chủ duy nhất và nâng cao hiệu suất tổng thể.
 - Security (Bảo mật):
   + Mô tả: Cần thiết lập các biện pháp bảo mật để chỉ những nhân viên có quyền mới có thể truy cập và chỉnh sửa thông tin cá nhân của họ và thông tin nhạy cảm như bảng lương.
   + Lý do: Để bảo vệ dữ liệu nhạy cảm khỏi truy cập trái phép, đảm bảo rằng chỉ những người dùng hợp lệ mới có quyền thao tác trên thông tin cá nhân.
 - Legacy Interface (Giao diện hệ thống kế thừa):
   + Mô tả: Hệ thống mới cần có khả năng giao tiếp với hệ thống quản lý dự án hiện có mà công ty không muốn thay thế.
   + Lý do: Để duy trì tính tương thích và tích hợp với các hệ thống cũ, cần có một giao diện chắc chắn giữa hệ thống mới và cũ nhằm đảm bảo dữ liệu được truyền tải đúng và đầy đủ.
 - Data Validation (Kiểm tra tính hợp lệ dữ liệu):
   + Mô tả: Cần có cơ chế để kiểm tra tính hợp lệ của thông tin đầu vào từ người dùng, như thông tin ngân hàng và bảng chấm công.
   + Lý do: Để tránh lỗi và đảm bảo rằng thông tin được nhập vào hệ thống là chính xác, từ đó cải thiện chất lượng dữ liệu và giảm thiểu rủi ro trong xử lý thanh toán.
 - Audit Logging (Ghi nhật ký kiểm tra):
   + Mô tả: Hệ thống cần ghi lại các hành động quan trọng liên quan đến dữ liệu nhạy cảm, như cập nhật thông tin nhân viên hoặc thay đổi phương thức thanh toán.
   + Lý do: Để có thể theo dõi và truy cứu lại các thay đổi trong hệ thống, tăng cường tính minh bạch và phát hiện các hành vi đáng ngờ.
   
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
    + Employee và PaymentMethod:
      * Loại mối quan hệ: Một - Một
      * Giải thích: Mỗi nhân viên sẽ có một phương thức thanh toán cụ thể. Ví dụ, nhân viên chỉ chọn một trong các phương thức như Pick-up, Mail, hoặc Direct Deposit.
    + PaymentMethod và các lớp con (Pick-up, Mail, DirectDeposit):
      * Loại mối quan hệ: Một - Nhiều
      * Giải thích: Lớp PaymentMethod có thể có nhiều loại phương thức thanh toán, nhưng mỗi phương thức đều thuộc về PaymentMethod.
    + PaymentSystem và Employee:
      * Loại mối quan hệ: Một - Nhiều
      * Giải thích: Một hệ thống thanh toán sẽ quản lý thông tin thanh toán cho nhiều nhân viên.
    
- Biểu đồ sequence:\
    ![Diagram](https://www.planttext.com/api/plantuml/png/R90n3i8m34LtdyBgL8PUW04nmC1G2GakOBKVY4YJqBYLUZO6ZiGLY00L5NMq_T-pvUVziOughNQD9OfNuxZr4KHgr8Ap4Z7A6P4BFk3MmLNWZP5pAqr699NwbhTDi7u0c48IcSe4SShPNeO6JWz3LAJmtAo4NdoTHAEYMF64uoL7M5Gw8VBmgOv3m8AcmC_moIP3BzRKelZsT-xayn7xfcOMlx5ynZzUcuwJ_azBQxWwVVC5003__mC0)\
- Biểu đồ lớp:\
  ![Diagram](https://www.planttext.com/api/plantuml/png/R55B3e8m4Dtt5Br0Bq2CaGGNB30awW66TXH2Vw5bGTIJkV18Ni4GAx4Divlttinxata_NpldOV2ZaeHBS8xkbPLcGgGtGkV2q9T5t1z0OOpaGWpeN28RLOD3tHeTr1OcXTfNw5iZo8C4s_eV_da7xMcoORW1tUUScr7xBm31Czrpd9n7bUmfzSNCokL4nhQ9SPRaYzdDdJ5QTxm_spMcWawkuKKt8FS5MkCwJ-A4SuGbJqOLQBYY8plKOlx91m00__y30000)
    + Giải thích:
      1. Employee:
         * Đại diện cho nhân viên trong hệ thống.
         * Các thuộc tính bao gồm employeeID, employeeName, employeeAddress, employeeNumberPhone, và paymentMethod (liên kết tới phương thức thanh toán).
      2. PaymentMethod:
         * Đại diện cho phương thức thanh toán mà nhân viên chọn.
         * Có các thuộc tính như paymentType, bankAccount, và address.
      3. PaymentSystem:
         * Chịu trách nhiệm quản lý thông tin thanh toán của nhân viên.
         * Có thuộc tính paymentInfo để lưu trữ dữ liệu thanh toán.
      4. Quan hệ:
         * Employee có mối quan hệ với PaymentMethod thông qua thuộc tính paymentMethod, nghĩa là mỗi nhân viên sẽ có một phương thức thanh toán cụ thể.
         * PaymentMethod có các lớp con như PickUp, Mail, và DirectDeposit, mỗi lớp con đại diện cho một phương thức thanh toán cụ thể.
         * PaymentSystem liên kết với Employee, cho thấy rằng hệ thống thanh toán sẽ quản lý các thông tin liên quan đến nhân viên.
        
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
    + Employee và Timecard:
       * Loại mối quan hệ: Một - Nhiều
       * Giải thích: Mỗi nhân viên có thể có nhiều bảng chấm công, nhưng tại một thời điểm chỉ có một bảng chấm công hiện tại. Mối quan hệ này cho phép nhân viên nhập nhiều giờ làm việc qua các kỳ lương khác nhau.
    + Timecard và ProjectManagementSystem:
       * Loại mối quan hệ: Nhiều - Một
       * Giải thích: Nhiều bảng chấm công có thể sử dụng thông tin mã dự án từ hệ thống quản lý dự án, nhưng một mã dự án chỉ có thể thuộc về một bảng chấm công tại một thời điểm.
    + PayrollSystem và Timecard:
       * Loại mối quan hệ: Một - Nhiều
       * Giải thích: Hệ thống quản lý tiền lương sẽ xử lý nhiều bảng chấm công từ nhiều nhân viên, nhưng mỗi bảng chấm công chỉ được xử lý một lần cho mỗi kỳ lương.
- Biểu đồ sequence:\
    ![Diagram](https://www.planttext.com/api/plantuml/png/T95DIWD148NtTOfYLWRC1Ln8G0KtaK2yGANdCMdjdx6wHfYpkV18Ni5sCM4wuFRnVUyrNJzVtxjYeZR5G5JUVMBD1KJcBO2xFKgH0OMtVCJ7XEJ0Zru6bTWHYREi_1J7a6U0QQn5tlbHad5tqFm6Ptj9jI0YsN4kXgerrAkFSABzLNoGMNC8YqANZUqz_rFCTpp07iwY0rwcU8AMcqqZBbkLh1RqEK-LSIlZbiz_sOOkQAjzIl2z69ReQg1vTSNBT8hULd0BjDsZPbT_UqNJ3gclX_a5003__mC0)\
- Biểu đồ lớp:\
 ![Diagram](https://www.planttext.com/api/plantuml/png/T50x3i8m3DrpYboW5-Y0Ei300482YTcaLWlaKzd9K25Eni2Hk0ADsZGg4fxiv_UUFv_Nks8Fv8FHGcbWbXlJQTSZoeUGCN2gj-knjc1mpFpLe0AgnLDCsjE496rY96th0l7PqHth4L0jK8FxO2v8F4B3EZvmzZoGkw7oEx3Ge47hZprxD6d4qY6he2UdzSmT6lDXHR7AcvRvZ1cBX7zZInaOMIpzVnmxSWevqYgqTNpj5m00__y30000)
   + Giải thích:
     * Employee:
       + Đại diện cho nhân viên, cho phép họ nhập và cập nhật thông tin về giờ làm việc.
       + Các thuộc tính bao gồm employeeID, name, và timecard (liên kết tới bảng chấm công).
     * Timecard:
       + Lưu trữ thông tin về giờ làm việc của nhân viên cho kỳ lương hiện tại.
       + Các thuộc tính bao gồm timecardID, hoursWorked, chargeNumbers, và status.
     * ProjectManagementSystem:
       + Cung cấp mã dự án mà nhân viên có thể chọn khi nhập giờ làm việc.
       + Chứa thuộc tính chargeNumbers.
     * PayrollSystem:
       + Chịu trách nhiệm xử lý bảng chấm công đã nộp của nhân viên để thực hiện thanh toán.
     * Quan hệ:
       + Employee có mối quan hệ với Timecard qua thuộc tính timecard, cho thấy rằng một nhân viên có thể có một hoặc nhiều bảng chấm công, nhưng chỉ có một bảng chấm công hiện tại tại một thời điểm.
       + Timecard liên kết với ProjectManagementSystem để nhận các mã dự án hợp lệ khi nhập giờ làm việc.
       + PayrollSystem có quan hệ với Timecard, cho thấy rằng hệ thống quản lý tiền lương sẽ xử lý bảng chấm công sau khi nhân viên nộp.
**5. Hợp nhất kết quả phân tích**
