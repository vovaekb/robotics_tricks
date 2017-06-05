# Useful utilities on RPi
## Hardware information
To get information about processor and memory read file /proc/cpuinfo:

```bash
cat /proc/cpuinfo
```
To list USB devices use lsusb command:
```bash
lsusb
```

## Voltages and temperatures informatiom with vcgencmd 
vcgencmd provides custom commands for Raspberry Pi for obtaining information about voltages ans temperature.
To get the temperature of board use fllowing command:
```bash
vcgencmd measure_temp
```
To get voltage we use command:
```bash
vcgencmd measure_volts <id>
```
where id can be one of **core**, **sdram_c**, **sdram_i**, **sdram_p** (core id on default).

To get detailed information about vcgencmd command [visit this page](http://www.elinux.org/RPI_vcgencmd_usage) or read Chapter 18 in the [book](http://dl.finebook.ir/book/65/11843.pdf).
