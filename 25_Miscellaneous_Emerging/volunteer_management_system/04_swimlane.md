# Swimlane Diagram — Volunteer Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Volunteer"]
        V1["Browse Opportunities & Select Shift"]
        V2["Submit Application & Profile"]
        V3["Perform Mobile Check-In at Event"]
        V4["Perform Mobile Check-Out & Log Notes"]
    end

    subgraph Lane2["System"]
        S1["Verify Qualification & Skill Match"]
        S2{"Background Check Required?"}
        S3["Send Verification Request to API"]
        S4{"Verification Passed?"}
        S5["Confirm Shift Assignment & Notify"]
        S6["Validate GPS Location & Timestamp"]
        S7["Calculate Duration & Queue Timesheet"]
        S8["Update Verified Hours & Award Certificate"]
    end

    subgraph Lane3["Background Check API"]
        B1["Perform Identity & Safety Screening"]
        B2["Return Screening Status Code"]
    end

    subgraph Lane4["Event Coordinator"]
        C1["Review Application Roster"]
        C2{"Approve Applicant?"}
        C3["Verify Event Attendance & Approve Hours"]
    end

    Finish(["End"])

    Start --> V1 --> V2 --> S1 --> S2
    S2 -->|"Yes"| S3 --> B1 --> B2 --> S4
    S2 -->|"No"| C1
    S4 -->|"Yes"| C1
    S4 -->|"No"| C2
    C1 --> C2
    C2 -->|"Yes"| S5 --> V3 --> S6 --> V4 --> S7 --> C3 --> S8 --> Finish
    C2 -->|"No"| Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Volunteer | Initiates application, selects shift preferences, performs mobile GPS check-in/out on event day, and submits work logs. |
| 2 | System | Automates qualification checks, routes screening requests, validates real-time attendance timestamps, calculates hours, and issues certificates. |
| 3 | Background Check API | Receives identity payloads, executes background checks against criminal databases, and returns clearance status. |
| 4 | Event Coordinator | Evaluates applicant profiles, confirms shift assignments, supervises on-site attendance, and approves final service timesheets. |
