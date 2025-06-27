# Modelo de Datos (Colecciones MongoDB)

```mermaid
erDiagram
    USER {
        string id "ObjectId"
        string name "Nullable"
        string email "Unique, Nullable"
        Role role "Enum: ADMIN, DOCENTE, ESTUDIANTE"
        string password "Hashed, Nullable"
        string enrolledSubjectIds "Array of ObjectId, references SUBJECT"
    }

    SUBJECT {
        string id "ObjectId"
        string name
        string code "Unique"
        string teacherId "ObjectId, references USER"
        string studentIds "Array of ObjectId, references USER"
    }

    "CLASS" {
        string id "ObjectId"
        datetime date
        string topic "Nullable"
        ClassStatus status "Enum: PROGRAMADA, REALIZADA, CANCELADA"
        string subjectId "ObjectId, references SUBJECT"
    }

    ATTENDANCE {
        string id "ObjectId"
        AttendanceStatus status "Enum: PRESENTE, AUSENTE, TARDANZA, JUSTIFICADO"
        string studentId "ObjectId, references USER"
        string classId "ObjectId, references CLASS"
    }

    QRCODE {
        string id "ObjectId"
        string token "Unique"
        datetime expiresAt
        boolean isActive
        string classId "ObjectId, references CLASS"
    }

    ATTENDANCE_LOG {
        string id "ObjectId"
        AttendanceStatus oldStatus "Nullable"
        AttendanceStatus newStatus
        string attendanceId "ObjectId, references ATTENDANCE"
        string changedById "ObjectId, references USER"
    }

    USER ||--o{ SUBJECT : teaches
    SUBJECT ||--o{ "CLASS" : schedules
    "CLASS" ||--o{ ATTENDANCE : records
    USER ||--o{ ATTENDANCE : "has attendance for"
    "CLASS" ||--o{ QRCODE : generates
    ATTENDANCE ||--o{ ATTENDANCE_LOG : logs
    USER ||--o{ ATTENDANCE_LOG : "is changed by"
```
