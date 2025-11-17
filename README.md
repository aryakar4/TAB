```mermaid
flowchart TD

    %% Vehicle to Backend Ingestion
    A[Vehicle] --> B[API Gateway]
    B --> C[Lambda (Ingest)]
    C --> D[Kinesis Data Stream]

    %% Kinesis Consumers
    D --> E[Kinesis Consumer Lambda]

    %% TripState
    E --> F[TripState (DynamoDB)]

    %% Parallel downstream paths
    E --> G[Firehose]
    G --> H[S3 (Raw Telemetry)]

    E --> I[Geofence API (Amazon Location)]

    E --> J[Alerts Engine\n(SNS + DynamoDB)]

    %% TripEnd path
    E --> K[TripEnd Trigger]
    K --> L[Step Function]
    L --> M[TripSummary\n(DynamoDB + S3)]

    %% Fleet Management API
    N[Fleet Management API\n(NestJS Lambda)] --> O[Web & Mobile Apps\n(Cognito Auth + WebSocket)]
```
