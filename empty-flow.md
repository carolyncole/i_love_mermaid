Mermaid System Scenario
You are designing a system that needs to:

* A User created a new object: I need to mint a ID with ID System X
* A User updates the metadata on the Object: Update Sytem X if the change is something X is interested
* The system notifies curator when an object is ready for review
* A Curator needs to approve the object for it to show up publically in the system
* A User can revoke an object at any time: Need to revoke System X ID

```mermaid
sequenceDiagram
actor user as User
participant sys As Our System
participant x As System x
participant slack As Slack
actor curator as Curator
user->>sys: Create Object
sys->>x: Request ID
x->>sys: ID response
sys->>user: Show Object
user->>sys: Update Metadata
alt System X cares about update
  sys->>x: update Request
  x->>sys: update status
end
sys->>user: Show Object
user->>sys: Mark as Ready for Review
sys->>slack: Notify Curator
curator-->>slack: Notices Notification
alt Object Ready to be approved?
  curator->>sys: Approve Object
else
  curator->>syste: Reject Object
end

```
