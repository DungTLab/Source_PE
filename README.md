# Source_PE — Huong dan su dung

> He thong tai lieu thi tu dong cho mon **SWR302**
> AI dong vai BA Senior tu dong sinh diagram Mermaid + bang mo ta song ngu
>
> **Version**: 3.0 | **Updated**: 2026-07-22

---

## Cau truc thu muc

```text
Source_PE/
|-- README.md              <-- File nay
|-- AGENTS.md              <-- Dinh nghia vai tro AI (BA Senior) + tieu chuan chat luong
|-- PROMPT.md              <-- Master prompt de goi AI tao he thong moi
|
|-- 01_Education_Learning/         <-- Moi domain = 1 folder
|   |-- _systems_list.md           <-- Danh sach he thong thuoc domain
|   |-- student_information_system/    <-- Moi he thong = 1 folder con
|   |   |-- 01_context_diagram.md
|   |   |-- 02_usecase_diagram.md
|   |   |-- 03_erd.md
|   |   |-- 04_swimlane.md
|   |   |-- 05_action_tree.md
|   |-- ...
|
|-- 02_Healthcare_Medical/
|-- 03_Finance_Banking/
|-- ... (den 25_Miscellaneous_Emerging)
```

---

## Cach tao tai lieu cho he thong moi

### Buoc 1: Mo PROMPT.md
Doc file `PROMPT.md` va copy phan prompt mau (trong khung ``` ```).

### Buoc 2: Dien ten he thong
Thay `[TEN HE THONG]` bang ten he thong trong de thi.
Neu co de bai, paste them noi dung de vao phia sau.

### Buoc 3: Gui cho AI (Gemini/Antigravity)
Paste prompt vao chat -> AI tu xac dinh domain -> tao folder trong domain -> tao 5 file.

### Buoc 4: Dung trong draw.io
1. Mo [draw.io Desktop](https://github.com/jgraph/drawio-desktop/releases)
2. **Extras** -> **Edit Diagram** (hoac Insert -> Advanced -> Mermaid)
3. Paste Mermaid code -> **OK**
4. Tu dong render so do

---

## Y nghia 5 file output

| File | So do | Muc dich | Tieu chuan v3.0 |
|------|-------|----------|-----------------|
| 01_context_diagram.md | Context Diagram | Xac dinh boundary & external actors | >= 6 actors, system hinh tron, actor hinh vuong |
| 02_usecase_diagram.md | Use Case Diagram | Liet ke UC + dac ta 4-5 UC chinh | >= 12 UC, 10 truong/UC spec |
| 03_erd.md | Conceptual ERD | Mo hinh du lieu cot loi | >= 8 entities, 4-8 attributes/entity |
| 04_swimlane.md | Swimlane Diagram | Luong xu ly theo vai tro | >= 3 lanes, decision node |
| 05_action_tree.md | Action Tree | Phan ra chuc nang he thong | >= 5 modules, >= 3 actions/module |

---

## Cac he thong da co tai lieu

| # | Ten he thong | Domain | Folder | Ngay tao |
|---|-------------|--------|--------|----------|
| 1 | Restaurant Management System at Vincom | 05_Food_Restaurant | restaurant_management_vincom/ | 2026-07-21 |
| 2 | IT Service Management (ITSM) System | 23_IT_Software | it_service_management_system/ | 2026-07-22 |
| 3 | Help Desk & Ticketing System | 23_IT_Software | help_desk_and_ticketing_system/ | 2026-07-22 |
| 4 | Software Development Lifecycle Management System | 23_IT_Software | software_development_lifecycle_management_system/ | 2026-07-22 |
| 5 | DevOps Pipeline Management System | 23_IT_Software | devops_pipeline_management_system/ | 2026-07-22 |
| 6 | Cloud Resource Management System | 23_IT_Software | cloud_resource_management_system/ | 2026-07-22 |
| 7 | API Management Platform | 23_IT_Software | api_management_platform/ | 2026-07-22 |
| 8 | Database Administration System | 23_IT_Software | database_administration_system/ | 2026-07-22 |
| 9 | Software Testing Management System | 23_IT_Software | software_testing_management_system/ | 2026-07-22 |
| 10 | IT Asset Management System | 23_IT_Software | it_asset_management_system/ | 2026-07-22 |
| 11 | Network Monitoring System | 23_IT_Software | network_monitoring_system/ | 2026-07-22 |
| 12 | Configuration Management System (CMDB) | 23_IT_Software | configuration_management_system_cmdb/ | 2026-07-22 |
| 13 | Software License Management System | 23_IT_Software | software_license_management_system/ | 2026-07-22 |
| 14 | Backup & Disaster Recovery System | 23_IT_Software | backup_and_disaster_recovery_system/ | 2026-07-22 |
| 15 | Change & Release Management System | 23_IT_Software | change_and_release_management_system/ | 2026-07-22 |
| 16 | Microservices Registry & Management System | 23_IT_Software | microservices_registry_and_management_system/ | 2026-07-22 |
| 17 | Data Governance & Catalog System | 23_IT_Software | data_governance_and_catalog_system/ | 2026-07-22 |
| 18 | Business Intelligence & Analytics Platform | 23_IT_Software | business_intelligence_and_analytics_platform/ | 2026-07-22 |
| 19 | Enterprise Content Management System | 23_IT_Software | enterprise_content_management_system/ | 2026-07-22 |
| 20 | Project Portfolio Management System | 23_IT_Software | project_portfolio_management_system/ | 2026-07-22 |
| 21 | Knowledge Base Management System | 23_IT_Software | knowledge_base_management_system/ | 2026-07-22 |
| 22 | AI & Machine Learning Model Management System | 23_IT_Software | ai_and_machine_learning_model_management_system/ | 2026-07-22 |
| 23 | Data Warehouse Management System | 23_IT_Software | data_warehouse_management_system/ | 2026-07-22 |
| 24 | Robotic Process Automation (RPA) Platform | 23_IT_Software | robotic_process_automation_rpa_platform/ | 2026-07-22 |
| 25 | Low-Code / No-Code Development Platform | 23_IT_Software | low_code_no_code_development_platform/ | 2026-07-22 |
| 26 | DevSecOps Security Management System | 23_IT_Software | devsecops_security_management_system/ | 2026-07-22 |
| 27 | Container & Kubernetes Management System | 23_IT_Software | container_and_kubernetes_management_system/ | 2026-07-22 |
| 28 | IT Capacity Planning System | 23_IT_Software | it_capacity_planning_system/ | 2026-07-22 |
| 29 | Incident & Problem Management System | 23_IT_Software | incident_and_problem_management_system/ | 2026-07-22 |
| 30 | Data Quality Management System | 23_IT_Software | data_quality_management_system/ | 2026-07-22 |
| 31 | Multi-tenant SaaS Platform | 23_IT_Software | multi_tenant_saas_platform/ | 2026-07-22 |
| 32 | Enterprise Integration Platform (EIP) | 23_IT_Software | enterprise_integration_platform_eip/ | 2026-07-22 |
| 33 | IoT Platform & Device Management System | 23_IT_Software | iot_platform_and_device_management_system/ | 2026-07-22 |
| 34 | Serverless Computing Management System | 23_IT_Software | serverless_computing_management_system/ | 2026-07-22 |
| 35 | Edge Computing Management Platform | 23_IT_Software | edge_computing_management_platform/ | 2026-07-22 |
| 36 | Open Source Contribution Management System | 23_IT_Software | open_source_contribution_management_system/ | 2026-07-22 |
| 37 | Software Defect Tracking System | 23_IT_Software | software_defect_tracking_system/ | 2026-07-22 |
| 38 | Technical Documentation Management System | 23_IT_Software | technical_documentation_management_system/ | 2026-07-22 |
| 39 | Code Review & Collaboration Platform | 23_IT_Software | code_review_and_collaboration_platform/ | 2026-07-22 |
| 40 | IT Vendor & Contract Management System | 23_IT_Software | it_vendor_and_contract_management_system/ | 2026-07-22 |
| 41 | Observability & Monitoring Platform | 23_IT_Software | observability_and_monitoring_platform/ | 2026-07-22 |
| 42 | Digital Transformation Management System | 23_IT_Software | digital_transformation_management_system/ | 2026-07-22 |
| 43 | Application Performance Management (APM) System | 23_IT_Software | application_performance_management_apm_system/ | 2026-07-22 |
| 44 | IT Risk Management System | 23_IT_Software | it_risk_management_system/ | 2026-07-22 |
| 45 | Enterprise Service Bus (ESB) System | 23_IT_Software | enterprise_service_bus_esb_system/ | 2026-07-22 |
| 46 | Data Analytics Pipeline System | 23_IT_Software | data_analytics_pipeline_system/ | 2026-07-22 |
| 47 | Software Architecture Documentation System | 23_IT_Software | software_architecture_documentation_system/ | 2026-07-22 |
| 48 | IT Budget & Cost Management System | 23_IT_Software | it_budget_and_cost_management_system/ | 2026-07-22 |
| 49 | Agile & Scrum Project Tracking System | 23_IT_Software | agile_and_scrum_project_tracking_system/ | 2026-07-22 |
| 50 | Tech Talent Acquisition System | 23_IT_Software | tech_talent_acquisition_system/ | 2026-07-22 |
| 51 | Software Quality Assurance (SQA) System | 23_IT_Software | software_quality_assurance_sqa_system/ | 2026-07-22 |
| 52 | Fleet Management System | 06_Transportation_Logistics | fleet_management_system/ | 2026-07-22 |
| 53 | Ride-Hailing Platform | 06_Transportation_Logistics | ride_hailing_platform/ | 2026-07-22 |
| 54 | Freight Management System | 06_Transportation_Logistics | freight_management_system/ | 2026-07-22 |
| 55 | Warehouse Management System | 06_Transportation_Logistics | warehouse_management_system/ | 2026-07-22 |
| 56 | Last-Mile Delivery Management System | 06_Transportation_Logistics | last_mile_delivery_management_system/ | 2026-07-22 |
| 57 | Supply Chain Management System | 06_Transportation_Logistics | supply_chain_management_system/ | 2026-07-22 |
| 58 | Route Optimization System | 06_Transportation_Logistics | route_optimization_system/ | 2026-07-22 |
| 59 | Parcel Tracking System | 06_Transportation_Logistics | parcel_tracking_system/ | 2026-07-22 |
| 60 | Container Terminal Management System | 06_Transportation_Logistics | container_terminal_management_system/ | 2026-07-22 |
| 61 | Cargo Booking System | 06_Transportation_Logistics | cargo_booking_system/ | 2026-07-22 |
| 62 | Cold Chain Logistics System | 06_Transportation_Logistics | cold_chain_logistics_system/ | 2026-07-22 |
| 63 | Public Bus Management System | 06_Transportation_Logistics | public_bus_management_system/ | 2026-07-22 |
| 64 | Taxi Dispatch System | 06_Transportation_Logistics | taxi_dispatch_system/ | 2026-07-22 |
| 65 | Bicycle Sharing System | 06_Transportation_Logistics | bicycle_sharing_system/ | 2026-07-22 |
| 66 | Electric Scooter Sharing System | 06_Transportation_Logistics | electric_scooter_sharing_system/ | 2026-07-22 |
| 67 | Toll Management System | 06_Transportation_Logistics | toll_management_system/ | 2026-07-22 |
| 68 | Vehicle Registration & Licensing System | 06_Transportation_Logistics | vehicle_registration_licensing_system/ | 2026-07-22 |
| 69 | Traffic Management System | 06_Transportation_Logistics | traffic_management_system/ | 2026-07-22 |
| 70 | Intelligent Transportation System (ITS) | 06_Transportation_Logistics | intelligent_transportation_system_its/ | 2026-07-22 |
| 71 | Drone Delivery Management System | 06_Transportation_Logistics | drone_delivery_management_system/ | 2026-07-22 |
| 72 | Customs & Border Control System | 06_Transportation_Logistics | customs_border_control_system/ | 2026-07-22 |
| 73 | Shipment Booking Platform | 06_Transportation_Logistics | shipment_booking_platform/ | 2026-07-22 |
| 74 | Logistics Partner Integration System | 06_Transportation_Logistics | logistics_partner_integration_system/ | 2026-07-22 |
| 75 | Reverse Logistics Management System | 06_Transportation_Logistics | reverse_logistics_management_system/ | 2026-07-22 |
| 76 | Fuel Management System | 06_Transportation_Logistics | fuel_management_system/ | 2026-07-22 |
| 77 | Driver Management & Compliance System | 06_Transportation_Logistics | driver_management_compliance_system/ | 2026-07-22 |
| 78 | Freight Brokerage Platform | 06_Transportation_Logistics | freight_brokerage_platform/ | 2026-07-22 |
| 79 | Postal & Mail Management System | 06_Transportation_Logistics | postal_mail_management_system/ | 2026-07-22 |
| 80 | Vehicle Maintenance Management System | 06_Transportation_Logistics | vehicle_maintenance_management_system/ | 2026-07-22 |
| 81 | Cross-Docking Management System | 06_Transportation_Logistics | cross_docking_management_system/ | 2026-07-22 |
| 82 | Autonomous Vehicle Fleet System | 06_Transportation_Logistics | autonomous_vehicle_fleet_system/ | 2026-07-22 |
| 83 | Rail Freight Management System | 06_Transportation_Logistics | rail_freight_management_system/ | 2026-07-22 |
| 84 | Air Cargo Management System | 06_Transportation_Logistics | air_cargo_management_system/ | 2026-07-22 |
| 85 | Port & Terminal Operations System | 06_Transportation_Logistics | port_terminal_operations_system/ | 2026-07-22 |
| 86 | Vehicle Inspection Management System | 06_Transportation_Logistics | vehicle_inspection_management_system/ | 2026-07-22 |
| 87 | Ride-Pooling & Carpooling Platform | 06_Transportation_Logistics | ride_pooling_carpooling_platform/ | 2026-07-22 |
| 88 | Last-Mile Locker System | 06_Transportation_Logistics | last_mile_locker_system/ | 2026-07-22 |
| 89 | Intermodal Transport Management System | 06_Transportation_Logistics | intermodal_transport_management_system/ | 2026-07-22 |
| 90 | Dangerous Goods Transport System | 06_Transportation_Logistics | dangerous_goods_transport_system/ | 2026-07-22 |
| 91 | Transport Booking Aggregator | 06_Transportation_Logistics | transport_booking_aggregator/ | 2026-07-22 |
| 92 | Smart Parking Management System | 06_Transportation_Logistics | smart_parking_management_system/ | 2026-07-22 |
| 93 | Logistics Analytics Platform | 06_Transportation_Logistics | logistics_analytics_platform/ | 2026-07-22 |
| 94 | Delivery Partner App System | 06_Transportation_Logistics | delivery_partner_app_system/ | 2026-07-22 |
| 95 | Vehicle Leasing Management System | 06_Transportation_Logistics | vehicle_leasing_management_system/ | 2026-07-22 |
| 96 | Moving & Relocation Service System | 06_Transportation_Logistics | moving_relocation_service_system/ | 2026-07-22 |
| 97 | Cargo Insurance Management System | 06_Transportation_Logistics | cargo_insurance_management_system/ | 2026-07-22 |
| 98 | GPS Asset Tracking System | 06_Transportation_Logistics | gps_asset_tracking_system/ | 2026-07-22 |
| 99 | Logistics ERP System | 06_Transportation_Logistics | logistics_erp_system/ | 2026-07-22 |
| 100 | Sustainable Logistics Management System | 06_Transportation_Logistics | sustainable_logistics_management_system/ | 2026-07-22 |
| 101 | Urban Micro-Mobility System | 06_Transportation_Logistics | urban_micro_mobility_system/ | 2026-07-22 |
| 102 | International Freight Forwarding System | 06_Transportation_Logistics | international_freight_forwarding_system/ | 2026-07-22 |
| 103 | Shipyard Management System | 06_Transportation_Logistics | shipyard_management_system/ | 2026-07-22 |
| 104 | Real-time Visibility & Tracking Platform | 06_Transportation_Logistics | real_time_visibility_tracking_platform/ | 2026-07-22 |
| 105 | Hazardous Material Tracking System | 06_Transportation_Logistics | hazardous_material_tracking_system/ | 2026-07-22 |
| 106 | Truck Load Optimization System | 06_Transportation_Logistics | truck_load_optimization_system/ | 2026-07-22 |
| 107 | Returns & Exchange Logistics System | 06_Transportation_Logistics | returns_exchange_logistics_system/ | 2026-07-22 |
| 108 | Transport Cost Calculation System | 06_Transportation_Logistics | transport_cost_calculation_system/ | 2026-07-22 |
| 109 | Crowdsourced Delivery Platform | 06_Transportation_Logistics | crowdsourced_delivery_platform/ | 2026-07-22 |
| 110 | Traffic Incident Reporting System | 06_Transportation_Logistics | traffic_incident_reporting_system/ | 2026-07-22 |
| 111 | Multi-Modal Journey Planner | 06_Transportation_Logistics | multi_modal_journey_planner/ | 2026-07-22 |

*(Cap nhat bang nay moi khi them he thong moi)*

---

## Convention dat ten folder

- Dung `snake_case` (viet thuong, cach nhau bang `_`)
- Khong dung dau tieng Viet
- Dat ten theo **ten he thong**, khong theo ten de bai

| Dung | Sai |
|------|-----|
| `hospital_management_system` | `Hospital Management` |
| `online_banking_system` | `he thong ngan hang` |
| `hotel_booking_system` | `HotelBooking` |

---

## Lien he & dong gop

Neu format can chinh sua, cap nhat `AGENTS.md` va `PROMPT.md` -> AI se tu ap dung cho cac he thong tiep theo.
