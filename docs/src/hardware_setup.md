# Hardware Setup

The board itself has been designed with ease of use in mind. However certain things need
to be considered.
First of all please use a proper power supply to power the board. In theory every output
can provide up to 1 amp and the Rasperry Pi could draw up to 3 amp. So in total the board might
require up to 10 amp to be provided by the PSU. Please calculate your actual power requirements
and provide proper fusing on the power input as currently only the outputs have fuses but not
the overall board itself.

## Polarity

Even though the board has reverse voltage protection on its input, polarity is important for
successful operation. When looking at the front of a screw terminal the negative side is always left
and the positive side is always right. This is true for the input connector and all output screw 
terminals.
