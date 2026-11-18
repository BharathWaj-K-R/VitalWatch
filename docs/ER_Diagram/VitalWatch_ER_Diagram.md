
```mermaid
YOUR ER DIAGRAM CODE

erDiagram
    WARD ||--o{ PATIENT : "assigned to (implied)"
    PATIENT ||--o{ DEVICE : owns
    DEVICE ||--o{ VITAL_READING : generates
    PATIENT ||--o{ ALERT : receives
    PATIENT ||--o{ CARE_TEAM_ASSIGNMENT : assigned

    WARD {
        int WardID PK
        varchar WardName
    }

    PATIENT {
        int PatientID PK
        varchar FirstName
        varchar LastName
        int WardID FK
        varchar Status
    }

    DEVICE {
        int DeviceID PK
        int PatientID FK
        varchar DeviceType
        varchar Status
    }

    VITAL_READING {
        int ReadingID PK
        int DeviceID FK
        varchar VitalType
        decimal ReadingValue
        datetime RecordedAt
    }

    ALERT {
        int AlertID PK
        int PatientID FK
        varchar Severity
        datetime TriggeredAt
        varchar Status
        varchar AcknowledgedBy
    }

    CARE_TEAM_ASSIGNMENT {
        int AssignmentID PK
        int PatientID FK
        int NurseID
        datetime AssignedFrom
    }
  ```