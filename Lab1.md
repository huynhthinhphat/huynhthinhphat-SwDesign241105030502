**LAB 1: PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG**

1. **Phân tích kiến trúc**
  - Đề xuất kiến trúc: Model - view - controller (MVC)
  - Lý do: Vì nó hỗ trợ tính linh hoạt, khả năng mở rộng, và dễ dàng bảo trì hệ thống khi có nhu cầu.
    - Phân tách rõ ràng các thành phần: Tách biệt các thành phần giúp hệ thống dễ bảo trì, mở rộng và cải thiện khi cần mà không ảnh hưởng đến các phần khác.
    -  Dễ dàng bảo trì và mở rộng: Mỗi thành phần hoạt động độc lập, nên khi thay đổi một phần như View, logic Model, hoặc Controller không ảnh hưởng đến các phần còn lại.
    -  Khả năng mở rộng: Khi có nhu cầu mở rộng chức năng, MVC cho phép thêm các View mới để cung cấp các tính năng khác mà không làm gián đoạn các thành phần khác.
    -  Tái sử dụng mã nguồn: Các thành phần trong kiến trúc MVC có tính tái sử dụng cao, đặc biệt khi mở rộng hệ thống hoặc tích hợp với các hệ thống khác.
  - Ý nghĩa từng thành phần: Gồm 3 thành phần chính:
    - Model: Mô hình đại diện cho dữ liệu và logic kinh doanh của ứng dụng. Nó chứa các đối tượng, lớp và phương thức để xử lý dữ liệu, thường bao gồm việc truy xuất và lưu trữ dữ liệu từ cơ sở dữ liệu.
    - View: là phần hiển thị của ứng dụng, nơi người dùng tương tác với ứng dụng. Nó nhận dữ liệu từ mô hình và hiển thị chúng một cách trực quan.
    - Controller: là cầu nối giữa mô hình và view. Nó nhận các yêu cầu từ view (chẳng hạn như tương tác của người dùng), xử lý chúng, và sau đó cập nhật mô hình hoặc view theo nhu cầu.
  - Vẽ biểu đồ package mô tả kiến trúc:
     ![Diagram](https://www.planttext.com/api/plantuml/png/R96zIWGn58NxFCKb_Rw0XIo8Q3CWk0YMOUQw4pS_Q-OEEeYLXOMFOI48OZz1jjWdoHFu2YQhp6QOhGBdEpddtkJ7R-OD2KUjLapX3G5PS79P4rJIOKdI6iRMebo99G8lR8MAmoC3A9Le6ZZLQsKxn45OI8sbSDKWN8XEew42gRQPwknjJ2-4YRc9NtODeMPFMTc9DUIiKkZonfYNn3sSL1z0_qDa92-wadX_QAcaJz97ucYv7OcvwOJPx1ZsTN04_2puJmdTzgE5ClJlBMSPJ_RTuoRdzU21XtW9rFQRipywZetUXGlz6rJ1Vu6ImRzCOzCuqNWUwRC1geD_XLNeDmHtRRpBsHnDbRx_5m00__y30000)

**2. Cơ chế phân tích**
  - Persistency (Lưu trữ lâu dài):
    - Mô tả: Hệ thống cần có cơ chế để đảm bảo dữ liệu như thông tin nhân viên, bảng lương và các dữ liệu liên quan được lưu trữ an toàn và tồn tại lâu dài, ngay cả khi ứng dụng tắt.
    - Lý do: Để đảm bảo rằng dữ liệu quan trọng không bị mất và có thể được truy xuất khi cần thiết.
  - Distribution (Phân phối):
    - Mô tả: Hệ thống sẽ phân phối logic nghiệp vụ trên nhiều nút trong hệ thống, cho phép xử lý đồng thời.
    - Lý do: Điều này giúp tăng tốc độ xử lý tính toán lương cho nhiều nhân viên, giảm thiểu quá tải cho một máy chủ duy nhất và nâng cao hiệu suất tổng thể.
  - Security (Bảo mật):
    - Mô tả: Cần thiết lập các biện pháp bảo mật để chỉ những nhân viên có quyền mới có thể truy cập và chỉnh sửa thông tin cá nhân của họ và thông tin nhạy cảm như bảng lương.
    - Lý do: Để bảo vệ dữ liệu nhạy cảm khỏi truy cập trái phép, đảm bảo rằng chỉ những người dùng hợp lệ mới có quyền thao tác trên thông tin cá nhân.
  - Legacy Interface (Giao diện hệ thống kế thừa):
    - Mô tả: Hệ thống mới cần có khả năng giao tiếp với hệ thống quản lý dự án hiện có mà công ty không muốn thay thế.
    - Lý do: Để duy trì tính tương thích và tích hợp với các hệ thống cũ, cần có một giao diện chắc chắn giữa hệ thống mới và cũ nhằm đảm bảo dữ liệu được truyền tải đúng và đầy đủ.
  - Data Validation (Kiểm tra tính hợp lệ dữ liệu):
    - Mô tả: Cần có cơ chế để kiểm tra tính hợp lệ của thông tin đầu vào từ người dùng, như thông tin ngân hàng và bảng chấm công.
    - Lý do: Để tránh lỗi và đảm bảo rằng thông tin được nhập vào hệ thống là chính xác, từ đó cải thiện chất lượng dữ liệu và giảm thiểu rủi ro trong xử lý thanh toán.
  - Audit Logging (Ghi nhật ký kiểm tra):
    - Mô tả: Hệ thống cần ghi lại các hành động quan trọng liên quan đến dữ liệu nhạy cảm, như cập nhật thông tin nhân viên hoặc thay đổi phương thức thanh toán.
    - Lý do: Để có thể theo dõi và truy cứu lại các thay đổi trong hệ thống, tăng cường tính minh bạch và phát hiện các hành vi đáng ngờ.
   
**3. Phân tích ca sử dụng Payment**
  - Các lớp phân tích của ca sử dụng Payment:
    - Entity:
      - Employee: Lưu thông tin cơ bản của nhân viên, như tên, ID, và phương thức thanh toán.
      - PaymentMethod: Lưu trữ chi tiết phương thức thanh toán (gửi qua thư, nhận tại chỗ, hoặc chuyển khoản trực tiếp).
      - PayrollRecord: Lưu thông tin về kỳ lương, số tiền thanh toán, ngày thanh toán.
    - Boundary:
      - PaymentUI: Giao diện cho nhân viên lựa chọn hoặc xác nhận phương thức thanh toán.
    - Control:
      - PaymentController: Điều phối các thao tác trong quá trình thanh toán, lấy thông tin từ Employee và PaymentMethod, xử lý yêu cầu thanh toán, và cập nhật trạng thái thanh toán trong PayrollRecord.
  - Quan hệ giữa các lớp phân tích:
    - Employee và PaymentMethod:
      - Loại mối quan hệ: Một - Một
      - Giải thích: Employee có một PaymentMethod duy nhất để xác định phương thức thanh toán của mình. Điều này giúp mỗi nhân viên được liên kết rõ ràng với một trong các phương thức thanh toán như PickUp, Mail, hoặc DirectDeposit
    - PaymentMethod và các lớp con (Pick-up, Mail, DirectDeposit):
      - Loại mối quan hệ: Một - Nhiều
      - Giải thích: PaymentMethod là lớp cha trừu tượng, có nhiều lớp con đại diện cho các phương thức thanh toán cụ thể. Các lớp con như PickUp, Mail, và DirectDeposit kế thừa thuộc tính và hành vi từ PaymentMethod, và có thể mở rộng thêm chi tiết nếu cần.
    - PaymentSystem và Employee:
      - Loại mối quan hệ: Một - Nhiều
      - Giải thích: PaymentSystem quản lý các giao dịch thanh toán cho nhiều nhân viên (Employee). PaymentSystem sẽ lưu trữ và quản lý thông tin thanh toán của mỗi nhân viên để đảm bảo tính chính xác và nhất quán trong các kỳ thanh toán.
  - Biểu đồ sequence:\
    ![Diagram](https://www.planttext.com/api/plantuml/png/T991RW8n34NtEKKkm0LOL4Y0gYug8L0F43A_QgHC38wdKix6WYDnXMRKX7GAi_JNV_QtazlbkefYM8RUAsE5M6_xawS4g2CDeJESzCwa7a4-tfIb84o-AklVqeDLhfoa1fUw6DyXNzJz4KTg3qlSALKPlNXfe_HI7-1XfKgwz6YEPcyvChR7UK1it8x98aRrwCqDxhD7JjZX6qtRG8ppC-Haiuo_OYxg0zUMpzoQOGHLrkKeKzUJSRdff-E-whF0v3GrNu4n7_7-21iNJzwa_wWHHq6j4Bhnu_m0003__mC0)\
  - Biểu đồ lớp:\
  ![Diagram](https://www.planttext.com/api/plantuml/png/X5FBJiCm4BpdAwoS0Aa7hZcWLWg7IhIA29mG1yTPMgj-oLvBH8Wluy0dyGiuaAHnQ6WkKMPdn-FPpTV7vz8XjUYbI9YWpf5RQOHk0CXRGiAp8D01wpmZ9LgkTfF2bagOAQtgse9pCzLYhnLilQp0JXY6DX8KRW3tkiv8CVvCtfFEQWHtVadV-z2OewjZ2sU7HqFW5K7Limg1vCsTPXIvLdz5DfIBCn8oK4BFzFw3HCujCCp1QCVnZ5P5rM75cFOAJuJrMuzcC0x8QY7kWMbR3mCD0HLWUHjiJX4wbChsW01fNmc8vr0YHN_Y5ftVid48SgpVeclrehFOmjDpdx3LBEJIzL_q2v4DstVP7ZAiOdgTaiNYvkSTxqBiOE1TfOFIFvJ8Mx8C8sX_Wsy0003__mC0)
    - Giải thích:
      - Employee:
        - Thuộc tính: Bao gồm employeeID, employeeName, employeeAddress, employeePhoneNumber, và paymentMethod (liên kết đến một PaymentMethod cụ thể).
        - Quan hệ: Mỗi Employee liên kết với một PaymentMethod duy nhất để xác định cách nhận lương của mình.
      - PaymentMethod:
        - Thuộc tính: paymentType chỉ định loại phương thức thanh toán.
        - Quan hệ: Là lớp cha của các lớp con cụ thể như PickUp, Mail, và DirectDeposit. Các lớp con kế thừa thuộc tính paymentType từ PaymentMethod và mở rộng thêm các chi tiết cần thiết.
        - Lớp con:
          - PickUp: Có thuộc tính pickupLocation để chỉ định địa điểm nhận lương.
          - Mail: Có thuộc tính mailingAddress để lưu địa chỉ nhận thư.
          - DirectDeposit: Có thuộc tính bankAccountNumber và bankName để lưu thông tin ngân hàng khi thực hiện chuyển khoản.
      - PayrollRecord:
        - Thuộc tính: payPeriod, amount, và paymentStatus để lưu thông tin chi tiết về kỳ lương, số tiền thanh toán và trạng thái thanh toán.
        - Quan hệ: PayrollRecord được quản lý bởi PaymentSystem để ghi lại lịch sử thanh toán cho từng nhân viên.
      - PaymentSystem:
        - Thuộc tính: paymentInfo, lưu trữ danh sách các PayrollRecord cho nhiều nhân viên.
        - Quan hệ: PaymentSystem quản lý thông tin thanh toán cho nhiều Employee và thực hiện xử lý các giao dịch thông qua phương thức processPayment().
        
**4. Phân tích ca sử dụng Maintain Timecard**
  - Các lớp phân tích của ca sử dụng Payment:
    - Entity:
      - Employee: Đại diện cho nhân viên trong hệ thống. Lớp này lưu giữ thông tin nhân viên như ID và tên, và cũng có tham chiếu đến bảng chấm công (Timecard).
      - Timecard: Lưu trữ thông tin chấm công hàng ngày của nhân viên như số giờ làm việc và mã chi phí dự án. Mỗi Timecard đại diện cho bảng chấm công của một kỳ lương.
      - ProjectManagementSystem: Hệ thống quản lý dự án, cung cấp các mã dự án (charge numbers) mà nhân viên có thể chọn để ghi vào bảng chấm công của họ.
    - Boundary:
      - TimecardUI: Giao diện cho phép nhân viên nhập và nộp bảng chấm công.
    - Control:
      - TimecardController: Điều phối các thao tác của bảng chấm công như lưu thông tin chấm công từ TimecardUI, xác thực dữ liệu nhập vào và lưu vào hệ thống.
  - Quan hệ giữa các lớp phân tích:
    - Employee và Timecard:
      - Loại mối quan hệ: Một - Nhiều
      - Giải thích: Mỗi Employee có thể có nhiều Timecard qua các kỳ lương khác nhau. Tuy nhiên, tại một thời điểm chỉ có một bảng chấm công hiện tại cho kỳ lương hiện tại. Điều này giúp nhân viên quản lý và ghi lại giờ làm việc qua các kỳ lương khác nhau một cách hiệu quả.
    - Timecard và ProjectManagementSystem:
      - Loại mối quan hệ: Nhiều - Một
      - Giải thích: Nhiều Timecard có thể tham chiếu đến thông tin mã dự án từ ProjectManagementSystem, nhưng mỗi mã dự án chỉ thuộc về một dự án cụ thể tại một thời điểm. Điều này giúp đảm bảo tính chính xác khi ghi nhận giờ làm việc của nhân viên trên các dự án khác nhau.
    - PayrollSystem và Timecard:
      - Loại mối quan hệ: Một - Nhiều
      - Giải thích: PayrollSystem sẽ xử lý nhiều Timecard từ nhiều nhân viên khác nhau để thực hiện việc tính lương cho mỗi kỳ. Mỗi bảng chấm công chỉ được xử lý một lần trong mỗi kỳ lương, giúp hệ thống dễ dàng quản lý và tính toán chính xác.
  - Biểu đồ sequence:\
    ![Diagram](https://www.planttext.com/api/plantuml/png/X95B3i8m34JtEKKkm0MwG9MW2rOWVdktCL9GFfNh8kLiB3WILo3GDYqI5SknvdacplF-o1i6ujOQ0HLxaeMjZG-8elIjKq117hN52aYTDgBoZicRD5frsY09TAmvZ7Yl1-UWT-IlMB4GWr4kbfC4cSbjZIvDP143WfWO9lOnFMA7jhIQvy29DIv8sPayWz4A6CVYlv6-ToJsoAJnXccqycgEIcrYFuZ8JBlPHqLnqMI1jNT_8ZwtM-kcDX2wOpHDfBvNvEZK-wjV0000__y30000)\
  - Biểu đồ lớp:\
 ![Diagram](https://www.planttext.com/api/plantuml/png/V59BQiCm5Dph54Ahf915jwQ4GDE5eIs1j7Gjoo-EMtt2anmmfIVheaVg5IhNaaWSnzuOltapcXdhz_jdPHr7roX9XEJMqWTraAO5e9-4-cT18GpoTKQt3cjT1K1p1OEHgnK8ZgNDw6DjtTrB-5wIBnBquoZfHyw5_juqQDyCVa2PqRLf2Wa14NkE5JmtgW0Sa7mQrzWqJCTkqBo3S4zSymeKQBTjhGCLND0poUY-rpZnlk4j6Ya7r0CQ0TR6OBCOA4jPvvVnN_F4zsO0uppNEpER1yGsXQfT4XwHkJVQTPO0avpbHvZqqgyTkQnBxgPN_NdfFh1RHXUB9MKtB6sGz3SJwj_NkiueGzW1WXR0o7cPa-g-h0uR2Uqb-v8O6K5FIV-hlXf6Lg3Bxhx_0G00__y30000)
   - Giải thích:
     - Employee:
       - Thuộc tính: employeeID (ID nhân viên) và name (tên nhân viên), cùng với timecards (danh sách các bảng chấm công của nhân viên).
       - Quan hệ: Một Employee có thể có nhiều Timecard cho nhiều kỳ lương khác nhau.
     - Timecard:
       - Thuộc tính: timecardID (ID bảng chấm công), hoursWorked (số giờ làm việc), chargeNumber (mã chi phí dự án), và status (trạng thái của bảng chấm công).
       - Quan hệ: Timecard tham chiếu đến ProjectManagementSystem để lấy mã chi phí hợp lệ cho từng dự án. Điều này giúp ghi lại chính xác dự án mà nhân viên đã làm việc trong từng kỳ lương.
     - ProjectManagementSystem:
       - Thuộc tính: chargeNumbers (danh sách các mã chi phí dự án)
       - Quan hệ: Cung cấp mã chi phí để Timecard có thể sử dụng khi ghi lại giờ làm việc trên các dự án.
     - PayrollSystem:
       - Phương thức: processTimecard() để xử lý Timecard của nhân viên trong kỳ lương hiện tại.
       - Quan hệ: PayrollSystem liên kết với Timecard, xử lý bảng chấm công của nhiều nhân viên để tính lương theo kỳ.
     - TimecardUI:
       - Phương thức: enterTimecardInfo() và submitTimecard() để nhân viên nhập và nộp bảng chấm công qua giao diện.
       - Quan hệ: TimecardUI gửi thông tin đến TimecardController để xác nhận và lưu bảng chấm công.
     - TimecardController:
       - Phương thức: saveTimecard() để lưu bảng chấm công và validateTimecard() để xác thực thông tin bảng chấm công.
       - Quan hệ: Điều phối luồng công việc của bảng chấm công, xác thực dữ liệu từ TimecardUI và lưu thông tin vào Timecard.
         
**5. Hợp nhất kết quả phân tích**
- Các Lớp Phân tích Chính và Vai trò
  - Entity:
    - Employee: Đại diện cho nhân viên trong hệ thống, lưu trữ các thông tin cơ bản như employeeID, name, và paymentMethod. Đối với ca sử dụng Payment, Employee chứa thông tin về phương thức thanh toán của mình. Trong ca sử dụng Maintain Timecard, Employee có một danh sách Timecard để quản lý các giờ làm việc của họ qua các kỳ lương khác nhau.
    - Timecard: Được sử dụng trong ca sử dụng Maintain Timecard, Timecard lưu trữ thông tin về giờ làm việc, mã dự án, và trạng thái. Mỗi Employee có thể có nhiều Timecard.
    - PaymentMethod: Lớp này lưu trữ các chi tiết về phương thức thanh toán của nhân viên, bao gồm các lớp con như PickUp, Mail, và DirectDeposit. Mỗi Employee chỉ có một PaymentMethod duy nhất.
    - PayrollRecord: Lưu trữ thông tin thanh toán cho mỗi kỳ lương của nhân viên, bao gồm payPeriod, amount, và paymentStatus. PayrollRecord hỗ trợ ca sử dụng Payment, giúp hệ thống theo dõi các giao dịch thanh toán.
    - ProjectManagementSystem: Hệ thống cung cấp mã dự án cho Timecard để đảm bảo các bảng chấm công của nhân viên ghi nhận đúng mã chi phí dự án.
  - Boundary:
    - PaymentUI: Giao diện cho phép nhân viên chọn và xác nhận phương thức thanh toán.
    - TimecardUI: Giao diện cho phép nhân viên nhập và nộp bảng chấm công của mình.
  - Control:
    - PaymentController: Điều phối các thao tác trong quá trình thanh toán của nhân viên. PaymentController quản lý các yêu cầu từ PaymentUI, lấy thông tin từ Employee và PaymentMethod, tạo PayrollRecord và lưu lại trạng thái thanh toán.
    - TimecardController: Điều phối quy trình nhập và lưu bảng chấm công từ TimecardUI, xác thực dữ liệu và lưu bảng chấm công vào hệ thống.
- Quan hệ Giữa Các Lớp
  - Employee và PaymentMethod:
    - Quan hệ: Một - Một
    - Giải thích: Mỗi Employee liên kết với một PaymentMethod duy nhất để xác định cách thức nhận lương của mình. Điều này đảm bảo nhân viên có thể nhận thanh toán thông qua các phương thức khác nhau như PickUp, Mail, hoặc DirectDeposit.
  - Employee và Timecard:
    - Quan hệ: Một - Nhiều
    - Giải thích: Mỗi Employee có thể có nhiều Timecard qua các kỳ lương khác nhau, giúp ghi nhận giờ làm việc của nhân viên một cách chi tiết qua các kỳ.
  - PayrollSystem và Employee, Timecard:
    - Quan hệ: Một - Nhiều
    - Giải thích: PayrollSystem quản lý và xử lý bảng chấm công cũng như các giao dịch thanh toán cho nhiều Employee, giúp hệ thống đảm bảo tính nhất quán và chính xác khi tính toán lương và thực hiện thanh toán.
  - Timecard và ProjectManagementSystem:
    - Quan hệ: Nhiều - Một
    - Giải thích: Nhiều Timecard có thể sử dụng cùng mã dự án từ ProjectManagementSystem, nhưng mỗi mã dự án chỉ thuộc về một dự án cụ thể.
 - Biểu đồ sequence:
      ![Diagram](https://www.planttext.com/api/plantuml/png/X9HBJiD038RtESLSW0iW1LLgAzH59THGzcxYmg1vj3CEKix6WYDn1PmmZuGcOXDfFFzdZ_rR-VxyMda2HwrM1THadTZgYx8TOd6ohMd0TU89Ees6ZhiSUfOQQt0Dnsfho5aLLUlVeqANRg9uTCL2ILsk5SuXnnxfpJOn6F6HgCzomDgEWiw-OqrxCF2AVOwgyuJw3nE2HLd6KkBeKQo1FsLPnEU8kuVSjBWN5IhEdP3mlAp8yjmYOmUyjkWpns-iqVlYLii9KksU8oVn0tDiWmHIBP2JeJ7-Y4jFlU7o79bREmJ261PXlbFLJ3bEUfPEn_Wia6VFmF7IpDTPR6qmOIFzHK7QaLWNI5epEBe7QNXC9YtCehTvUpdlrX0NIypEd6qn4epa4tEhzgGbvUMS4KrTVG4bXyRJqiyZ2viyteiWuH4qIrbIF_nIO2ITkLtN9MZEdx2c6JdpNo68_gasCMgOaFTipzIh5Pgc_zty0000__y30000)
    - Giải thích:
      - Payment Use Case:
        - Employee chọn phương thức thanh toán trong PaymentUI, yêu cầu PaymentController xử lý thanh toán.
        - PaymentController lấy thông tin từ Employee và PaymentMethod, sau đó tạo PayrollRecord để lưu lại chi tiết thanh toán.
        - PayrollRecord xác nhận phương thức thanh toán qua PaymentMethod và cập nhật vào PayrollSystem.
        - Sau khi hoàn thành, PaymentController hiển thị xác nhận thanh toán qua PaymentUI.
      - Maintain Timecard Use Case:
        - Employee nhập thông tin bảng chấm công qua TimecardUI, yêu cầu TimecardController xử lý.
        - TimecardController xác thực thông tin Employee và lấy mã dự án từ ProjectManagementSystem.
        - TimecardController lưu dữ liệu chấm công vào Timecard và chuyển thông tin đến PayrollSystem để xử lý cho kỳ lương.
        - Sau khi hoàn tất, TimecardController hiển thị xác nhận qua TimecardUI.
 - Biểu đồ lớp:
      ![Diagram](https://www.planttext.com/api/plantuml/png/Z5JBRjim4BphAmYTx08-z2e4GO8g1mDnODG9SgQfjSsO3s591ZMAVbaE-QJyGgcAfFLoKbq4BOUpCyiHFzxURuobQ9qK6HFK678dQw5F0EHtHlop810Aox8W6ujSxSE2eX86fPgU92Yx0dlGLK7MtSy0iLm2erYPWjnpOwyUm_TrzYSB4c8fIOXxHX8Esg5vrdW4twtKRYiWhB03nJqyEBa576poXgqpgPZQhb6_0BChgkWU6jsRax4WWmhIeupgMuwETcyPjH23hJLg1iP4OxDeg4XUvtracDmi3hz8vpBlzJgFzzohhJwUQfZmoDdngIRmouAgBZ9uaAllDQEMQpKcML4klg2G7kBtt5OLUZTZYfAZ7tK9jJRSVi6rfUfuovXsoawSPxl-qCtYy31-0jETDFa1hG5v4z2IsXWOAfi6WnI5MMuk9QPTVbechGQ4zzNpCOj7oxJQSPJnQEVZm7U8F08mrfTgfnEDSLl9ROhIE0y_jBADRS34nXMtt7lzB5OjqjLLYpiFRahfH0z3N-4_0lvA1MzQV0hr_T8zb7_FoM9n_U_Tlr36a6zv8idIBT8ZkF2F5oH7s062Of1d_Pzualqof3UxB2YUm4NrsOtFVdF__WK00F__0m00)
    - Giải thích:
      - Employee: Là lớp trung tâm, kết nối với cả PaymentMethod và Timecard, cho phép hệ thống Payroll quản lý thông tin thanh toán và bảng chấm công cho từng nhân viên.
      - Timecard và ProjectManagementSystem: Timecard tham chiếu đến ProjectManagementSystem để đảm bảo mã dự án hợp lệ khi ghi lại giờ làm việc, hỗ trợ hệ thống trong việc phân bổ chi phí cho từng dự án.
      - PayrollSystem: Xử lý cả Timecard và PayrollRecord, thực hiện tính toán và lưu trữ thông tin bảng chấm công và thanh toán cho từng nhân viên trong kỳ lương.
      - PaymentMethod: Hỗ trợ tính linh hoạt với các phương thức thanh toán như PickUp, Mail, và DirectDeposit. Quan hệ kế thừa giữa PaymentMethod và các lớp con giúp mở rộng phương thức thanh toán dễ dàng khi cần.
      - Controller và Boundary: PaymentController và TimecardController chịu trách nhiệm điều phối quy trình trong các ca sử dụng, tương tác với PaymentUI và TimecardUI để đảm bảo rằng các thao tác từ người dùng được xử lý và lưu trữ chính xác.
