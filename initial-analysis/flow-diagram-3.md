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
User->>Our System: Edit Object
alt System X cares about information in update
  Our System->>System X: Send Update
end
Our System->>User: Show Object
```
