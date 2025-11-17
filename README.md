```mermaid
flowchart TD
A[Vehicle] --> B[API Gateway]
B --> C[Lambda (Ingest)]
C --> D[Kinesis Data Stream]
D --> E[Kinesis Consumer Lambda]
E --> F[TripState (DynamoDB)]
E --> G[Firehose]
G --> H[S3 (Raw Telemetry)]
E --> I[Geofence API (Amazon Location)]
E --> J[Alerts Engine\n(SNS + DynamoDB)]
E --> K[TripEnd Trigger]
K --> L[Step Function]
L --> M[TripSummary\n(DynamoDB + S3)]
N[Fleet Management API\n(NestJS Lambda)] --> O[Web & Mobile Apps\n(Cognito Auth + WebSocket)]
```
