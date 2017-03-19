# Build FreeRTOS

Various ways to build FreeRTOS + demo as a static library.

# ARM926EJ-S

Available in `FreeRTOS-ARM926EJ-S`.

<https://github.com/jkovacic/FreeRTOS-GCC-ARM926ejs>

CMake based.

## Setup

    $ unzip FreeRTOSv9.0.0.zip
    $ git clone https://github.com/jkovacic/FreeRTOS-GCC-ARM926ejs
    $ cmake .
    $ make

# Intel Galileo Board

Available in `FreeRTOS-IA32_flat`.

<http://www.freertos.org/RTOS_Intel_Quark_Galileo_GCC.html>

Automake based.

## Setup

    $ unzip FreeRTOSv9.0.0.zip
    $ ./autogen.sh
    $ make
