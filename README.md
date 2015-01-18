# nucleo
NUCLEO_F030R8 mbed Example

## Make
Makefile is based on the mbed_gcc_makefile (https://github.com/0xc0170/mbed_gcc_makefile).

## mbed
First mbed library has to be bult like this:
```bash
drasko@Lenin:~/mbed/workspace_tools$ python build.py -m NUCLEO_F030R8 -t GCC_ARM
```

## ARM GCC
ARM GCC for Cortex-M can be found here: https://launchpad.net/gcc-arm-embedded

**N.B.** `crosstool-ng` toolchaiin for AMR Cortex-M0+ will not work - issues with size optimisation and some libraries.

## Normal flashing
Copy the <myProgram>.bin to remote drive NUCLEO.

Although there is already some files on this file system, copying <myProgram>.bin to the remote drive NUCLO root dir will cause:
* Automatic flashing of the newly added binary
* Reset of the board (and strat of the new program)

## OpenOCD
```bash
drasko@Lenin:~/openocd/tcl$ pwd
/home/drasko/openocd/tcl
drasko@Lenin:~/openocd/tcl$ sudo openocd -f board/st_nucleo_f030r8.cfg 
Open On-Chip Debugger 0.9.0-dev-00181-g1ea25b8 (2014-10-06-23:08)
Licensed under GNU GPL v2
For bug reports, read
	http://openocd.sourceforge.net/doc/doxygen/bugs.html
Info : The selected transport took over low-level target control. The results might differ compared to plain JTAG/SWD
adapter speed: 1000 kHz
adapter_nsrst_delay: 100
srst_only separate srst_nogate srst_open_drain connect_deassert_srst
Info : clock speed 1000 kHz
Info : STLINK v2 JTAG v19 API v2 SWIM v2 VID 0x0483 PID 0x374B
Info : using stlink api v2
Info : Target voltage: 3.240865
Info : stm32f0x.cpu: hardware has 4 breakpoints, 2 watchpoints
```
### Flashing from telnet client
```bash
drasko@Lenin:~$ telnet localhost 4444
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Open On-Chip Debugger
> reset halt
target state: halted
target halted due to debug-request, current mode: Thread 
xPSR: 0xc1000000 pc: 0xfffffffe msp: 0xfffffffc
> flash write_image erase /home/drasko/nucleo/test/build/main.elf
auto erase enabled
target state: halted
target halted due to breakpoint, current mode: Thread 
xPSR: 0x61000000 pc: 0x2000003a msp: 0xfffffffc
wrote 13312 bytes from file /home/drasko/nucleo/test/build/main.elf in 0.760248s (17.100 KiB/s)
> 
```


