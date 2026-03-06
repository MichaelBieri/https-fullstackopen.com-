```mermaid
sequenceDiagram
    participant U as User
    participant B as Browser
    participant CDN as CDN / Web Server
    participant API as Backend API
    participant DB as Database

    U->>B: Open app URL
    B->>CDN: GET https://studies.cs.helsinki.fi/exampleapp/spa with Request HTML, CSS, JS
    CDN-->>B: HTML with return SPA assets

    B->>B: Run JavaScript (start SPA)

    B->>API: Request data
    API->>DB: Query data
    DB-->>API: Results
    API-->>B: JSON response
