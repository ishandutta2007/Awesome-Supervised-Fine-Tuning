# Enterprise Tool-Calling & API Function Injection

Enterprise Tool-Calling aligns base models to parse natural language queries and dynamically construct valid structured queries or API payloads.

## Concept
During SFT, the model is trained to recognize when a user query requires external data (e.g., fetching user details, executing SQL, or calling an API). The model learns to output structured JSON or tool-call blocks that match a pre-defined API schema.

```mermaid
sequenceDiagram
    participant User as User
    participant Model as SFT Model
    participant API as External API / SQL Database
    User->>Model: "Fetch sales reports for Q2 2026"
    Note over Model: SFT triggers JSON/schema generation
    Model->>API: call_api("fetch_sales_reports", {"quarter": "Q2", "year": 2026})
    API-->>Model: Return JSON data: { "total": "$2.3M", ... }
    Model->>User: "Here is your sales report summary..."
```

[← Back to README](../README.md)
