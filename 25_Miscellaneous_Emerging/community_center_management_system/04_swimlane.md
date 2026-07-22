# Swimlane Diagram — Community Center Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Community Member / Resident"]
        M1["Select Room & Hourly Time Slot"]
        M2["Submit Rental Payment & Security Deposit"]
        M3["Enter 6-Digit PIN on Door Keypad"]
    end

    subgraph Lane2["System"]
        S1["Verify Room Availability & Resident Rate"]
        S2["Process Credit Card Charges via Gateway"]
        S3{"Payment & Insurance Verified?"}
        S4["Issue Payment Decline Notice"]
        S5["Generate Time-Restricted Door Access PIN"]
        S6["Unlock Electronic Door Latch & Log Entry"]
    end

    subgraph Lane3["Access Control & Door Lock Hardware"]
        H1["Capture Keypad PIN Entry Payload"]
        H2["Physically Release Lock Latch Bolt"]
    end

    subgraph Lane4["Center Administrator"]
        A1["Inspect Room Post-Event for Damage"]
        A2["Release Refundable Security Deposit"]
    end

    Finish(["End"])

    Start --> M1 --> S1 --> M2 --> S2 --> S3
    S3 -->|"No"| S4 --> Finish
    S3 -->|"Yes"| S5 --> M3 --> H1 --> S6 --> H2 --> A1 --> A2 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Community Member / Resident | Selects room and hourly time slot, submits rental payment and security deposit, and enters 6-digit PIN on room door keypad. |
| 2 | System | Verifies room schedule availability, processes credit card charges via gateway, validates event insurance, generates time-restricted door PIN, unlocks door, and logs entry. |
| 3 | Access Control & Door Lock Hardware | Captures keypad PIN entry payload, verifies system authorization handshake, and physically releases door latch bolt. |
| 4 | Center Administrator | Inspects rented room post-event for cleanliness or damage, and authorizes full refund of the security deposit. |
