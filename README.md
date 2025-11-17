```mermaid
usecaseDiagram
    actor Vehicle as V
    actor FleetManager as FM
    actor Driver as D
    actor App as APP

    rectangle "Vehicle Telemetry Platform" {
        usecase "Send Telemetry" as UC1
        usecase "Ingest Telemetry" as UC2
        usecase "Process Stream" as UC3
        usecase "Store Raw Telemetry" as UC4
        usecase "Perform Geofence Check" as UC5
        usecase "Trigger Alerts" as UC6
        usecase "Compute Trip Summary" as UC7
        usecase "Manage Fleet Data" as UC8
        usecase "View Dashboard" as UC9
        usecase "Receive Real-Time Updates" as UC10
    }

    V --> UC1
    UC1 --> UC2
    UC2 --> UC3
    UC3 --> UC4
    UC3 --> UC5
    UC3 --> UC6
    UC3 --> UC7

    FM --> UC8
    APP --> UC9
    APP --> UC10
