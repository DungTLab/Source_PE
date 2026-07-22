# Context Diagram — Cultural Institution Management System

## Mermaid Code

```mermaid
flowchart LR
    MuseumCurator["Museum Curator / Art Registrar"]
    ExhibitionVisitor["Exhibition Visitor"]
    InstitutionDirector["Institution Director"]
    ConservationSensor["Conservation Sensor Network"]
    TicketingGateway["Ticketing & Access Gateway"]
    DigitalArchivalSystem["Digital Archival System"]
    PerformingArtsSystem["Performing Arts Booking System"]
    HeritageAuthority["Cultural Heritage Authority"]
    DonorManagementSystem["Donor & Grant Management System"]

    System(("Cultural Institution Management System"))

    MuseumCurator -->|"submits artifact cataloging & loan agreements"| System
    System -->|"returns provenance histories & condition report logs"| MuseumCurator

    ExhibitionVisitor -->|"submits timed ticket reservations & AR queries"| System
    System -->|"provides digital QR entry passes & audio guide streams"| ExhibitionVisitor

    InstitutionDirector -->|"submits gallery curation goals & budget approvals"| System
    System -->|"provides attendance analytics & exhibition revenue reports"| InstitutionDirector

    ConservationSensor -->|"streams lux, temperature, & humidity telemetry"| System
    System -->|"configures climate thresholds & environmental alarms"| ConservationSensor

    System -->|"dispatches QR ticket validation payloads"| TicketingGateway
    TicketingGateway -->|"returns turnstile entry scans & gate access logs"| System

    System -->|"queries high-resolution 3D artifact scans & manuscripts"| DigitalArchivalSystem
    DigitalArchivalSystem -->|"returns digital archival assets & IIIF manifests"| System

    System -->|"dispatches auditorium seating reservations & showtimes"| PerformingArtsSystem
    PerformingArtsSystem -->|"returns box office sales & ticket confirmations"| System

    System -->|"transmits national heritage registry compliance filings"| HeritageAuthority
    HeritageAuthority -->|"returns heritage export/import permits & licenses"| HeritageAuthority

    System -->|"exports donor endowment metrics & naming rights"| DonorManagementSystem
    DonorManagementSystem -->|"returns patron sponsorship contributions & grants"| System
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Museum Curator / Art Registrar | Primary | Artifact acquisition details, accession numbers, provenance histories, condition reports, inter-museum loan contracts | Catalog search results, conservation alerts, loan expiration notices, valuation ledgers | Museum staff responsible for artifact preservation, curation, acquisition, and loan management. |
| 2 | Exhibition Visitor | Primary | Timed-entry ticket reservations, membership pass renewals, AR tour guide queries, feedback ratings | QR entry passes, digital exhibition guides, audio tour streams, event schedule notifications | Museum, gallery, or theater visitors booking tickets and engaging with cultural exhibits. |
| 3 | Institution Director | Primary | Exhibition curation approvals, annual operating budgets, naming rights policies, strategic priorities | Attendance dashboards, exhibition ROI analytics, donor contribution summaries, security audit logs | Executive leadership overseeing institution strategy, fundraising, financial growth, and operations. |
| 4 | Conservation Sensor Network | Primary / Hardware | Temperature (°C), relative humidity (%), lux light exposure, UV index, vibration telemetry | Sensor calibration commands, environmental alarm thresholds, battery health alerts | IoT sensors placed inside display cases and galleries to prevent artifact degradation. |
| 5 | Ticketing & Access Gateway | Supporting System | Turnstile QR code entry scans, barcode validation timestamps, attendance gate counters | Ticket validation payloads, gate access permissions, membership pass validity checks | Physical turnstiles, handheld scanners, and barcode readers controlling visitor entry. |
| 6 | Digital Archival System | Supporting System | High-resolution 3D photogrammetry scans, IIIF image manifests, digitized ancient manuscripts | Archival metadata queries, digital asset indexing requests, public research access logs | Enterprise digital repository (DSpace, Omeka) archiving high-definition cultural assets. |
| 7 | Performing Arts Booking System | Supporting System | Auditorium seat availability maps, box office ticket sales receipts, performance showtime updates | Event reservation payloads, seat allocation blocks, artist booking schedules | Ticketing system managing theater performances, concerts, lectures, and film screenings. |
| 8 | Cultural Heritage Authority | Regulatory System | UNESCO heritage classifications, national artifact protection laws, export/import permits | Mandatory heritage inventory filings, artifact loan security protocols, theft incident alerts | Government department of culture or UNESCO auditing historical asset preservation compliance. |
| 9 | Donor & Grant Management System | Supporting System | Patron donation receipts, endowment pledges, grant funding allocations, VIP membership tiers | Donor naming rights allocations, VIP event invitations, sponsorship attribution reports | CRM platform (Raiser's Edge, Salesforce) managing donor relationships and grant funding. |

## System Boundary Description | Mô tả Phạm vi Hệ thống

The **Cultural Institution Management System (CIMS)** is an enterprise museum, gallery, and performing arts administration platform. Inside the system boundary, CIMS manages artifact cataloging, provenance tracking, inter-museum loan agreements, exhibition curation, gallery environmental conservation monitoring, timed-entry visitor ticketing, performing arts auditorium scheduling, AR/VR audio guide delivery, and digital archival asset indexing. External to the system boundary are physical conservation sensors (Conservation Sensor Network), physical entry turnstiles (Ticketing & Access Gateway), enterprise digital archives (Digital Archival System), box office platforms (Performing Arts Booking System), national heritage regulators (Cultural Heritage Authority), and donor CRM software (Donor Management System).
