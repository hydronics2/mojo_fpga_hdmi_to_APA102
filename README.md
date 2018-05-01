# mojo_fpga
driving 3 APA102 LEDs with the Mojo FPGA in lucid


Using the beginner greeter.luc example to push bytes of APA102 LED data from an array of bytes to the SPI


led array of bytes to turn 3 LEDs on when you send an 'h' over serial (any baud seems to work). It also prints back the array you just sent for troubleshooting. It works better if you continually update bytes (wrather than sending the array once) but this is nice for troubleshooting.



data2 = {8b0,8b0,8b0,8b0,8b0,8b0,8b0,8b0,8h1e,8he3, 8b0, 8b0, 8b0, 8he3, 8b0, 8b0, 8h1e, 8he3, 8b0, 8b0, 8b0, 8b0};


The APA102 data protocol is described here: https://cpldcpu.wordpress.com/2014/11/30/understanding-the-apa102-superled/

- as 32 bits of 0s for the start of the LED strip

- followed by a 32 bit LED frame (per pixel). The first byte is 3 bits (111) and 5 bits (brightness value), and then 1 byte each for R,G,B... (need to verify order)

- followed by 32 bits of 1 or 0 depending on what you read
