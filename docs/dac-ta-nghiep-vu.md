# Đặc tả nghiệp vụ — Hệ thống Đăng ký Học phần (DT04)

## 1. Tác nhân hệ thống (`A01–A04`)
- **A01 – Quản trị hệ thống:** Quản lý tài khoản, phân quyền vai trò, xem báo cáo chung và nhật ký hệ thống.
- **A02 – Cán bộ phòng đào tạo:** Quản lý khoa/CTĐT, môn học, môn tiên quyết, học kỳ/đợt đăng ký, phòng học, hồ sơ sinh viên/giảng viên; mở lớp & xếp lịch; khóa/mở khóa đăng ký sinh viên; điều chỉnh điểm sau công bố; chốt học kỳ.
- **A03 – Giảng viên:** Xem danh sách lớp và sinh viên được phân công; nhập/sửa điểm trước khi công bố và công bố điểm cho lớp phụ trách.
- **A04 – Sinh viên:** Tra cứu lớp mở; đăng ký/hủy đăng ký trong hạn; xem thời khóa biểu cá nhân, bảng điểm và GPA.

## 2. Danh mục 21 Use Case (`UC01–UC21`)
- **UC01:** Đăng nhập hệ thống (`A01–A04`).
- **UC02:** Phân quyền tài khoản (`A01`).
- **UC03:** Quản lý khoa và CTĐT (`A02`).
- **UC04:** Quản lý môn học (`A02`).
- **UC05:** Thiết lập môn tiên quyết (`A02`).
- **UC06:** Quản lý học kỳ & đợt đăng ký (`A02`).
- **UC07:** Quản lý phòng học (`A02`).
- **UC08:** Quản lý hồ sơ nhân sự (`A02`).
- **UC09:** Mở lớp học phần & xếp lịch (`A02`).
- **UC10:** Khóa/mở khóa đăng ký (`A02`).
- **UC11:** Tra cứu lớp đang mở (`A04`).
- **UC12:** Đăng ký lớp học phần (`A04`) — kiểm tra đợt đăng ký theo khóa, trạng thái/khóa đăng ký của sinh viên, môn thuộc CTĐT và chưa đạt ở kỳ trước, điều kiện môn tiên quyết, không trùng lịch/môn học, sĩ số lớp, giới hạn tín chỉ học kỳ; thực hiện trong giao dịch nguyên tử có khóa dòng (`SELECT ... FOR UPDATE`) và hỗ trợ khóa chống gửi lặp (`Idempotency-Key`).
- **UC13:** Hủy đăng ký học phần (`A04`) — chỉ thực hiện trước hạn hủy của học kỳ và khi lớp chưa có điểm; cập nhật trạng thái đăng ký và giảm sĩ số đúng 1 lượt (hủy lặp không giảm thêm).
- **UC14:** Xem TKB cá nhân (`A04`).
- **UC15:** Xem danh sách lớp phụ trách (`A03`).
- **UC16:** Nhập điểm học phần (`A03`).
- **UC17:** Công bố điểm (`A03`).
- **UC18:** Xem bảng điểm và GPA (`A04`).
- **UC19:** Điều chỉnh điểm sau công bố (`A02`).
- **UC20:** Chốt học kỳ & tổng hợp GPA (`A02`).
- **UC21:** Xem báo cáo thống kê (`A01, A02`).

## 3. Danh mục 17 quy tắc nghiệp vụ (`BR01–BR17`)
- **BR01:** Phân quyền truy cập chặt chẽ theo từng vai trò.
- **BR02:** Mã định danh duy nhất toàn hệ thống; mã lớp học phần duy nhất trong phạm vi `(học kỳ, môn)`.
- **BR03:** Chỉ được đăng ký khi học kỳ mở đăng ký và nằm trong đợt đăng ký riêng của khóa sinh viên.
- **BR04:** Sinh viên phải ở trạng thái `ACTIVE` và không bị khóa đăng ký (`student_holds`).
- **BR05:** Chỉ đăng ký môn thuộc CTĐT của mình và chưa đạt ở kỳ trước.
- **BR06:** Phải đạt đủ môn tiên quyết; đồ thị môn tiên quyết không được có chu trình đệ quy.
- **BR07:** Tối đa 01 đăng ký còn hiệu lực (`REGISTERED`) cho cùng một môn trong một học kỳ.
- **BR08:** Không vượt sức chứa; tạo đăng ký và tăng sĩ số trong cùng một giao dịch nguyên tử.
- **BR09:** Không trùng lịch học (thứ, tiết, khoảng ngày học) giữa các lớp đã đăng ký.
- **BR10:** Không vượt giới hạn tín chỉ tối đa của học kỳ.
- **BR11:** Chỉ hủy trước hạn hủy và khi lớp chưa có điểm; hủy giảm sĩ số đúng 1, hủy lặp không giảm thêm.
- **BR12:** Không trùng lịch phòng học hoặc giảng viên khi mở lớp/xếp lịch.
- **BR13:** Điểm thang `0–10` và chỉ nhập cho sinh viên thuộc lớp giảng viên phụ trách.
- **BR14:** Điểm đã công bố bị khóa; sửa trực tiếp bị trigger chặn, phải qua thủ tục có lý do và ghi `audit_logs`.
- **BR15:** GPA theo thang 4; môn học lại lấy lần có điểm cao nhất để tính GPA tích lũy.
- **BR16:** Chống gửi lặp yêu cầu đăng ký bằng khóa chống lặp (`idempotency_key`).
- **BR17:** Không xóa vật lý dữ liệu lịch sử học vụ và nhật ký; danh mục ngừng dùng thì đặt `is_active = FALSE`.
