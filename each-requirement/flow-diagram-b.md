* A User created a new object: I need to mint a ID with ID System X
* **A User updates the metadata on the Object: Update Sytem X if the change is something X is interested**

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
