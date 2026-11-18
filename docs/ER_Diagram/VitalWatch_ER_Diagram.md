# VitalWatch Entity Relationship Diagram

The diagram contains the six entities listed in the project specification.

```mermaid
erDiagram
    WARD ||--o{ PATIENT : "assigned to (inferred)"
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

## Relationship note

The specification explicitly lists four relationships: Patient–Device, Device–VitalReading, Patient–Alert, and Patient–CareTeamAssignment.

The Ward–Patient relationship is inferred from the Patient entity's WardID field. Confirm with the trainer whether WardID should be implemented as a foreign key before finalizing the database schema.

## Design note

The entity names and attribute names follow the project specification. The SQL data types shown here are provisional and will be finalized during MySQL 8 schema design.
