AOC = arm-none-eabi-objcopy
KERNEL_BIN = kernel.bin
KERNEL_ELF = target/$(TARGET)/debug
MAIN_FILE = src/main.rs

AFLAGS = -O binary
TARGET = thumbv7m-none-eabi
FFLAGS = -v -g 0x8000000
USB_PORT = /dev/ttyUSB0

run:
	qemu-system-arm --cpu cortex-m3 --machine lm3s6965evb --nographic --semihosting-config enable=on,target=native --kernel target/thumbv7m-none-eabi/debug/a01-blink-onboard-led

build:
	cargo build

compile:
	$(AOC) $(AFLAGS) $(KERNEL_ELF)/a01-blink-onboard-led $(KERNEL_BIN)
