# Hardware Class

The module class is the basic element of any XTS system, this class is its software representation. The module uses its XtsIoEnv interfaceto pull data about each module direct from the XPU. The main function of the class is to monitor the module for issues in its electrical system. Higher level errors are pushed into the movers, part and tracks.

## Class Diagram

```mermaid

classDiagram
    class I_Hardware{
        +GetConfiguredDetectionMoverNumber()
        +GetMoverDetectionState()
        +GetNumberMoversDetected()
        +GetTrackInterfaceByNumber()
        +GetTrackInterfaceByOTCID()
        +RemoveATrackFromDetection()
        +ResetAllParts()
        +ResetAPart()
        +SetAPartOriginTransform()
        +SetATrackForDetection()
        +SetMoverNumberForDetection()
        +TriggerMoverDetection()
        +TriggerMoverIDDetection()
        +TriggerMoverRedtection()
        +ExpectedNumberOfParts
        +ExpectedNumberOfTracks
        +MyXts
        +AreAllMoverPositionsValid()
        +AreAnyPartsInError()
        +AreExpectedMoversFound()
        +DetectedNumberOfParts
        +DetectedNumberOfTracks
        +GetPartErrorCode()
        +HasValidXPUReference()
        +IsHardware24VdcOK()
        +IsHardware48VdcOK()
        +IsIDDetectionStandard()
        +IsXtsInSim()
    }

    class Hardware{
        +GetConfiguredDetectionMoverNumber()
        +GetMoverDetectionState()
        +GetNumberMoversDetected()
        +GetTrackInterfaceByNumber()
        +GetTrackInterfaceByOTCID()
        +RemoveATrackFromDetection()
        +ResetAllParts()
        +ResetAPart()
        +SetAPartOriginTransform()
        +SetATrackForDetection()
        +SetMoverNumberForDetection()
        +TriggerMoverDetection()
        +TriggerMoverIDDetection()
        +TriggerMoverRedtection()
        +ExpectedNumberOfParts
        +ExpectedNumberOfTracks
        +MyXts
        +AreAllMoverPositionsValid()
        +AreAnyPartsInError()
        +AreExpectedMoversFound()
        +DetectedNumberOfParts
        +DetectedNumberOfTracks
        +GetPartErrorCode()
        +HasValidXPUReference()
        +IsHardware24VdcOK()
        +IsHardware48VdcOK()
        +IsIDDetectionStandard()
        +IsInitialised()
        +IsXtsInSim()
        +Cycle()
        +Initialise()
        +RegisterWithParent
    }

    class CyclicBase{
        +Cycle()
    }

    class I_Initialisable{
        +Initialise()
        +IsInitialised()
    }

    class I_Object{
        +RegisterWithParent()
    }

    I_Initialisable <|-- Hardware : implements
    I_Object <|-- Hardware : implements
    I_Hardware <|-- Hardware : implements
    Hardware --|> CyclicBase
```

## Interface
### GetConfiguredDetectionMoverNumber()
### GetMoverDetectionState()
### GetNumberMoversDetected()
### GetTrackInterfaceByNumber()
### GetTrackInterfaceByOTCID()
### RemoveATrackFromDetection()
### ResetAllParts()
### ResetAPart()
### SetAPartOriginTransform()
### SetATrackForDetection()
### SetMoverNumberForDetection()
### TriggerMoverDetection()
### TriggerMoverIDDetection()
### TriggerMoverRedtection()
### ExpectedNumberOfParts
### ExpectedNumberOfTracks
### MyXts
### AreAllMoverPositionsValid()
### AreAnyPartsInError()
### AreExpectedMoversFound()
### DetectedNumberOfParts
### DetectedNumberOfTracks
### GetPartErrorCode()
### HasValidXPUReference()
### IsHardware24VdcOK()
### IsHardware48VdcOK()
### IsIDDetectionStandard()
### IsXtsInSim()