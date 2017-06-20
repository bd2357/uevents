# uevents
small events package for microprocessors, usable OS replacement, kind of like node

## small micros
many small micro projects like for an Arduino or even cortex-m0 have a background
loop inside a while(1) statement the just runs forever. Most often I don't really need
a full OS but I often do need some ability to chain together a sequence of functions
in response to some event like time passing or data available in a buffer. 

This small package is a simple framework you can drop onto most embedded C projects to 
let you run your collection of functions in response to events.  It supports both 
background (blocking) functions and to a certain extent isr level functions and 
is mainly intended to launch a background task in response to some isr activity.

## timers
At the root of the framework are one or more timer sources. These can be as simple
as the system tick, which is present on most microprocessors, or can be more involved
using the things like output compare functions with free running timers.

```
I wrote this when I was working on stm32 family of arm processors and discovered that
the uarts don't have FIFOs and there was no way to receive variable length messages
unless you wrote your own timeout method. To make it worse, if you had a higher
baud rate, you really needed to use DMA to get the data out of the uart so you
didn't lose bytes. This package was used to wrap the circular DMA buffer with a
resettable timer that would tell me when the transmission had stopped.
```

### Ceedling
I don't do a lot of non-embedded programming, so to do offline development of frameworks
or code experiments I use ceedling and gcc because it just works and I like the
test driven development model in principle. (although it is still a pain for embedded)
If you want to run the test code, you will need Ruby and gcc and the ceedling gem.
Google it. you can also look in the vendor directories for ceedling documentation.

