# Hệ thống Đăng ký Học phần (Đề tài DT04)

- **Học phần:** Đồ án Cơ sở dữ liệu — Lớp 75DCHT22
- **Đơn vị đào tạo:** Bộ môn Hệ thống thông tin – Khoa Công nghệ Thông tin, Trường Đại học Công nghệ Giao thông Vận tải (UTT)
- **Giảng viên hướng dẫn:** Thầy Trần Đức Thắng
- **Kho lưu trữ mã nguồn:** https://github.com/quynhanhninh67-ship-it/dang-ky-hoc-phan.git

---

## 1. Giới thiệu đề tài
Hệ thống hỗ trợ quản lý xuyên suốt vòng đời học vụ đăng ký học phần: quản lý danh mục đào tạo (khoa, chương trình đào tạo, môn học, môn tiên quyết), học kỳ & đợt đăng ký theo khóa, mở lớp học phần & xếp lịch tuần, đăng ký/hủy học phần chống tranh chấp đồng thời, nhập/công bố/điều chỉnh điểm có nhật ký kiểm toán (`audit_logs`), tính GPA học kỳ/tích lũy (chọn điểm cao nhất khi học lại), chốt học kỳ và báo cáo thống kê.

## 2. Công nghệ sử dụng
- **Hệ quản trị CSDL:** MySQL 8.x (`utf8mb4`)
- **Ngôn ngữ & Tầng nghiệp vụ:** Java (JDBC / DAO / Service / Transaction)
- **Giao diện người dùng:** Java Swing (phát triển trên Apache NetBeans)
- **Kiểm thử tự động:** JUnit & Testcontainers (chạy trên MySQL thật)

## 3. Thành viên nhóm & Phân công (05 thành viên)

| STT | Thành viên | Vai trò chính | Câu SQL phụ trách |
| :-: | :--- | :--- | :--- |
| 1 | **Ninh Quỳnh Anh** | Trưởng nhóm / Phân tích nghiệp vụ (BA) | `Q03, Q04, Q11, Q16` |
| 2 | **Nguyễn Hoàng Anh** | Thiết kế Cơ sở dữ liệu (DB Architect) | `Q01, Q02, Q06, Q20` |
| 3 | **Lê Duy Anh** | Lập trình CSDL & Quản trị (DBA) | `Q07, Q09, Q10, Q18` |
| 4 | **Hà Đức Anh** | Phát triển Backend & Tích hợp hệ thống (Java) | `Q05, Q08, Q12, Q13` |
| 5 | **Tạ Đức Anh** | Phát triển Giao diện (Java Swing) & Kiểm thử | `Q14, Q15, Q17, Q19` |

## 4. Cấu trúc thư mục dự án

```text
dang-ky-hoc-phan/
├── database/
│   ├── migrations/      # Script DDL tạo 20 bảng, khóa, ràng buộc, chỉ mục
│   ├── routines/        # Stored Procedures, Functions, Triggers, Views
│   ├── security/        # Phân quyền vai trò CSDL (db_migrator, app_rw, reporting_ro)
│   ├── seeds/           # Dữ liệu mẫu tiếng Việt (>= 10.000 và >= 100.000 bản ghi)
│   ├── backup/          # Script sao lưu và phục hồi bằng mysqldump
│   └── queries.sql      # Bộ 20 truy vấn nghiệp vụ (Q01 - Q20)
├── src/                 # Mã nguồn Java (DAO, Service, Model, Security, Giao diện Java Swing)
├── test/                # Bộ kiểm thử tự động Testcontainers & biên bản kiểm thử
├── docs/                # Đặc tả Use Case, quy tắc BR01-BR17, ERD, từ điển dữ liệu
├── README.md
└── CONTRIBUTING.md
