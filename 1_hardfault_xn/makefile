CROSS-COMPILER = arm-none-eabi-

all: hardfault.bin

hardfault.bin: blink.c startup.c vector_table.s
	$(CROSS-COMPILER)gcc -std=c11 -Wall -mcpu=cortex-m4 -mthumb -nostartfiles -T stm32f4.ld blink.c startup.c vector_table.s -o hardfault.elf
	$(CROSS-COMPILER)objcopy -O binary hardfault.elf hardfault.bin
	$(CROSS-COMPILER)objdump -D -h  hardfault.elf
    

flash:
	st-flash --reset write hardfault.bin 0x8000000

clean:
	rm -f *.o *.elf *.bin
