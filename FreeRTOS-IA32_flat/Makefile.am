AUTOMAKE_OPTIONS = subdir-objects

AM_CPPFLAGS = -I$(top_srcdir) @RTOS_CPPFLAGS@

noinst_LIBRARIES      = libfreertos.a
libfreertos_a_SOURCES = \
	FreeRTOSv9.0.0/FreeRTOS/Source/croutine.c \
	FreeRTOSv9.0.0/FreeRTOS/Source/event_groups.c \
	FreeRTOSv9.0.0/FreeRTOS/Source/list.c \
	FreeRTOSv9.0.0/FreeRTOS/Source/queue.c \
	FreeRTOSv9.0.0/FreeRTOS/Source/tasks.c \
	FreeRTOSv9.0.0/FreeRTOS/Source/timers.c

noinst_PROGRAMS       = IA32_flat.elf
IA32_flat_elf_SOURCES = \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Full/BlockQ.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Full/death.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Full/dynamic.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Full/events.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Full/flop.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Full/integer.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Full/PollQ.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Full/print.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Full/semtest.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Minimal/AbortDelay.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Minimal/blocktim.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Minimal/countsem.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Minimal/EventGroupsDemo.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Minimal/GenQTest.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Minimal/IntQueue.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Minimal/IntSemTest.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Minimal/QPeek.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Minimal/QueueOverwrite.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Minimal/QueueSet.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Minimal/QueueSetPolling.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Minimal/recmutex.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Minimal/StaticAllocation.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Minimal/TaskNotify.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/Common/Minimal/TimerDemo.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2/Blinky_Demo/main_blinky.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2/Full_Demo/IntQueueTimer.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2/Full_Demo/IntQueueTimer.h \
	FreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2/Full_Demo/main_full.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2/Full_Demo/RegTest.S \
	FreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2/main.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2/Support_Files/freestanding_functions.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2/Support_Files/galileo-support.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2/Support_Files/GPIO_I2C.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2/Support_Files/HPET.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2/Support_Files/printf-stdarg.c \
	FreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2/Support_Files/startup.S \
	FreeRTOSv9.0.0/FreeRTOS/Source/portable/GCC/IA32_flat/portASM.S \
	FreeRTOSv9.0.0/FreeRTOS/Source/portable/GCC/IA32_flat/port.c \
	FreeRTOSv9.0.0/FreeRTOS/Source/portable/MemMang/heap_4.c
IA32_flat_elf_LDADD   = libfreertos.a
IA32_flat_elf_LDFLAGS = @RTOS_CPPFLAGS@ -static -T FreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2/elf_ia32_efi.lds

noinst_SCRIPTS        = IA32_flat.bin
IA32_flat.bin: IA32_flat.elf
	$(OBJCOPY) -O binary $< $@
