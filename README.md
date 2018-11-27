# nRF52840-DK_easy
Just upload this hex file to an nRF52840-DK, and it will then run mecrisp-starellis FORTH

It is essentially the same as the microbit release (version 2.4.6), except that it has been corrected and recompiled to utilize the 256KB RAM and 1MB flash available on the nRF2840 and the proper serial UART pins used on the nRF52840-DK.

To use it, simply:

1. Connect your nRF52840-DK via usb to your computer
2. Drag the hex file in this repository to the JLINK virtual drive which then appears.

The JLINK virtual drive will then briefly disappear as the reprogramming happens.  When it re-appears, you're done.  You can then connect to your nRF52840-DK using a serial terminal (115200 baud) as you normally would, and you will be greeted by the mecrisp-starellis FORTH welcome and prompt.

Enjoy!

