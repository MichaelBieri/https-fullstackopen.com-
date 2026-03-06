
sequenceDiagram
    participant U as User
    participant B as Browser
    participant CDN as CDN / Web Server
    participant API as Backend API
    participant DB as Database

    U->>B: Open app URL
    B->>CDN: Request HTML, CSS, JS
    CDN-->>B: Return SPA assets

    B->>B: Run JavaScript (start SPA)

    B->>API: Request data
    API->>DB: Query data
    DB-->>API: Results
    API-->>B: JSON response
