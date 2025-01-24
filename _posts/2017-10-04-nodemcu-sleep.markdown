---
layout: post
title:  "NODEMCU ESP8266 IO Pin state during DeepSleep, High, Low, Tristate"
date:   2017-10-04 10:50:18 +0000
categories: tech electronics
---

Not a long post, but something I found little reference to.

I have been working on a project that uses the NodeMCU v1 board to drive a couple of transistor based outputs. The project uses a battery, so I was keen to keep the module in DeepSleep() for as long as possible.

It turns out however, that contrary to what is stated in the ESP8266 datasheet – the GPIOs do not hold their state through DeepSleep(). For me the pins I was using went high during sleep, turning on relays and LEDs galore.  I found that a fairly stout resistor would pull them back down during the sleep, without impacting normal operation – but this added a couple of milliamps to my sleep current, and seemed wasteful to have the board sit burning current in a resistor.

A little exploration found, for me at least that D0-D4 would always go high during sleep, but D5-D7 actually held their state. So far this has worked for several weeks, and quite a bit of testing.

So if you are having this problem, maybe try using the higher numbered outputs!