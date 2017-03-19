# FreeRTOS Static Library

Automake project for building FreeRTOS v9.0.0 as a static library,
and [Intel® Galileo Board](http://www.freertos.org/RTOS_Intel_Quark_Galileo_GCC.html) demo.

# Setup

You'll need a 32 bit C compiler if you're on a 64 bit system:

    $ sudo apt-get install libc6-dev-i386

The FreeRTOS v9.0.0 sources should be in this directory:

    $ unzip FreeRTOSv9.0.0.zip

You'll need to build in 32 bit mode:

    $ CFLAGS=-m32 ./autogen.sh

Good to go!

    $ make
