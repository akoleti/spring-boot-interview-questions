
graph TD
    A[Client Request] --> B{Cache Hit?}
    B -->|Yes| C[Return Cached Data]
    B -->|No| D[Load from Database]
    D --> E[Process Data]
    E --> F[Cache Result]
    F --> G[Return Response]
    C --> G
    H[Cache Eviction Policy] --> I{Eviction Trigger?}
    I -->|Time| J[Time-based Eviction]
    I -->|Size| K[Size-based Eviction]
    I -->|Manual| L[Manual Eviction]
