# mb_remote
A simple way to 'remote' control a micro:bit from Python on a PC/Mac/Pi/Linux

This was some work that I did in August 2015 when MicroPython was first ported to the micro:bit

In it's current state it is now out of step with the MicroPython API, but the concept is sound.

The way I did this was to create a microbit module that you import on the
PC like this

import microbit

And then for each micro:bit feature, the PC version would send the
appropriate REPL to MicroPython running on the micro:bit, it would 'do it's
stuff' and return the result.

So, writing this on the PC

import microbit
import time

    while True:
        x = microbit.accelerometer.get_x()
        y = microbit.accelerometer.get_y()
        print("pos %s %s" % (x, y))
        time.sleep(1)

The bulk of this loop runs on the existing installed python on the PC. When
it calls microbit.accelerometer.get_x() it sends a message to the micro:bit
REPL to get the x acceleration, it returns the value, and that is assigned
to the x variable in the python running on the PC.

So, the micro:bit just becomes a sort of remote sensing device.

    microbit.display.scroll("hello world")

Running this on the PC would scroll Hello World on the micro:bit display.

The micro:bit MicroPython API has changed quite a lot since I first wrote
this, but if this is what you are talking about, I could upload the code to
github and someone else could help me update it to the latest API :)
