# CPU32

A tiny MIPS implementation for Terasic DE0/DEx and other Altera FPGA boards



## Features


* Runs MIPS I binary code generated from basic C program
* 32KB RAM (with Block RAM of Cyclone III)
* I/O: 7-seg LEDs for output, sw3 - sw0 for input
* Single clocked design (no pipeline)



## Memory Mappings and I/O access

### Memory map

    0x0000 ->        : text
           <- 0x7efc : stack
    0x7f00 -- 0x7fff : global

              0x7f00 : to display a value on LED 
              0x7ff0 : to input params from sw3 - sw0

### 7-seg LED display modes

The 7-seg LED displays $7f00, PC or registers, based on switch setting:

    sw9:   off = $7f00      on = PC or registers
    sw8:   off = PC         on = reg
    sw7:   off = low bytes  on = high bytes
    sw6-5: not used
    sw4-0: register address


