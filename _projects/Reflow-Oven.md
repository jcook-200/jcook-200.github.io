---
layout: single
title: "Reflow Toaster Oven"
classes: wide
excerpt: "Modified toaster oven using Arduino, SPI temperature module and Solid State Relay with Qt interface"
header:
  teaser: /assets/images/projects/Reflow-Interface.jpg
sidebar:
  - title: "Tech Stack"
    text: "SPI, Arduino, C, Serial Communication, Python, Qt "
---
In PCBA manufacturing, and specifically when it comes to surface mounted components, it is standard practice to:

  1) Apply a layer of solder paste (very small solder balls suspended in a binder)
  2) Place the components onto the solder paste, often with robots
  3) Heat the PCBA's in order to evenly melt the solder

In my other audio to Bluetooth project, I decided not to get my board assembled. Instead, I would manufacture my own!

In order to melt the solder, I decided to make a reflow-oven, the piece of equipment that heats the boards.

## Hardware & Firmware

Convignenetly, I spotted a toaster oven on the side of the street, and ordered the remain parts needed for my design: 
![Hardware Diagram]({{ '/assets/images/projects/Reflow-Toaster-Oven-Hardware.jpg' }})

I set up a PID loop in the arduino using the SPI data from the MAX31855. Then I setup a moving setpoint based on data received from the laptop.

## Interface

Used Qt in python to create an interface. This interface reads data from the Arduino and give target temperatures to it using Serial over USB.

![Qt Reflow Oven Interface]({{ '/assets/images/projects/Reflow-Interface.jpg' }})

As you see the interface includes a graph with target temp in red and observed temperature in white. There is also a button that allows you to import csv data for the target temperature.
