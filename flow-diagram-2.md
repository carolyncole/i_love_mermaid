```mermaid
sequenceDiagram
actor User
participant Our System
actor Curator
participant System X
User->>Our System: Create Object
Our System->>System X: Mint ID Request
System X->>Our System: Return ID
Our System->>User: Show Object
```
