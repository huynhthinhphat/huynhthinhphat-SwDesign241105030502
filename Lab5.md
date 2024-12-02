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
Mô hình hóa hệ thống con bằng TextPlant
@startuml  
actor Employee  

participant TimecardForm {  
    + displayTimecard()  
    + saveTimecard()  
}  

participant TimecardController {  
    + getChargeCodes()  
    + getCurrentTimecard()  
    + updateTimecard()  
}  

participant ProjectManagementDatabase {  
    + saveTimecard()  
}  

participant Timecard {  
    + date : Date  
    + hours : float  
}  

Employee -> TimecardForm : maintainTimecard()  
Employee -> TimecardForm : enterHoursForChargeNumbers()  
TimecardForm -> TimecardController : displayTimecard()  
TimecardController -> TimecardController : getChargeCodes()  
TimecardController -> ProjectManagementDatabase : saveTimecard()  
TimecardController -> Timecard : getCurrentTimecard()  
TimecardController -> TimecardForm : return currentTimecard()  
TimecardForm -> TimecardController : saveTimecard()  
TimecardController -> ProjectManagementDatabase : updateTimecard()  
ProjectManagementDatabase -> Timecard : saveTimecard()  
note right of TimecardController : Data saved successfully  
@enduml


