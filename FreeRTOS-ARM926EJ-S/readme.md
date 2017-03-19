# ARM926EJ-S + Qemu

    $ make DEBUG=1
    $ qemu-system-arm -M versatilepb -m 128M -nographic -s -S -kernel FreeRTOS-ARM926EJ-S.bin
    # At another terminal:
    $ arm-none-eabi-gdb
    (gdb) target remote localhost:1234
    (gdb) break vectors_start
    (gdb) continue
