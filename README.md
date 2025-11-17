flowchart TD

    %% Vehicle → API Gateway → Lambda (Ingest)
    A[🚗 Vehicle] --> B[API Gateway]
    B --> C[Lambda: Ingest Telemetry]

    %% Kinesis Stream
    C --> D[(Kinesis Data Stream)]

    %% Kinesis Consumer → DynamoDB (Trip State)
    D --> E[Lambda: Kinesis Consumer]
    E --> F[(DynamoDB: TripState)]

    %% Branches from Consumer Lambda
    E --> G[Firehose → S3: Raw Telemetry]
    E --> H[Geofence API\n(Amazon Location]()
