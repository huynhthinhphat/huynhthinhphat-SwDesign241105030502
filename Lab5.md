Thiết kế Hệ thống Con cho Ca Sử Dụng Duy Trì Thời Gian Làm Việc
Bước 1: Phân phối hành vi của hệ thống con đến các phần tử
Thành phần hệ thống con
TimecardForm: Giao diện người dùng để nhập và hiển thị thông tin thời gian làm việc.
TimecardController: Điều khiển logic và xử lý các yêu cầu từ TimecardForm.
ProjectManagementDatabase: Cơ sở dữ liệu để lưu trữ thông tin thời gian làm việc.
Timecard: Đối tượng đại diện cho các thông tin thời gian làm việc, bao gồm ngày và số giờ làm.
Bước 2: Tài liệu hóa các phần tử của hệ thống con
Các thành phần và phương thức:
TimecardForm

displayTimecard(): Hiển thị thông tin thời gian làm việc hiện tại.
saveTimecard(): Lưu thông tin giờ làm việc từ nhân viên.
TimecardController

getChargeCodes(): Lấy mã chi phí để nhập số giờ.
getCurrentTimecard(): Trả về thông tin thời gian làm việc hiện tại.
updateTimecard(): Cập nhật thông tin giờ làm việc.
ProjectManagementDatabase

saveTimecard(): Lưu thông tin thời gian vào cơ sở dữ liệu.
Timecard

Chứa thông tin ngày (date) và số giờ (hours).
Bước 3: Mô tả các phụ thuộc của hệ thống con
Mối quan hệ giữa các thành phần
Nhân viên (Employee): Là tác nhân tương tác với hệ thống, sử dụng TimecardForm để nhập thông tin về thời gian làm việc.
TimecardForm gọi đến TimecardController để thực hiện logic và lưu dữ liệu.
TimecardController tương tác với ProjectManagementDatabase để lưu trữ thông tin thời gian làm việc.
Bước 4: Kiểm tra (Checkpoints)
Quy trình kiểm tra
Tổ chức các buổi họp định kỳ để xem xét từng phần của thiết kế với các bên liên quan nhằm đảm bảo đáp ứng được yêu cầu.
Thực hiện kiểm thử đơn vị cho các thành phần để đảm bảo chức năng hoạt động chính xác và hiệu suất đạt yêu cầu.

###
Thiết kế Hệ thống Con cho Ca Sử Dụng Duy Trì Thời Gian Làm Việc
Bước 1: Phân phối hành vi của hệ thống con
Các thành phần hệ thống con
SystemClock: Theo dõi thời gian.
PayrollController: Quản lý quy trình tính toán tiền lương.
BankSystem: Xử lý các giao dịch ngân hàng.
Printer: In phiếu lương.
Timecard: Lưu trữ thông tin thời gian làm việc.
PurchaseOrder: Có thể sử dụng để xử lý các chi phí liên quan đến tiền lương.
Bước 2: Tài liệu hóa các phần tử của hệ thống con
Phân loại thành phần và phương thức:
SystemClock

start(): Khởi động quá trình theo dõi thời gian.
PayrollController

runPayroll(): Bắt đầu quy trình thanh toán tiền lương.
getPayAmount(): Lấy số tiền thanh toán cho nhân viên.
calculatePay(): Tính toán tổng số tiền lương dựa trên thông tin thời gian.
BankSystem

sendBankTransaction(Paycheck, bankInfo): Thực hiện giao dịch ngân hàng để chuyển tiền.
Printer

print(Paycheck): In phiếu lương cho nhân viên.
Timecard

getTimecardInfo(): Lấy thông tin thời gian làm việc của nhân viên.
PurchaseOrder

(Nên có nếu cần quản lý các chi phí phát sinh).
Bước 3: Mô tả các phụ thuộc của hệ thống con
Mối quan hệ giữa các thành phần
Employee tương tác với PayrollController thông qua các phương thức, khi cần lấy thông tin thanh toán.
PayrollController gọi đến SystemClock để xác định thời gian và liệu có đến ngày thanh toán hay không.
PayrollController lấy thông tin từ Timecard để tính toán tiền lương cho từng nhân viên.
BankSystem xử lý giao dịch và chuyển tiền lệ phí cho nhân viên.
Printer sẽ in phiếu lương nếu phương thức thanh toán không phải là chuyển khoản.
Bước 4: Kiểm tra (Checkpoints)
Quy trình kiểm tra
Tổ chức các buổi họp để xem xét quy trình thực hiện với các bên liên quan, đảm bảo rằng mọi thành phần được xác định rõ ràng.
Kiểm thử đơn vị cho mỗi phương thức trong các thành phần, đảm bảo các chức năng hoạt động chính xác trước khi đưa vào triển khai.
