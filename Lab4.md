Lab 4 - Thiết kế ca sử dụng cho hệ thống "Payroll System" dựa vào kết quả phân tích ca sử dụng và các phần tử thiết kế
# 1. Ca sử dụng: Timecard
## 1.1 Mô tả sự tương tác giữa các đối tượng thiết kế
  -  Nhân Viên ─> TimecardForm: Khởi động quy trình để duy trì thẻ công.
  -  TimecardForm ─> TimecardController: Yêu cầu hiển thị thẻ công hiện tại.
  -  TimecardController ─> ProjectManagementDatabase: Truy xuất mã chi phí và dữ liệu thẻ công hiện tại.
  -  TimecardForm hiển thị thẻ công đã nhận.
  -  Nhân Viên <–> TimecardForm: Nhập giờ làm và lưu lại.
  -  TimecardController cập nhật và lưu thẻ công lại vào cơ sở dữ liệu.
## 1.2 Đơn giản hóa sơ đồ sequence bằng Subsystem
![Diagram](https://www.planttext.com/api/plantuml/png/Z5DBJiCm4Dtd5BE4HIwG1QeKG6n0NN21gJrDZVo9ncEad8q5H-8A35IbAKsYB2pPR_pclNcMlpu-DrcGfGGFKA6HnF0GUfy68WLwBJdZUem2howGGRQFYSDCgKrHE7bF_E_2bjCR6Nd6Y1q5YdAFWZlCSneALtyswhiBxGO2kYYwJkZDhTw_i3UYd3qrO5tkFGwJl95tPSyQRg0ZQG_87RN9KbxeSKAFbCAiRIQbeQvd33D9uGXcWJpMl4fgQk25O5M3-2aLpde-3lbImeuuhuuuupkjoFUSJUajoXhAmfDSYLOn2G6xxY2GzalKdzqltq8knb3E--Bze3qs5Ar-Ysy0003__mC0)
## 1.3 Mô tả hành vi lưu trữ
  -  Nhân viên bắt đầu duy trì thẻ công:
      -  Nhân viên (Employee) tương tác với giao diện TimecardForm bằng cách gọi phương thức maintainTimecard().
  -  Hiển thị thông tin thẻ công:
      -  TimecardForm yêu cầu TimecardController hiển thị thông tin thẻ công hiện tại bằng cách gọi displayTimecard().
      -  TimecardController sẽ lấy các mã số chi phí từ ProjectManagementDatabase bằng cách gọi getChargeCodes().
      -  Sau đó, nó yêu cầu thông tin thẻ công hiện tại từ Timecard bằng cách gọi getCurrentTimecard().
      -  Timecard trả về thông tin thẻ công hiện tại cho TimecardController, và sau đó TimecardController hiển thị thông tin này trên TimecardForm.
  -  Nhập giờ làm việc:
      -  Nhân viên nhập giờ làm việc cho các mã số chi phí trong giao diện TimecardForm.
  -  Lưu thẻ công:
      -  Khi nhân viên hoàn tất việc nhập dữ liệu, TimecardForm gọi saveTimecard() trên TimecardController.
      -  TimecardController sẽ cập nhật thông tin thẻ công với dữ liệu giờ làm việc mới thông qua phương thức updateTimecard().
    -  Sau khi cập nhật, TimecardController sẽ lưu thông tin thẻ công đã cập nhật vào ProjectManagementDatabase bằng cách gọi saveTimecard().
  -  Xác nhận lưu trữ:
      -  Sau khi dữ liệu được lưu thành công, ProjectManagementDatabase sẽ trả về một thông báo xác nhận rằng dữ liệu đã được lưu thành công.
      -  Mặc dù không hiển thị rõ trong sơ đồ, thông báo này có thể được dùng để thông báo cho TimecardController hoặc trực tiếp cho TimecardForm.
  -  Thông báo cho nhân viên:
      -  Cuối cùng, TimecardController có thể gửi một thông báo về việc lưu trữ thành công trở lại TimecardForm, giúp nhân viên biết rằng dữ liệu của họ đã được lưu an toàn.
## 1.4 Tinh chỉnh mô tả luồng sự kiện
  -  Luồng Sự Kiện:
      -  Duy Trì Thẻ Công:
          -  Nhân viên chọn duy trì thẻ công của họ.
          -  get current timecard() được gọi để truy xuất dữ liệu hiện có.
          -  Nếu thẻ công không tồn tại, một thẻ mới được tạo ra.
          -  Mẫu Thẻ Công hiển thị thẻ công với tùy chọn xem mã chi phí.
      -  Nhập Giờ Cho Mã Chi Phí:
          -  Nhân viên nhập số giờ làm việc cho các mã chi phí cụ thể.
          -  Hệ thống xác thực dữ liệu đầu vào và yêu cầu sửa đổi nếu cần.
      -  Lưu Thẻ Công:
          -  Nhân viên hoàn tất nhập liệu và chọn để lưu thẻ công.
          -  Bộ Điều Khiển Thẻ Công cập nhật thông tin thẻ công.
          -  Cuối cùng, thông tin được lưu vào Cơ Sở Dữ Liệu Quản Lý Dự Án.
## 1.5 Hợp nhất các lớp và hệ thống con
  -  Timecard: Bao gồm các thuộc tính như số giờ làm việc, kỳ lương, và các phương thức để lưu và cập nhật thông tin thẻ công.
  -  Nhân Viên: Chứa thông tin cá nhân và các phương thức liên quan đến quản lý tiền lương.
  -  TimecardController: Đóng vai trò là trung gian, phối hợp giữa giao diện người dùng và cơ sở dữ liệu.
---
# 2. Ca sử dụng: RunPayroll
# 2.1 Mô tả sự tương tác giữa các đối tượng thiết kế
  -  Khởi động quy trình:
      -  SystemClock gửi thông báo đến PayrollController về thời gian chạy bảng lương.
  -  Kiểm tra ngày thanh toán:
      -  PayrollController kiểm tra ngày hiện tại để xác định xem có phải là ngày thanh toán không bằng cách gọi is payday().
  -  Lấy số tiền thanh toán:
      -  Nếu đây là ngày thanh toán, PayrollController gọi get pay amount() để lấy số tiền cho từng nhân viên.
  -  Thu thập thông tin thẻ công:
      -  Với mỗi nhân viên, PayrollController yêu cầu Timecard cung cấp thông tin giờ làm bằng cách gọi get timecard info().
  -  Tính toán lương:
      -  Dựa trên thông tin từ Timecard, PayrollController gọi calculatePay() để tính toán số tiền phải trả cho nhân viên.
  -  Chọn phương thức thanh toán:
      -  PayrollController hỏi nhân viên về phương thức thanh toán thông qua get payment method(). Nếu nhân viên chọn chuyển khoản ngân hàng, PayrollController sẽ đi đến bước gọi get bank info() để lấy thông tin tài khoản.
  -  Gửi giao dịch tới ngân hàng:
      -  PayrollController sẽ gửi thông tin giao dịch tới BankSystem bằng cách gọi send bank transaction(Paycheck, bank info) cho phép thực hiện thanh toán trực tiếp vào tài khoản của nhân viên.
  -  In phiếu lương khi cần:
      -  Nếu nhân viên chọn nhận séc, PayrollController sẽ gọi print(Paycheck) từ Printer để in bảng lương cho nhân viên.
# 2.2 Đơn giản hóa sơ đồ sequence bằng Subsystem
![Diagram](https://www.planttext.com/api/plantuml/png/b5HBKiCm3Dtt59gkoWozG1VGeR0jpC26fN0KugbjPMnbaREnu4XS0Jlk9qrQQBNnHtvFyhFadw_lPH3qqbW3C44bxE79rePRehXHHvTMkaOdyDe68Rioh3O3pmksderPiPCqaX_u7z1jCde8zDh9wFYRjgJG5yF3ZLSL1dhsHGUPz1EQtuspM41tjTbDF3nEyJJ2Dmxgl7qLJeS4Ax2zJp8QWNSASGRHBgNu94aSW9ORbxDESCDSGncVXL1LG8UtWQsTvDzfc6bbfwXs9U-Pa-srdf_HWwJnxfZWlzWdQ1GQrHWKYhwZ-5UAOoaMWYMfk3YYIOe_QazAeA2QWvQUyzeu7x5SnqgTPJbKTomuSaN6YqSNOZzfThC8KnMfpUs1UiZSQv4pBw7ObTfRJ8mzC9b0kO-WYt7HlNFRBQ1Eatrw_PpIFV8gpxemQ_whf7VVnW8SYoxRsNJD0hZjYsbYprpBECJ_vXS00F__0m00)
# 2.3 Mô tả hành vi lưu trữ
  -  Khởi động quy trình tính lương:
      -  System Clock khởi động quy trình bằng cách gọi phương thức run payroll(). Quy trình này được kiểm soát bởi PayrollController.
  -  Kiểm tra ngày thanh toán:
      -  PayrollController kiểm tra xem đây có phải là ngày thanh toán hay không bằng cách gọi phương thức is payday().
  -  Lấy thông tin về số tiền thanh toán:
      -  Nếu đúng là ngày thanh toán, PayrollController sẽ gọi get pay amount() để lấy thông tin về số tiền phải trả cho từng nhân viên.
  -  Thu thập thông tin thẻ công:
      -  Đối với mỗi nhân viên, PayrollController sẽ yêu cầu thông tin thẻ công bằng cách gọi get timecard info() từ Timecard, thu thập số giờ làm việc.
  -  Tính toán tiền lương:
      -  Gọi phương thức calculatePay() để tính toán số tiền lương dựa trên thông tin thẻ công và phương thức thanh toán.
  -  Chọn phương thức thanh toán:
      -  PayrollController sẽ yêu cầu nhân viên chọn phương thức thanh toán bằng cách gọi get payment method(). Tùy thuộc vào lựa chọn của nhân viên (trực tiếp hoặc in séc), quy trình sẽ tiếp tục khác nhau.
  -  Lưu thông tin ngân hàng:
      -  Nếu nhân viên chọn trực tiếp vào tài khoản ngân hàng, PayrollController sẽ gọi get bank info() để lấy thông tin cần thiết.
  -  Tạo và gửi giao dịch ngân hàng:
      -  Nếu là thanh toán trực tiếp, PayrollController sẽ tạo một giao dịch với BankSystem bằng cách gọi send bank transaction(Paycheck, bank info), trong đó Paycheck chứa các thông tin thanh toán như số tiền.
      -  Ngân hàng sẽ xử lý và gửi giao dịch thông qua send transaction().
  -  In bảng lương nếu cần:
      -  Nếu nhân viên chọn in, PayrollController sẽ yêu cầu Printer in bảng lương bằng cách gọi print(Paycheck).
  -  Kết thúc quy trình:
      -  Chương trình hoàn thành quy trình tính lương với việc gửi thông báo cho phù hợp, và lưu giữ tất cả thông tin hợp lệ cho việc báo cáo sau này
# 2.4 Tinh chỉnh mô tả luồng sự kiện
  -  Luồng sự kiện chính (Run Payroll):
      -  Khởi động quá trình:
          -  Sự kiện bắt đầu: SystemClock kích hoạt quy trình tính bảng lương bằng cách gửi thông báo cho PayrollController với phương thức run payroll().
      -  Xác định ngày thanh toán:
          -  PayrollController kiểm tra xem hiện tại có phải là ngày thanh toán không bằng cách gọi is payday().
          -  Nếu không phải: Gửi thông báo đến nhân viên và kết thúc quy trình.
      -  Lấy thông tin nhân viên:
          -  Cho mỗi nhân viên trong hệ thống:
            -  PayrollController gọi get pay amount() để lấy số tiền thanh toán.
            -  PayrollController yêu cầu thông tin công việc từ Timecard và PurchaseOrder (nếu có), phương thức get timecard info() cho giờ làm việc và get PO info() cho các giao dịch hoa hồng.
      -  Tính lương:
          -  PayrollController thực hiện calculatePay() với thông tin đã thu thập để tính toán tổng lương cho từng nhân viên.
      -  Chọn và xác nhận phương thức thanh toán:
          -  PayrollController hỏi nhân viên về phương thức thanh toán:
            -  Nếu nhân viên chọn chuyển khoản trực tiếp:
                -  Lấy thông tin ngân hàng từ get bank info().
                -  Tạo giao dịch thanh toán và gửi đến BankSystem bằng send bank transaction(Paycheck, bank info) để thực hiện chuyển khoản.
            -  Nếu nhân viên chọn in séc:
                -  Gọi phương thức print(Paycheck) từ Printer để tạo phiếu lương.
      -  Kết thúc quy trình:
          -  Sau khi hoàn tất tất cả các giao dịch, gửi thông báo cho nhân viên về kết quả thanh toán (qua email hoặc tin nhắn).
# 2.5 Hợp nhất các lớp và hệ thống con
  -  Các lớp chính
      -  Payroll System:
          -  Phương thức: runPayroll(), isPayday(), getPayAmount(), calculatePay(), getPaymentMethod(), getBankInfo()
          -  Thuộc tính: Danh sách nhân viên.
      -  Employee:
          -  Phương thức: getTimecardInfo(), getPaymentMethod(), getBankInfo()
          -  Thuộc tính: ID, tên, thông tin ngân hàng, số giờ làm việc.
      -  Timecard:
          -  Phương thức: getTimecardInfo(), save()
          -  Thuộc tính: Thông tin về giờ làm việc.
      -  BankSystem:
          -  Phương thức: sendTransaction(Paycheck, bankInfo)
          -  Thuộc tính: Danh sách giao dịch.
      -  Printer:
          -  Phương thức: print(Paycheck)
          -  Thuộc tính: Loại máy in
  -  Hệ thống con
      -  Hệ thống Giao dịch Ngân hàng: Xử lý các giao dịch tài chính, thông qua lớp BankSystem.
      -  Hệ thống In ấn: Quản lý việc in các phiếu lương thông qua lớp Printer.
