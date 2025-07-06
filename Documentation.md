# TwinCAT XTS Framework Documentation

## Contents

1. [Framework Structure](#framework-structure)
2. [XTS Class](#xts-class)
3. [Mover Class](#mover-class)
4. [Mover Sequence Class](#mover-sequence-class)
5. [Station Class](#station-class)
6. [XTS Part Class](#xts-part-class)
7. [XTS Track Class](#xts-track-class)

## Framework Structure

The framework contains a number of elements that allow the user to implement an XTS system. It contains several other elements that implement core features of its operation, event messaging and PackML state machine functionality. These features will eventually need to be removed leaving the core XTS elements in this library. As a result refactoring going forward will be made to pull references to these as libraries inverting the dependanices. 

## XTS Class

The XTS class is the handler class for the hardware and collision group elements of the XTS. The XTS Class holds the Xts hardware class, which is responsible for managing the hardware elements of the XTS via the Xts Environment Variable. These include the Track class and the Part class, which are able to provide status information and diagnostics information of all the elements of the system. These class combine to provide all control and informaiton on the track hardware.

## Mover Class

The movers are provided by a Mover Class, this class takes a sequence class that controls its movement. The Mover Class contains all the motion operations of the system, the XTS class is repsonsible for all detection features assigning to collision avoidance groups. The Movers handle the motion functions and error handling. 

## Mover Sequence Class

The movers only hold the functionality of the mover itself and the XTS calss the track. There are options for how you control the motion in an XTS system, Station centric and Mover centric. In the station centric model the XTS system is given a set of station, these stations control the mover, as the mover arrives it joins a virtual queue on the station, when the station is complete the mover moves on. 

In a mover centric model the motion is controlled by a mover sequence, you create a motion profile and give it to each mover, the mover then holds the location information and required destination. You can provide station class as an array, a simple indexing sequence would then simply iterate through the array. 

## Station Class

A lot of XTS operations end up with stations, locations on the track where a mover needs to take the load for product loading, work and unloading. Virtually we think of these as stations, they arent really any physical quality so most XTS applications invent them to allow operation. This framework can utilise Stations assuming you implement a station sequencing profile for the movers. The Index Sequence class is an example of this.

The advantage here is the user of the framework only needs to code the station operation and use the inbuilt fields of the class, Done, Ready, Busy etc. The sample Index Sequence responds to stations being done, the mover will move on at that point. 

## Process Class

## Queue Class

## Trigger Point Class

## XTS Part Class

The XTS part represents the 'parts' of the XTS track, XTS modules are grouped into parts. The XTS part class holds the detail of the individual part as defined in the XtsIoDrv, this is not hardware dependant. The Part class creates a set of objects of XTS Modules class, it is responsible for checking the health and status of all modules within its defined part. IT also allows the reset of the Part or NCT part.

The Part Class will check the modules for the correct voltage levels across the 24 and 48v networks, it also has the ability to export the diag history and other useful information.

## XTS Track Class

The track class represents the summation of the individual parts of the XTS track, in stnadard closed tracks there will likely be only a single part and track. However in TMS track systems there will be multiple parts and the tracks are of significant importance as these are the references for the modulo motion of the movers.

## XTS Module Class

The module class is the representation of the physical motor modules, its the access point for the information at the module level of the XTS. You can get the CoE data, NCT information, voltage, current information etc. Modules are created by the Part Class and are contained wihtin them as arrays of modules.

## XTS Hardware Class

The XTS Hardware class is a logical grouping of the Tracks, Parts and Modules that encapsulate the functionality of all the hardware, allowing you to enable and disabled tracks for detection, trigger mover searches, mover id detection. The hardware is injected into the XTS class at the initialisaiton stage of the setup, it is then cyclically called where ever you choose to do this, this cyclic call will update all the internal components.

## CA Group Class
