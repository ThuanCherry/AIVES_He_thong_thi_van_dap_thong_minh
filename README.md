# AIVES – AI-powered Viva Exam System

AIVES (AI-powered Viva Exam System) là hệ thống thi vấn đáp thông minh có ứng dụng AI, hướng tới hỗ trợ quá trình tổ chức thi vấn đáp, đặt câu hỏi, hỏi tiếp dựa trên câu trả lời của sinh viên, hỗ trợ chấm điểm theo rubric và lưu lại quá trình thi.

## 1. Mục tiêu dự án

Thi vấn đáp thường được sử dụng trong các hoạt động như bảo vệ đồ án, thi cuối kỳ và phỏng vấn đánh giá năng lực. Tuy nhiên, hình thức này có thể gặp một số khó khăn:

- Tốn nhiều thời gian của giảng viên.
- Khó chuẩn hóa câu hỏi và cách chấm giữa các phòng thi.
- Khó mở rộng khi số lượng sinh viên lớn.
- Thiếu bằng chứng khách quan như transcript và điểm theo từng câu hỏi khi cần đối chiếu kết quả.

AIVES được xây dựng nhằm hỗ trợ giải quyết các vấn đề trên bằng cách ứng dụng AI vào quy trình thi vấn đáp.

## 2. Actors

Theo phạm vi Topic hiện tại, hệ thống có ba nhóm người dùng chính:

- **Quản trị viên (Administrator)**
- **Giảng viên (Lecturer)** – người ra đề / coi thi
- **Sinh viên (Student)** – thí sinh

> Chức năng chi tiết của Quản trị viên chưa được mô tả rõ trong Topic hiện tại.

## 3. Các chức năng chính

### Exam & Schedule Management

- Giảng viên tạo kỳ / phiên thi vấn đáp.
- Gắn kỳ thi với môn học.
- Thiết lập danh sách sinh viên tham gia.
- Thiết lập thời gian thi cho mỗi thí sinh.
- Thiết lập số lượng câu hỏi chính.
- Thiết lập số lượng câu hỏi phụ tối đa.

### Question Management

- Hỗ trợ tạo câu hỏi.
- Lựa chọn bộ câu hỏi cho từng sinh viên.
- Có thể lựa chọn ngẫu nhiên hoặc thích ứng.
- Hạn chế lặp lại câu hỏi giữa các thí sinh liên tiếp.

### AI Viva Examination

- AI đặt câu hỏi cho sinh viên.
- AI có thể đặt câu hỏi tiếp theo dựa trên câu trả lời trước đó của sinh viên.

### Rubric & Evaluation

- Hỗ trợ đánh giá câu trả lời dựa trên rubric.
- Hỗ trợ lưu điểm theo từng câu hỏi.

### Transcript & Exam Trace

- Lưu transcript của quá trình thi.
- Lưu lại quá trình tương tác trong phiên thi để phục vụ việc xem lại và đối chiếu.

## 4. Công nghệ sử dụng

### Frontend

- React
- TypeScript
- Vite

### Backend

- ASP.NET Core Web API
- C#

Backend sử dụng kiến trúc **3-Layer Architecture**:

```text
Presentation Layer
        ↓
Business Logic Layer
        ↓
Data Access Layer
        ↓
MySQL
```

### Database

- MySQL

## 5. Cấu trúc project

```text
AIVES_He_thong_thi_van_dap_thong_minh/
│
├── src/
│   ├── frontend/
│   │   ├── src/
│   │   │   ├── app/
│   │   │   ├── assets/
│   │   │   ├── components/
│   │   │   ├── features/
│   │   │   │   ├── exams/
│   │   │   │   ├── questions/
│   │   │   │   ├── viva/
│   │   │   │   ├── evaluations/
│   │   │   │   └── transcripts/
│   │   │   ├── hooks/
│   │   │   ├── services/
│   │   │   ├── types/
│   │   │   └── utils/
│   │   └── package.json
│   │
│   └── backend/
│       ├── AIVES.sln
│       │
│       ├── AIVES.Presentation/
│       │   ├── Controllers/
│       │   ├── Middleware/
│       │   ├── Models/
│       │   └── Extensions/
│       │
│       ├── AIVES.BusinessLogic/
│       │   ├── DTOs/
│       │   ├── Interfaces/
│       │   ├── Services/
│       │   ├── Validators/
│       │   ├── Mappings/
│       │   └── Helpers/
│       │
│       └── AIVES.DataAccess/
│           ├── Data/
│           ├── Entities/
│           ├── Interfaces/
│           ├── Repositories/
│           ├── Configurations/
│           └── Migrations/
│
├── README.md
└── .gitignore
```

## 6. Backend Architecture

### Presentation Layer

Chịu trách nhiệm nhận HTTP request từ frontend và trả HTTP response.

Các thành phần dự kiến:

- Controllers
- Middleware
- Request / Response Models
- Dependency Injection configuration

### Business Logic Layer

Chứa các quy tắc nghiệp vụ chính của hệ thống.

Các thành phần dự kiến:

- DTOs
- Service interfaces
- Services
- Validators
- Mappings
- Helpers

### Data Access Layer

Chịu trách nhiệm làm việc với dữ liệu và MySQL.

Các thành phần dự kiến:

- Entities
- Database context / connection
- Repository interfaces
- Repositories
- Entity configurations
- Database migrations

## 7. Các entity dự kiến

Dựa trên Topic hiện tại, một số entity cần được phân tích thêm trước khi thiết kế database chính thức:

- Subject
- Lecturer
- Student
- ExamSession
- ExamCandidate
- Question
- ExamQuestion
- Answer
- TranscriptEntry / Interaction
- Rubric
- Evaluation
- QuestionScore

> Database schema hiện chưa được chốt. Các entity và relationship sẽ được điều chỉnh sau khi hoàn tất phân tích requirement.

## 8. Trạng thái hiện tại

Project hiện đang ở giai đoạn:

```text
Requirement Analysis
        ↓
Project Structure
        ↓
Database Design
        ↓
API Design
        ↓
Implementation
```

Hiện tại chưa bắt đầu implementation chức năng chính và chưa chốt database schema.

## 9. Những nội dung cần làm rõ

Một số nội dung chưa được Topic hiện tại mô tả đủ chi tiết:

- Chức năng cụ thể của Administrator.
- Authentication / Login / Account Management.
- Nguồn dữ liệu sinh viên và môn học.
- Cách tổ chức lịch thi.
- Cách AI tạo câu hỏi.
- Cấu trúc Question Bank.
- Tiêu chí lựa chọn câu hỏi adaptive.
- Phạm vi kiểm tra câu hỏi bị lặp.
- Cấu trúc rubric.
- Ai là người quyết định điểm cuối cùng.
- Transcript chỉ lưu text hay cần lưu thêm audio/video.

Các nội dung trên cần được xác nhận trước khi thiết kế database và business rules chính thức.

## 10. Repository

Repository này dùng để phát triển hệ thống **AIVES – AI-powered Viva Exam System**.

---

> README sẽ tiếp tục được cập nhật khi requirement, database schema, API và các chức năng của hệ thống được hoàn thiện.
