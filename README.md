# TwinCAT XTS Framework

## Contents

1. [Background](#Background)
2. [Project Description](#Description)
3. [Project Explanation](#Project-Explanation)
4. [Running the Demo](#Running-the-Demo)
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

## Project Explanation

The repo is split into 3 projects:
1) the library
    - the library contains all the elements required to run an XTS, the loosly coupled elements allow you top arrange a project to you own designs.
2) unit testing project
    - unit testing is done with an internal unit test framework at this time
3) demo project for a simple closed XTS track.
    - the demo is a simple 8 mover, 3m closed loop of XTS, simple stations using timers to simulate operation are used to make it realistic.

## Running the Demo

The demo project is a very simple implemnentation of an XTS, the abstract XTS class is extended in the project, to add the abstract functionality of a home sequence.
This is then instanced in the machine class, which contains all the XTS elements, these are injected as required to allow the machine to run. There is a simple init sequence to register all elements as required and set the linkages up. Finally once initialised the system will cycle and respond to 3 bools, reset, start and stop. 
The steps to run:
1) actiavte the configuration
2) login to the PLC
3) wait for init to be true
4) toggle the reset (movers will home according to the logic in the homesequence that you can edit)
5) toggle the start (the movers will then begin stationing operations)

Station positions and timings can be changed easily whilst the system is running, although I recommend you stop the movers to change positions.

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









