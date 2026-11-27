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
├── app/                   # Mã nguồn Java (tầng nghiệp vụ/DAO/JDBC & Swing)
├── database/              # Migration, SQL, thủ tục, hàm, trigger, view, seed, backup
├── docs/                  # Đặc tả, ERD, từ điển dữ liệu, báo cáo, slide, kiểm thử
├── tests/
│   └── testcontainers/      # Kiểm thử tự động Testcontainers trên MySQL
├── .env.example           # Mẫu biến môi trường kết nối CSDL (không chứa bí mật thật)
├── docker-compose.yml     # Dựng dịch vụ MySQL cục bộ
├── CONTRIBUTING.md        # Quy định đóng góp mã nguồn, nhánh, PR & review chéo
└── README.md              # Tổng quan dự án và hướng dẫn khởi tạo
