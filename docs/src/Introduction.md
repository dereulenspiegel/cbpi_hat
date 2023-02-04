# Introduction

This CraftBeerPi Hat is mainly intended for brewery automation. It can be used for other use cases
involving digital outputs and sensor inputs, however this is out of scope of this project.
The hat should be compatible with other Single Board Computer systems following the 40 pin GPIO
layout introduced by the Raspberry Pi, but this is not guaranteed and untested.

The Hat has currently the following features:

* Input voltage of 12V - 24V
* DC-DC converter to power the Raspberry Pi from input voltage
* Reverse voltage protection on input
* Digital outputs operate on input voltage and provide up to 1 amp of output current
* Digital outputs are secured by flyback diode to be able to switch inductive loads
* Digital outputs are secured by a PTC resettable fuse to protect from over currents
* RTC for the Raspberry Pi
* OneWire connector to add additional sensors
* Possibility to mount a QWIIC connector for additional sensors and actors
* 5 slots for MAX31865 PT100/PT1000 converter
