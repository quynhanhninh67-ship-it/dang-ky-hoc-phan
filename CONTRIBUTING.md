# Quy định đóng góp mã nguồn & tài liệu (`CONTRIBUTING.md`)

Tài liệu này thống nhất cách làm việc chung của nhóm trên kho `dang-ky-hoc-phan` để mã nguồn và tài liệu luôn rõ ràng, dễ theo dõi và hạn chế xung đột.

## 1. Phân công phụ trách chính

| Thành viên | Vai trò chính | Phạm vi phụ trách |
| :--- | :--- | :--- |
| **Ninh Quỳnh Anh** | Trưởng nhóm / BA | Đặc tả nghiệp vụ, điều phối công việc & PR, báo cáo, slide, phụ lục AI, truy vấn `Q03`, `Q04`, `Q11`, `Q16` |
| **Nguyễn Hoàng Anh** | DB Architect | ERD 3NF, từ điển dữ liệu, script tạo bảng, dữ liệu mẫu, truy vấn `Q01`, `Q02`, `Q06`, `Q20` |
| **Lê Duy Anh** | DBA | Stored Procedure, Function, Trigger, View, Index, phân quyền, xử lý đồng thời, sao lưu/phục hồi, truy vấn `Q07`, `Q09`, `Q10`, `Q18` |
| **Hà Đức Anh** | Backend Java | Kết nối JDBC, DAO/Service/Model, transaction, idempotency, xác thực & phân quyền, truy vấn `Q05`, `Q08`, `Q12`, `Q13` |
| **Tạ Đức Anh** | Giao diện & Kiểm thử | Giao diện Java Swing trên NetBeans, kiểm thử Testcontainers, kịch bản kiểm thử `T01–T20`, video demo, truy vấn `Q14`, `Q15`, `Q17`, `Q19` |

## 2. Quy tắc làm việc với nhánh (`Branch`)
- Không đẩy trực tiếp các thay đổi lớn hoặc mã nguồn/SQL mới lên nhánh `main`.
- Tạo nhánh riêng từ `main` đã cập nhật mới nhất theo từng loại công việc:
  - `docs/<ten-viec>` — tài liệu, đặc tả, ERD, báo cáo
  - `db/<ten-viec>` — script CSDL, thủ tục, hàm, trigger, view, index, dữ liệu mẫu, truy vấn
  - `feat/<ten-viec>` — mã nguồn Java, giao diện Swing
  - `test/<ten-viec>` — kiểm thử tự động và kịch bản kiểm thử

## 3. Quy tắc Commit
- Mỗi thành viên sử dụng tài khoản GitHub cá nhân khi thực hiện commit.
- Đặt thông điệp commit ngắn gọn, đúng nội dung thay đổi:
  - `docs: cap nhat dac ta va tai lieu du an`
  - `db: them script tao bang va du lieu mau`
  - `feat: hoan thien chuc nang dang ky hoc phan`
  - `test: them testcontainers kiem tra nghiep vu`

## 4. Quy trình Pull Request & Review chéo
- Khi hoàn thành một phần việc trên nhánh riêng, mở **Pull Request (PR)** vào `main` và ghi rõ nội dung thay đổi.
- Mỗi PR cần ít nhất **01 thành viên review chéo** trước khi gộp vào `main`.
- Kiểm tra kỹ không để lộ mật khẩu thật, thông tin nhạy cảm hay file `.env` cá nhân trước khi mở PR.
