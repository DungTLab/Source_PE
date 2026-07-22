# Swimlane Diagram — Cultural Institution Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Exhibition Visitor"]
        V1["Select Timed Slot & Purchase Ticket"]
        V2["Scan QR Code Pass at Turnstile Gate"]
        V3["Stream AR Audio Guide on Mobile"]
    end

    subgraph Lane2["System"]
        S1["Reserve Timed-Entry Slot Capacity"]
        S2["Generate Encrypted QR Code Pass"]
        S3{"Ticket Pass Valid & Slot Active?"}
        S4["Deny Entry & Flash Red Gate Alert"]
        S5["Unlock Turnstile & Log Attendance"]
        S6["Deliver Location-Aware AR Exhibit Guide"]
    end

    subgraph Lane3["Ticketing & Access Gateway"]
        G1["Scan Visitor QR Ticket Barcode"]
        G2["Rotate Physical Gate Turnstile"]
    end

    subgraph Lane4["Museum Curator / Art Registrar"]
        C1["Review Live Gallery Crowd Density"]
        C2["Adjust Gallery Timed-Entry Capacity"]
    end

    Finish(["End"])

    Start --> V1 --> S1 --> S2 --> V2 --> G1 --> S3
    S3 -->|"No"| S4 --> Finish
    S3 -->|"Yes"| S5 --> G2 --> V3 --> S6 --> C1 --> C2 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Exhibition Visitor | Selects timed-entry slot, purchases exhibition ticket online, scans QR code pass at turnstile gate, and streams AR audio guide on mobile device. |
| 2 | System | Reserves slot capacity, generates encrypted QR code pass, verifies pass validity and slot timestamps, unlocks turnstile, logs entry, and streams AR content. |
| 3 | Ticketing & Access Gateway | Scans visitor QR ticket barcode at entrance turnstile, verifies hardware handshake, and physically rotates gate arm to admit visitor. |
| 4 | Museum Curator / Art Registrar | Monitors live gallery crowd density on EOC dashboard and dynamically adjusts hourly timed-entry ticket capacity limits. |
