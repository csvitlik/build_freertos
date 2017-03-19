AC_INIT([FreeRTOS-IA32_flat], [9.0.0])
AM_INIT_AUTOMAKE([-Wall -Werror foreign subdir-objects])
AC_PROG_CC
AC_PROG_RANLIB
AM_PROG_AR
AM_PROG_AS
AC_CHECK_TOOL([OBJCOPY], [objcopy], [:])
AC_SUBST([RTOS_CPPFLAGS], ["-IFreeRTOSv9.0.0/FreeRTOS/Demo/Common/include \
-IFreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2 \
-IFreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2/Full_Demo \
-IFreeRTOSv9.0.0/FreeRTOS/Demo/IA32_flat_GCC_Galileo_Gen_2/Support_Files \
-IFreeRTOSv9.0.0/FreeRTOS/Source/include \
-IFreeRTOSv9.0.0/FreeRTOS/Source/portable/GCC/IA32_flat \
-ffreestanding -nostartfiles"])
AC_CONFIG_FILES([Makefile])
AC_OUTPUT
