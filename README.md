# Acer 5750G Fan Maximiser
==========================

Max out Acer 5750G Fan Speed.

**WARNING:** this is software that, as far as the author is concerned, writes magic values to unknown ports on your laptop. This can easily cause **BRICKING** of your device.

Use at your own risk and be sure to check the laptop model! You may want to inspect the source code also.

I have only tested this software on my Acer 5750G laptop.

Other users reported it working on Acer V3-571G, 5742G and 5741G models.

You have been warned.


This repository contains source code that maximises fan speed on the Acer 5750G (and possibly similar models). It writes one of two magic values (0x77 and 0x76) to port 0x68. One value (0x77) makes the fan spin at maximum speed, the other value makes it return to normal (BIOS-operated maybe?) mode.


The magic values, port numbers and read/write sequences were obtained by reverse engineering FanController.exe provided by Acer for Windows OEM:
http://community.acer.com/t5/Notebooks-Netbooks/Fan-Control-Problems-With-5750G-And-similar-machines/m-p/199637/highlight/true#M33756

Files and description:
* `acer_5750G_fan_controller.pl`: perl script that does the magic.
Can be invoked with `perl acer_5750G_fan_controller.pl MAX` or `perl acer_5750G_fan_controller.pl NORMAL`.
Permission to access /dev/ports is required.
* `FanController-clone.cpp`: An application that does the same thing. Written in Visual C++ 2012.
This essentially does the same ioctls as FanController.exe. I first wrote this to test that the order in which ports were written to / read from was correct.
If using Windows, it is higly recommended you use Acer's original app.
I have included this file just in case somebody might be interested in what driver and what ioctls FanController.exe uses.

For details about how this project came to be as well as how the values were obtained from FanController.exe and eblib.dll, go to http://neduard.wikidot.com/acer-fancontroller-linux
