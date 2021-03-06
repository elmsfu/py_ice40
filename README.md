![experimental](https://img.shields.io/badge/-Work_in_Progress-orange.svg)

# Goal

Generalized utility to configure iCE40 from SBC.

## Why no iceprog?

`iceprog` is great if you are using an FTDI chip. The idea is to have
one tool for beginners and experts that can support most if not all
iCE40 dev boards.

# How to use

```shell
sudo ./py_ice40/example_config.py <binfile>
```

## Troubleshooting

1. If you get a SPIError check that the the SPI device is enabled and present `ls /dev/spidev*`

   To enable on Raspberry Pi:
   ```shell
   sudo raspi-config nonint do_spi 0
   ```

2. GPIOError

   Check that you have GPIO enabled and have permission:
   ```shell
   ls -l /sys/class/gpio
   ```

# Sketch of plan

top level options
 - speed
 - flash or sram
  - flash
    - offset
    - command set?

SPI - spi operations and encapsulation

SRAM - logic with reset and SS to put into slave mode
  - cdone

FLASH - commands and logic for interacting with SPI Flash
  - hold ice40s in reset
  - set of flash commands
  
Intrepid
 - add option for fpga 1 or 2
  - different SS, reset, and cdone
  - auxilary switch
 - support reset of multiple for flash

Hardware support
 spidev and gpio
- bitbang
- FTDI chips
 - USB id

# TODO
 - [x] config FPGA
 - [x] flash access
 - [ ] options compatible with iceprog
 - Device interfaces
   - [x] SPIdev/GPIO support
   - [ ] FTDI support
   - [ ] FX2 support
