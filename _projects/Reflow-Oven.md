---
layout: single
title: "Reflow Toaster Oven"
excerpt: "Modified toaster oven using Arduino, SPI temperature module and Solid State Relay with Qt interface"
header:
  #teaser: /assets/images/projects/
sidebar:
  - title: "Tech Stack"
    text: "SPI, Arduino, C, Serial Communication, Python, Qt "
---
-intro

what is it?

## Hardware & Firmware
-Removed old controls and mecahnism. 
-Added single SSR to control all 4 elements
-Added MAX31855 module with k-type thermocouple
-Arduino connects via SPI, GPIO and Serial over USB
-Programmed PID loop with moving set point
-Implemented basic communication with arduino

## Interface

-Used Qt in python to communicate with arduino over USB Serial
-Allows imports of csv temp goal data
-Graphs current temp against goal temp
