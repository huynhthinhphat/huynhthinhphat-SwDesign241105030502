**LAB 1: PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG**

1. **Phân tích kiến trúc**
   - Đề xuất kiến trúc: Model - view - controller (MVC)
   - Lý do: Vì nó hỗ trợ tính linh hoạt, khả năng mở rộng, và dễ dàng bảo trì hệ thống khi có nhu cầu.
     + Phân tách rõ ràng các thành phần: Tách biệt các thành phần giúp hệ thống dễ bảo trì, mở rộng và cải thiện khi cần mà không ảnh hưởng đến các phần khác.
     + Dễ dàng bảo trì và mở rộng: Mỗi thành phần hoạt động độc lập, nên khi thay đổi một phần như View, logic Model, hoặc Controller không ảnh hưởng đến các phần còn lại.
     + Khả năng mở rộng: Khi có nhu cầu mở rộng chức năng, MVC cho phép thêm các View mới để cung cấp các tính năng khác mà không làm gián đoạn các thành phần khác.
     + Tái sử dụng mã nguồn: Các thành phần trong kiến trúc MVC có tính tái sử dụng cao, đặc biệt khi mở rộng hệ thống hoặc tích hợp với các hệ thống khác.
   - Ý nghĩa từng thành phần:
     gồm 3 thành phần chính
         1. Model: Mô hình đại diện cho dữ liệu và logic kinh doanh của ứng dụng. Nó chứa các đối tượng, lớp và phương thức để xử lý dữ liệu, thường bao gồm việc truy xuất và lưu trữ dữ liệu từ cơ sở dữ liệu.
         2. View: là phần hiển thị của ứng dụng, nơi người dùng tương tác với ứng dụng. Nó nhận dữ liệu từ mô hình và hiển thị chúng một cách trực quan.
         3. Controller: là cầu nối giữa mô hình và view. Nó nhận các yêu cầu từ view (chẳng hạn như tương tác của người dùng), xử lý chúng, và sau đó cập nhật mô hình hoặc view theo nhu cầu.
   - Vẽ biểu đồ:
     
**3. Cơ chế phân tích**
     
**4. Phân tích ca sử dụng Payment**

**5. Phân tích ca sử dụng Maintain Timecard**

**6. Hợp nhất kết quả phân tích**
