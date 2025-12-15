# Part Class

## Overview

The Part class represents a group of motor modules, it is the governor for them, bringing together diagnostic and control data for all modules included in its set up. This class represents that function, allowing resetting and status checks on the modules within.

## Class Diagram

```mermaid

classDiagram
    class I_XtsPart{
        <<interface>>
        +SetInSim()
        +ResetPart()
        +ResetNCT()
        +Is24VBusOK()
        +Is48VBusOK()
        +HasError()
        +GetCurrentError()
        +SetPartOriginTransform()
    }

    class XtsPart{
        +SetInSim()
        +ResetPart()
        +ResetNCT()
        +Is24VBusOK()
        +Is48VBusOK()
        +HasError()
        +GetCurrentError()
        +SetPartOriginTransform()
        +MyXtsIoEnvVarInterface
    }

    class CyclicBase{
        +Cycle()
    }

    class I_Initialisable{
        +Initialise()
        +IsInitialised()
    }

    I_Initialisable <|-- XtsPart : implements
    XtsPart --|> CyclicBase
    I_XtsPart <|-- XtsPart : implements
```

## Implementation

Inside the Part class is the following:
```
_MyInterface : Tc3_XTS_Utility.I_TcIoXtsXpuPart;
```
This interface is populated in the initialise phase of the [hardware](Hardware%20Class.md). It is via this function that the Part class can perform tasks listed below. 

### Cycle

### Initialise

## Interface

### SetInSim()

This method is invoked by the [Hardware Class](./Hardware%20Class.md) during its initialisation, its simply sets the part into simulation mode, which in turns calls the internal modules.

### ResetPart()

This method thriggers the part reset function, this allows the clearing of module faults and part faults without needing the movers, not typically needed as the movers forward reset commands.

### ResetNCT()

Triggers a reset of the NCT element of a module.

### Is24VBusOK()

This method returns a TRUE if all modules in part report a good 24vdc 

### Is48VBusOK()

This method returns a TRUE if all modules in part report a good 48Vdc.

### HasError()

This method returns a TRUE if the module goes into Fault, FaultReactionActive or DCLinkVoltage not ready.

### GetCurrentError()

This method returns the current error value from the part.

### SetPartOriginTransform()

This method allows you to set x and y coordinates for the part as displayed in TcHMI, this is useful for TMS applications representing modules on switches.