AOC = arm-none-eabi-objcopy
TARGET = thumbv7m-none-eabi

KERNEL_BIN = kernel.bin
KERNEL_ELF = target/$(TARGET)/debug
MAIN_FILE = src/main.rs

AFLAGS = -O binary
FFLAGS = -v -g 0x8000000

USB_PORT = /dev/ttyUSB0

run:
	qemu-system-arm --cpu cortex-m3 --machine lm3s6965evb --nographic --semihosting-config enable=on,target=native --kernel target/thumbv7m-none-eabi/debug/a01-blink-onboard-led

build:
	cargo build

compile:
	$(AOC) $(AFLAGS) $(KERNEL_ELF)/a01-blink-onboard-led $(KERNEL_BIN)

flash: $(KERNEL_BIN)
	stm32flash -w $< $(FFLAGS) $(USB_PORT)

clean:
	cargo clean
	rm $(KERNEL_BIN)

all: $(KERNEL_BIN)

$(KERNEL_BIN): $(KERNEL_ELF) $(MAIN_FILE)
	$(AOC) $(AFLAGS) $(KERNEL_ELF)/a01-blink-onboard-led $(KERNEL_BIN)

$(KERNEL_ELF): $(MAIN_FILE)
	cargo build