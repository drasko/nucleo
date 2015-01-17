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
**N.B.** `crosstoolt-ng` toolchaiin for AMR Cortex-M0+ will not work - issues with size optimisation and some libraries.


