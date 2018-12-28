# nRF52840-DK_easy
Just upload this hex file to an nRF52840-DK, and it will then run mecrisp-starellis FORTH

It is essentially the same as the microbit release (version 2.4.6), except that it has been corrected and recompiled to utilize the 256KB RAM and 1MB flash available on the nRF52840 and the proper serial UART pins used on the nRF52840-DK.

To use it, simply:

1. Connect your nRF52840-DK via usb to your computer
2. Drag the hex file in this repository to the JLINK virtual drive which then appears.

The JLINK virtual drive will then briefly disappear as the reprogramming happens.  When it re-appears, you're done.  You can then connect to your nRF52840-DK using a serial terminal (115200 baud) as you normally would, and you will be greeted by the mecrisp-sterallis FORTH welcome and prompt.

For all the credits and attributions, please see http://mecrisp.sourceforge.net/ and the discussion: https://sourceforge.net/p/mecrisp/discussion/general/thread/6fe04a2841/

Enjoy!

Update 2018-12-11: Use the code located here: https://github.com/rabbithat/nRF52840_enable_reset_pin to enable the reset button on the nRF52840-DK.

Note: mecrisp-stellaris-nRF52840DK-RA.hex is mecrisp-stellaris 2.4.7


File clone.hex is mecrisp-stellaris 2.4.7 RA together with the following files already pre-loaded into flash:
essential functions,
delay functions,
uploader,
programmer.

Complete.hex is the same as clone.hex, but including the cloning software and 'clone" word.

ultra.hex is the same as complete.hex plus the radio REPL.
