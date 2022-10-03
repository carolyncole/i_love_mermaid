
* A User created a new object: I need to mint a ID with ID System X
* A User updates the metadata on the Object: Update Sytem X if the change is something X is interested

**We are updating the people to display as actors**

```mermaid
sequenceDiagram
actor u as User
participant os as Our System
participant x as System X
u->>os: Create Object
os->>x: Mint ID Request
x->>os: Return ID
os->>u: Show Object
u->>os: Update Metadata
alt System X Cares about the update
  os->>x: Send Updated Metadata
end
os->>u: Show Object
```
