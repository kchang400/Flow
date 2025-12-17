```mermaid
flowchart LR

    %% Pilot Manager Lane
    subgraph PM[ Pilot Manager ]
        A[Receive Flight Schedule]
        B[Assign Pilot]
        C[Assign Location]
        D[Schedule Hours]
        E[Review Allotted Time]
        F[Publish Shift to Employees]
    end

    %% Pilot Lane
    subgraph P[ Pilot ]
        G[Review Shift]
        H{Needs Changes?}
        I[Request Changes]
        J[Confirm Shift]
        K[Clock In]
        L[Complete Safe to Fly]
        M[Clock Out]
    end

    %% Automated Lane
    subgraph AUTO[ Automated System ]
        N[Match Work Time to Shift]
        O[Create Timecard]
        P2[Export Hours to FAA / Workday / etc.]
    end

    %% Connections
    A --> B --> C --> D --> E --> F --> G
    G --> H

    H -->|Yes| I --> E
    H -->|No| J --> K --> L --> M --> N --> O --> P2
    
