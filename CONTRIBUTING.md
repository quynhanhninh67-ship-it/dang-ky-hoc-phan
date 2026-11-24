# Quy định đóng góp mã nguồn & tài liệu (`CONTRIBUTING.md`)

Tài liệu này quy định cách 05 thành viên nhóm làm việc trên kho GitHub `dang-ky-hoc-phan` để tránh xung đột file, giữ lịch sử commit rõ ràng và đảm bảo mỗi người đều có đóng góp minh bạch khi chấm điểm[cite: 2].

## 1. Phân công & phạm vi làm việc

| Thành viên | Vai trò chính | Khu vực phụ trách chính |
| :--- | :--- | :--- |
| **Ninh Quỳnh Anh** | Trưởng nhóm / BA | Đặc tả nghiệp vụ, quản lý issue/PR, báo cáo, slide, phụ lục AI, câu SQL `Q03, Q04, Q11, Q16`[cite: 2]. |
| **Nguyễn Hoàng Anh** | DB Architect | ERD 3NF, từ điển dữ liệu, migration 20 bảng, seed dữ liệu, câu SQL `Q01, Q02, Q06, Q20`[cite: 2]. |
| **Lê Duy Anh** | DBA | Stored Procedure, Function, Trigger, View, Index, phân quyền, đồng thời, backup/restore, câu SQL `Q07, Q09, Q10, Q18`[cite: 2]. |
| **Hà Đức Anh** | Backend Java | Kết nối JDBC, DAO/Service/Model, transaction, idempotency, phân quyền/bcrypt, câu SQL `Q05, Q08, Q12, Q13`[cite: 2]. |
| **Tạ Đức Anh** | Giao diện & Kiểm thử | Giao diện Java Swing trên NetBeans, test Testcontainers, biên bản `T01–T20`, video demo, câu SQL `Q14, Q15, Q17, Q19`[cite: 2]. |

## 2. Quy tắc dùng nhánh (`Branch`)
- **Không push trực tiếp lên `main`** cho các thay đổi lớn hoặc code/SQL mới. Nhánh `main` chỉ nhận phần đã được kiểm tra.
- Trước khi làm task mới, cập nhật `main` mới nhất rồi tạo nhánh riêng từ `main`:
  - `docs/<ten-viec>` — tài liệu, đặc tả, ERD, báo cáo
  - `db/<ten-viec>` — migration, thủ tục, hàm, trigger, view, index, seed, queries
  - `feat/<ten-viec>` — code Java, giao diện Swing
  - `test/<ten-viec>` — kiểm thử tự động / kịch bản kiểm thử

## 3. Quy tắc Commit
- **Mỗi người bắt buộc dùng tài khoản GitHub cá nhân** để commit phần việc của mình[cite: 2].
- Viết commit message rõ ràng, đúng nội dung, ưu tiên tiếng Việt không dấu hoặc tiếng Anh:
  - `docs: them dac ta 21 use case va 17 quy tac nghiep vu`
  - `db: tao migration 20 bang tren MySQL`
  - `feat: hoan thien man hinh dang ky hoc phan Swing`
  - `test: them test 50 sinh vien tranh 1 cho trong`

## 4. Pull Request (PR) & Review chéo
- Hoàn thành task thì mở **Pull Request** vào `main` và gắn với task/issue trên **GitHub Projects**[cite: 2].
- Mỗi PR cần ít nhất **01 người review chéo** trước khi merge[cite: 2]:
  - Tài liệu / đặc tả: **Quỳnh Anh** ↔ **Hoàng Anh**[cite: 2]
  - CSDL / SQL: **Hoàng Anh** ↔ **Duy Anh**[cite: 2]
  - Java / Swing / Test: **Hà Đức Anh** ↔ **Tạ Đức Anh**[cite: 2]

## 5. Lưu ý bắt buộc
- **Không đẩy mật khẩu thật, API key hoặc file cấu hình cá nhân** lên GitHub[cite: 2].
- Nếu sửa tên bảng, tên cột hoặc tham số thủ tục/hàm CSDL, phải báo ngay cho cả nhóm để đồng bộ code và từ điển dữ liệu.
