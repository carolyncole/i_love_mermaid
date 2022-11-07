Mermaid System Scenario
You are designing a system that needs to:

* A User created a new object: I need to mint a ID with ID System X
* A User updates the metadata on the Object: Update Sytem X if the change is something X is interested
* The system notifies curator when an object is ready for review
* A Curator needs to approve the object for it to show up publically in the system
* A User can revoke an object at any time: Need to revoke System X ID

```mermaid
sequenceDiagram
%%{init: { 'theme': 'forest',
             'sequence': {'useMaxWidth':false, 
                          'mirrorActors':true,   
                          'diagramMarginX': 10
                          } 
            } 
  }%%
actor user as User
participant oursys as Our Syetem
participant sysx as System X
actor curat as Curator
rect rgb(240, 255, 255)
  note left of user: Object Create
  user->>oursys: Create an Object
  oursys->>sysx: Mint an ID
  sysx->>oursys: return ID
  oursys->>oursys: Store ID
  oursys->>user: Object was created
end
rect rgb(255, 240, 255)
  note left of user: Object Approval
  loop Until Object is Approved
    user->>oursys: Update Metadata
    alt Is System X is interested in the update?
    oursys->>sysx: Update Metadata
    sysx->>oursys: Updated metdata
    end
    oursys->>user: Object was update
    user->>oursys: Object is Complete
    oursys->>curat: Object Ready for review
    alt Is Object ready to approve?
      curat->>oursys: Approve Object
      oursys->>oursys: Mark Object as Approved and Make it Public
      oursys->>curat: Object is public
    else
      curat->>oursys: Issues with o=Obeject
      oursys->>user: Notfiy user of issues
    end
  end
end
```

## Cheet Sheet

Here is a cheet sheet of useful items for a mermaid flow diagram.  Full documentation can be found at [Mermaid.js](https://mermaid-js.github.io/mermaid/#/sequenceDiagram)

### participants
  participant [name]: [display name] **OR** actor [name]: [display name] (an actor diplays a stick figure and a participat displays a box

  
  ```mermaid
  sequenceDiagram
  %%{init: { 'sequence': {'mirrorActors':false} } }%%
    actor you as You
    participant store as Pet store
  ```
 
### Alternate
 alt [choice]
    ...
 else [another choice]
    ...
 else [yet another choice]
    ...
 end

  ```mermaid
  sequenceDiagram
    actor you as You
    participant store as Pet store
    alt you love cats?
      you->>store: Buy a cat
    else you love fish
      you->>store: Buy a fish
    else you do not want a pet
      you->>you: stay home
    end  
  ```

### Loop
 loop [until when]
   ...
 end

  ```mermaid
  sequenceDiagram
      loop until you are full
        spoon->>mouth: Insert food on spoon
      end
  ```

### Theming
  Theming Mermaid can be done in a variety of ways.  See full documentation at [Mermaid.js](https://mermaid-js.github.io/mermaid/#/theming)
1. Rectangles
   * rect rgb(240, 255, 255)
   * rect rgb(255, 240, 255)
   * rect rgb(255, 255, 240)
1. Notes
   * note [left|right|over] of [the particiapnt]: <note>
  ```mermaid
  sequenceDiagram
    participant spoon AS #129348;
    participant mouth as #128068;
    loop until you are full
     note over spoon,mouth: Open wide
      spoon->>mouth: Insert food on spoon
    end
  ```

1. Overall 
  Overall themes can be applied like a color theme: forest, dark, neutral
  ```mermaid
  %%{init: { 'theme': 'dark',
             'sequence': {'useMaxWidth':false, 
                          'mirrorActors':false,   
                          'diagramMarginX': 10
                          } 
            } 
  }%%
  sequenceDiagram
    actor you as You
    participant store as Pet store
    alt you love cats?
      you->>store: Buy a cat
    else you love fish
      you->>store: Buy a fish
    else you do not want a pet
      you->>you: stay home
    end  
  ```

