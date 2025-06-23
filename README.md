# TwinCAT XTS Framework

## Contents

1. [Background](#Background)
2. [Project Description](#Description)
3. [System Design](#System-Design)
4. [Tests](#Tests)
5. [Support](#Support)
6. [Requirements](#Requirements)
7. [Documents](#Document-List)

## Background

This project is an attempt to use good programming practice to create a standard project to run a Beckhoff XTS unit, there is currently not a standard implementation for XTS so developers are able to design and implement their own system, however this leads to a lot of duplication of effort. Hopefully this will remove some of that process, even if only providing a basis for others to copy. Also its a good bit of fun :-)

## Description

The library is created solely to implement XTS functionality, other functions have been slowly pulled out and puished into their own repos.
This change means that you are not forced to use the XTS library with any of my structural systems. However you are required to instance the components
and run them via a cycle call to a cyclic method. All functionality are then implemented through method calls.

## System Design

The repo is split into 3 projects, the library, unit testing project and a demo project for s simple system.
The library project contains all functionality, it is referenced in the test project and actually installed and included in the demo one.
The library is brokem into 3 elements, Mover, Station and XTS.

1) The XTS elements deal with all things system, this includes communication to the XTS driver (XPU), the tracks, parts and mover commands avaialable there.
This allows functionality like resetting parts, activating tracks for movers, selecting tracks for detection and many other functions. It contains a hardware object which handles all the functions associated with the actual motor modules of the XTS, operations include monitoring voltage, errors and more.

2) The Mover element deals with all things mover, it recieves its interface to the XTS driver mover elements from the XTS class. As such it contains a full command suite for everything a mover can do. This includes activating onto a track, moving, resetting, detection, triggering leave and arrive and more. 

3) Station and Sequence, these 2 units combine to achieve a common application fiunction of XTS. the majority of implementations of the XTS are indexing devices, movers go from station to station with product and wait for a process to occur. As such the library includes a basic implementation for a station, the intention is that this be used in projects by extending this class and adding your own functionality to the cyclic method. If this is done then the index sequnece can be used. This is essentially prewritten statemachine for an XTS mover, pass your station array and mover to the index sequence, and on a run signal it will simply step the mover through each station, stopping at each and waiting for the station to report done.

## Tests

Tests will be performed using a testing framework. Being Honest testing was not done at the start, but at least Unit Tests will be rolled out to the older components. Refactoring components will allow TDD to be used on some elements. To keep it clean any additions must now have a test.

## Support

code was developed/modified by:

1. Chris Knight

## Requirements: 

TwinCAT 3 4024.7   
XTS Extension TF5850 3.21.703.0  
Advanced Motion TF5410 3.1.10.44

## Document List

Documentation for the repo starts **[here](./Documentation.md)**









