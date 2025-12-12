# Track Class

The Track class represents a group of parts, it is the governor for them, bringing together diagnostic and control data for all Parts included in its set up. This class represents that function, allowing resetting and status checks on the parts within.


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

## Interface

### RemoveFromDetection()

Returns a TRUE if the track successfully calls the SetIsIncludedInDetection(FALSE) command

### SetForDetection()

Returns a TRUE if the track successfully calls the SetIsIncludedInDetection(TRUE) command

### NumberOfPartsInTrack

Returns the number of detected parts in track

### TrackLength

Returns the configured length of the track