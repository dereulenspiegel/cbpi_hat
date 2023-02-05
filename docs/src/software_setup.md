# Software setup

To properly operate this board and make use of all its features a few things need to be
considered on the software side as well.

## RTC

The RTC on this board is a DS3231 and well supported by all Linux kernels. To make use of the RTC
you need to enable I2C and use the proper devive tree overlay to let the kernel know about the
availability of the RTC. To do this simply add the lines to the `config.txt` of your Raspberry Pi
installation

```
dtparam=i2c_arm=on
dtoverlay=i2c-rtc,ds3231
```

## OneWire

OneWire support needs to be enabled as well for the kernel to be usable by userland applicartions like
CraftBeerPi. The OneWire data line is connected to `GPIO4` on the Raspberry Pi. To enable OneWire support
simply add the following line to your `config.txt`

```
dtoverlay=w1-gpio,gpiopin=4
```

## SPI (MAX31865)

The MAX31865 modules are connected via SPI on the bus SPI0 on the Raspberry Pi. To enable SPI support
add the following lines to your `config.txt`

```
dtparam=spi=on
dtoverlay=spi0-0cs
```

We need to disable the chip enable pins of the SPI0 bus, because they would only support 2 devices and
this board supports up to 5 MAX31865. The GPIO formerly used us chip enable are used to control output
2 and 3.

When configuring the MAX31865 modules in CraftBeerPi you need to specify the chip enable pin for each
module. The following table maps the numbered module slot to the correct GPIO serving as the chip enable
pin:

| Module # | GPIO CS |
|-----------|---------|
| 1 | 17 |
| 2 | 27 |
| 3 | 22 |
| 4 |  5 |
| 5 |  6 |


## GPIO

The digital outputs are controlled by GPIO pins. Please note that the outputs are inverted, meaning that if
the GPIO is high the output is disabled and vice versa. To bring the GPIO pins controlling the outputs as soon
as possible on a defined high state and therefore disabling the outputs during boot please add the following
line to your `config.txt`

```
gpio=25,7,8,12,16,20,21=op,dh
```

When configuring GPIO actors in CraftBeerPi please ensure that you specify "Yes" for the field "Inverted"!
The following table maps the GPIO pin numbers to the numbered outputs

| Output # | GPIO |
|----------|------|
| 1 | 25 |
| 2 |  8 |
| 3 |  7 |
| 4 | 12 |
| 5 | 16 |
| 6 | 20 |
| 7 | 21 |
