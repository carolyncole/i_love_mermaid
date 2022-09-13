```mermaid
sequenceDiagram
User->>Our System: Create Object
Our System->>System X: Mint ID Request
System X->>Our System: Return ID
Our System->>User: Show Object
User->>Our System: Update Metadata
alt System X Cares about the update
  Our System->>System X: Send Updated Metadata
end
Our System->>User: Show Object

```
