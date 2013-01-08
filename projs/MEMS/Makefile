PROJECT=$(shell basename $(shell pwd))

BINARY=$(PROJECT).bin
TARGET=$(PROJECT).hex
EXECUTABLE=$(PROJECT).elf

CC=arm-none-eabi-gcc
LD=arm-none-eabi-ld 
AR=arm-none-eabi-ar
AS=arm-none-eabi-as
CP=arm-none-eabi-objcopy
OD=arm-none-eabi-objdump

BIN=$(CP) -O ihex 

DEFINES =-DUSE_STDPERIPH_DRIVER
DEFINES+=-DSTM32F4XX
DEFINES+=-DHSE_VALUE=8000000

MCU=cortex-m4
MCFLAGS=-mcpu=$(MCU) -mthumb -mlittle-endian -mfpu=fpv4-sp-d16 -mfloat-abi=soft -mthumb-interwork -std=c99 -lm -lc

STM32_INCLUDES =-I./src/
STM32_INCLUDES+=-I../../lib/CMSIS/Include/
STM32_INCLUDES+=-I../../lib/CMSIS/ST/STM32F4xx/Include/
STM32_INCLUDES+=-I../../lib/STM32F4-Discovery/
STM32_INCLUDES+=-I../../lib/STM32F4xx_StdPeriph_Driver/inc/

OPTIMIZE       = -Os

LINKER_SCRIPT=./link/stm32_flash.ld

CFLAGS=$(MCFLAGS) $(OPTIMIZE) $(DEFINES) $(STM32_INCLUDES) -T $(LINKER_SCRIPT)
AFLAGS=$(MCFLAGS) 

# CMSIS Source Files
SRC =../../lib/CMSIS/ST/STM32F4xx/Source/system_stm32f4xx.c

# ST Standard Library Source Files
SRC+=../../lib/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_exti.c
SRC+=../../lib/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_gpio.c
SRC+=../../lib/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_rcc.c
SRC+=../../lib/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_spi.c
SRC+=../../lib/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_syscfg.c
SRC+=../../lib/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_tim.c
SRC+=../../lib/STM32F4xx_StdPeriph_Driver/src/misc.c

# STM32F4 Discovery
SRC+=../../lib/STM32F4-Discovery/stm32f4_discovery.c
SRC+=../../lib/STM32F4-Discovery/stm32f4_discovery_lis302dl.c

# User Source Files
SRC+=./src/main.c
SRC+=./src/stm32f4xx_it.c

STARTUP=../../lib/CMSIS/ST/STM32F4xx/Source/startup_stm32f4xx.s

OBJDIR=.
OBJ =$(SRC:%.c=$(OBJDIR)/%.o) 
OBJ+=Startup.o

all: $(BINARY)

$(BINARY): $(TARGET)
	$(CP) -I ihex $^ -O binary $@

$(TARGET): $(EXECUTABLE)
	$(CP) -O ihex $^ $@

$(EXECUTABLE): $(SRC) $(STARTUP)
	$(CC) $(CFLAGS) $^ -o $@

clean:
	rm -f $(EXECUTABLE) $(TARGET) $(BINARY)

install:
	st-flash write $(BINARY) 0x08000000

