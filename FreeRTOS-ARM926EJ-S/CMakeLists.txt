##################################################################################################
cmake_minimum_required (VERSION 2.8)

project (FreeRTOS-ARM926EJ-S C ASM)

set (FreeRTOS-ARM926EJ-S_VERSION_MAJOR 9)
set (FreeRTOS-ARM926EJ-S_VERSION_MINOR 0)
set (FreeRTOS-ARM926EJ-S_VERSION_PATCH 0)

set (CMAKE_SYSTEM_NAME generic)

set (CMAKE_AR arm-none-eabi-gcc-ar)
set (CMAKE_ASM_COMPILER arm-none-eabi-as)
set (CMAKE_C_COMPILER arm-none-eabi-gcc)
set (CMAKE_OBJCOPY arm-none-eabi-objcopy)
set (CMAKE_RANLIB arm-none-eabi-gcc-ranlib)

set (CMAKE_C_FLAGS
    "--specs=nano.specs --specs=rdimon.specs \
    -flto -Os -fno-common -ffunction-sections -fdata-sections \
    -Wl,-flto,--relax,--gc-sections,-Map=FreeRTOS-GCC-ARM926ejs.map \
    -W -Wall -Wextra -pedantic -ffreestanding -nostartfiles")
set (CMAKE_ASM_FLAGS "${CFLAGS}")
# Surely this is incorrect:
set (CMAKE_SHARED_LIBRARY_LINK_C_FLAGS "-static -T FreeRTOS-GCC-ARM926ejs/Demo/qemu.ld")

##################################################################################################
include_directories ("${PROJECT_SOURCE_DIR}/FreeRTOSv9.0.0/FreeRTOS/Demo/Common/include")
include_directories ("${PROJECT_SOURCE_DIR}/FreeRTOSv9.0.0/FreeRTOS/Source/include")
include_directories ("${PROJECT_SOURCE_DIR}/FreeRTOS-GCC-ARM926ejs/Demo")
include_directories ("${PROJECT_SOURCE_DIR}/FreeRTOS-GCC-ARM926ejs/drivers/include")
include_directories ("${PROJECT_SOURCE_DIR}/FreeRTOS-GCC-ARM926ejs/FreeRTOS/Source/portable/GCC/ARM926EJ-S")

##################################################################################################
add_library (freertos STATIC
    FreeRTOSv9.0.0/FreeRTOS/Source/croutine.c
    FreeRTOSv9.0.0/FreeRTOS/Source/event_groups.c
    FreeRTOSv9.0.0/FreeRTOS/Source/list.c
    FreeRTOSv9.0.0/FreeRTOS/Source/portable/MemMang/heap_4.c
    FreeRTOSv9.0.0/FreeRTOS/Source/queue.c
    FreeRTOSv9.0.0/FreeRTOS/Source/tasks.c
    FreeRTOSv9.0.0/FreeRTOS/Source/timers.c
)
set (EXTRA_LIBS ${EXTRA_LIBS} freertos)

##################################################################################################
add_library (portISR STATIC
    FreeRTOS-GCC-ARM926ejs/FreeRTOS/Source/portable/GCC/ARM926EJ-S/portISR.c
)
set (EXTRA_LIBS ${EXTRA_LIBS} portISR)
target_compile_options (portISR PRIVATE -fno-lto)

##################################################################################################
add_executable (FreeRTOS-ARM926EJ-S
    FreeRTOS-GCC-ARM926ejs/Demo/init.c
    FreeRTOS-GCC-ARM926ejs/Demo/main.c
    FreeRTOS-GCC-ARM926ejs/Demo/nostdlib.c
    FreeRTOS-GCC-ARM926ejs/Demo/print.c
    FreeRTOS-GCC-ARM926ejs/Demo/receive.c
    FreeRTOS-GCC-ARM926ejs/Demo/startup.s
    FreeRTOS-GCC-ARM926ejs/drivers/interrupt.c
    FreeRTOS-GCC-ARM926ejs/drivers/timer.c
    FreeRTOS-GCC-ARM926ejs/drivers/uart.c
    FreeRTOS-GCC-ARM926ejs/FreeRTOS/Source/portable/GCC/ARM926EJ-S/port.c
)
target_link_libraries (FreeRTOS-ARM926EJ-S ${EXTRA_LIBS})

##################################################################################################
add_custom_command (OUTPUT FreeRTOS-ARM926EJ-S.tmp
                    COMMAND ${CMAKE_OBJCOPY} -O binary FreeRTOS-ARM926EJ-S FreeRTOS-ARM926EJ-S.tmp
                    COMMAND ${CMAKE_COMMAND} -E copy FreeRTOS-ARM926EJ-S.tmp FreeRTOS-ARM926EJ-S.bin
                    DEPENDS FreeRTOS-ARM926EJ-S)
add_custom_target(FreeRTOS-ARM926EJ-S.bin ALL DEPENDS FreeRTOS-ARM926EJ-S.tmp)
