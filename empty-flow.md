Mermaid System Scenario
You are designing a system that needs to:

* A User created a new object: I need to mint a ID with ID System X
* A User updates the metadata on the Object: Update Sytem X if the change is something X is interested
* The system notifies curator when an object is ready for review
* A Curator needs to approve the object for it to show up publically in the system

```mermaid
sequenceDiagram
  %%{init: { 'theme': 'forest',
             'sequence': {'useMaxWidth':false, 
                          'mirrorActors':true,   
                          'diagramMarginX': 10
                          } 
            } 
  }%%
  title A very basic Diagram
  actor user as User
  participant oursys as Our System 
  participant sysx as System x
  actor curat as Curator
  rect rgb(255, 255, 240)
    note left of user: Create an Object
    user->>oursys: Create an Object
    oursys->>sysx: Mint and ID
    sysx->>oursys: return ID
    oursys->>oursys: store the id
    oursys->>user: Created object
  end
  rect rgb(240, 255, 255)
    note left of user: Review an Object
    loop Object approved?
      user->>oursys: Update Object
      alt Does System X care?
        oursys->>sysx: Update System X
      end
      oursys->>user: Object Updated
      user->>oursys: Ready for Review
      oursys->>curat: Object ready for review
      alt is ready to approve?
        curat->>oursys: Appove Object
        oursys->>oursys: Mark as public
        oursys->>user: You object was Approved!
      else
        oursys->>user: Please update the object
      end
    end
  end
```
