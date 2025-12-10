# Track Class

## Class Diagram

```mermaid

classDiagram
    class I_XtsTrack{
        <<interface>>
        +RemoveFromDetection()
        +SetForDetection()
        +NumberOfPartsInTrack
        +TrackLength
    }

    class XtsTrack{
        +RemoveFromDetection()
        +SetForDetection()
        +NumberOfPartsInTrack
        +MyXtsIoEnvVarInterface
        +TrackLength
    }

    class CyclicBase{
        +Cycle()
    }

    class I_Initialisable{
        +Initialise()
        +IsInitialised()
    }

    I_XtsTrack <|-- XtsTrack : implements
    I_Initialisable <|-- XtsTrack : implements
    XtsTrack --|> CyclicBase
```