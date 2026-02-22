erDiagram

    AUTHOR {
        int AuthorID PK
        string Name
    }

    PLAY {
        int PlayID PK
        string Title
        int AuthorID FK
    }

    THEATRE {
        int TheatreID PK
        string Name
        int MaxAuditoriumSize
    }

    PERFORMANCE {
        int PerformanceID PK
        date PerformanceDate
        string TimeOfDay
        decimal RoyaltyPaid
        int PlayID FK
        int TheatreID FK
    }

    ACTOR {
        int ActorID PK
        string Name
    }

    AGENT {
        int AgentID PK
        string Name
        decimal CommissionPercentage
    }

    ROLE {
        int RoleID PK
        string RoleType
        string SpeakingType
        string Gender
        int PlayID FK
    }

    BOOKING {
        int BookingID PK
        decimal FeePaid
        int ActorID FK
        int RoleID FK
        int AgentID FK
    }

    AUTHOR ||--o{ PLAY : writes
    PLAY ||--o{ PERFORMANCE : performed_as
    THEATRE ||--o{ PERFORMANCE : hosts
    PLAY ||--o{ ROLE : has
    ACTOR ||--o{ BOOKING : books
    ROLE ||--o{ BOOKING : assigned
    AGENT ||--o{ BOOKING : manages
