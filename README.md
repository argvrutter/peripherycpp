# peripherycpp

## Description

Peripherycpp is a C++ wrapper for vsergeev's [c-periphery](https://github.com/vsergeev/c-periphery)
This project was initially developed in order to integrate [c-periphery](https://github.com/vsergeev/c-periphery) with UTK IEEE robotic's Robotics Integrated Platform (RIP).

## Usage and Installation
This project uses a cmake build structure. To build the project, type `cmake .` in the peripherycpp directory, followed by `make`. There is an additional cmake flag, `-DENABLE_DIAG`, that when set to on, builds the diag directory.

## Diag
This directory, if enabled, will create executables that will attempt to communicate with another device. This directory serves as a sort of scratch directory for basic integration testing. Nothing in this directory is needed for the library to function.

## Credits
Credit goes to the initial author of c-periphery. Furthermore, this wrapper was written with help from Ian Lumsden, Cameron Adkins, and Parker Mitchell.
