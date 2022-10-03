* **A User created a new object: I need to mint a ID with ID System X**

```mermaid
sequenceDiagram
User->>Our System: Create Object
Our System->>System X: Mint ID Request
System X->>Our System: Return ID
Our System->>User: Show Object
```
Footer
