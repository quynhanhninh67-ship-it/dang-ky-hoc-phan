# Hệ thống Đăng ký Học phần (Đề tài DT04)

- **Học phần:** Đồ án Cơ sở dữ liệu (Hệ đào tạo Đại học chính quy — Lớp 75DCHT22)
- **Đơn vị đào tạo:** Bộ môn Hệ thống thông tin – Khoa Công nghệ thông tin, Trường Đại học Công nghệ Giao thông Vận tải (UTT)
- **Giảng viên hướng dẫn:** Thầy Trần Đức Thắng
- **Kho lưu trữ mã nguồn:** https://github.com/quynhanhninh67-ship-it/dang-ky-hoc-phan.git

## Thành viên nhóm (05 người)
1. **Ninh Quỳnh Anh** — Trưởng nhóm / Phân tích nghiệp vụ (BA)
2. **Nguyễn Hoàng Anh** — Thiết kế Cơ sở dữ liệu (DB Architect)
3. **Lê Duy Anh** — Lập trình CSDL & Quản trị (DBA)
4. **Hà Đức Anh** — Phát triển Backend & Tích hợp hệ thống (Java)
5. **Tạ Đức Anh** — Phát triển Giao diện & Kiểm thử (Java Swing / Kiểm thử)

## Kiến trúc & Công nghệ
- **Cơ sở dữ liệu:** MySQL (`utf8mb4`), thiết kế đạt chuẩn tối thiểu 3NF (20 bảng), Stored Procedure, Function, Trigger, View (có view phân quyền), Index, phân quyền vai trò (`db_migrator`, `app_rw`, `reporting_ro`) và sao lưu/phục hồi bằng `mysqldump`.
- **Tầng ứng dụng & giao diện:** Java / JDBC / DAO / Service và giao diện desktop Java Swing trên NetBeans.
- **Kiểm thử & triển khai:** Testcontainers trên MySQL thật, `docker-compose.yml` và `.env.example`.

## Cấu trúc thư mục
```text
dang-ky-hoc-phan/
├── app/                   # Mã nguồn ứng dụng Java (tầng nghiệp vụ/DAO/JDBC & Java Swing)
├── database/              # Script migration, thủ tục, hàm, trigger, view, index, seed, queries.sql, backup/restore
├── docs/                  # Tài liệu đặc tả, ERD, từ điển dữ liệu, báo cáo, slide, biên bản kiểm thử
├── tests/
│   └── testcontainers/      # Bộ kiểm thử tự động Testcontainers chạy trên MySQL
├── .env.example           # Mẫu biến môi trường kết nối CSDL (không chứa thông tin nhạy cảm thật)
├── docker-compose.yml     # Cấu hình dựng dịch vụ MySQL cục bộ
├── CONTRIBUTING.md        # Quy ước làm việc nhóm, nhánh, PR và review chéo
└── README.md              # Tổng quan dự án và hướng dẫn triển khai
