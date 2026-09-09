---
layout: single
title: "Audio-to-Bluetooth PCB"
classes: wide
excerpt: "STM32-based hardware design featuring PCM1808 ADC and isolated power routing."
header:
  teaser: /assets/images/projects/Bluetooth-Top-Layout.png
sidebar:
  - title: "Tech Stack"
    text: "STM32F4, KiCad, C/C++"
schematic_gallery:
  - url: /assets/images/projects/Audio2BluetoothV1.jpg
    image_path: /assets/images/projects/Audio2BluetoothV1.jpg
    alt: "Main schematic file"
    title: "Main schematic file"
  - url: /assets/images/projects/Audio2BluetoothV1-Other.jpg
    image_path: /assets/images/projects/Audio2BluetoothV1-Other.jpg
    alt: "USB power filtering & mounting holes"
    title: "Miscellaneous schematic file"
  - url: /assets/images/projects/Audio2BluetoothV1-IO.jpg
    image_path: /assets/images/projects/Audio2BluetoothV1-IO.jpg
    alt: "Board I/O, excluding USB, schematic file"
    title: "Board I/O schematic file"
  - url: /assets/images/projects/Audio2BluetoothV1-MCU.jpg
    image_path: /assets/images/projects/Audio2BluetoothV1-MCU.jpg
    alt: "STM32F446 & supporting components schematic file"
    title: "Primary MCU schematic file"
  - url: /assets/images/projects/Audio2BluetoothV1-RF.jpg
    image_path: /assets/images/projects/Audio2BluetoothV1-RF.jpg
    alt: "CC2564C, level shifters & supporting components schematic file"
    title: "Bluetooth transceiver schematic file"
  - url: /assets/images/projects/Audio2BluetoothV1-Audio.jpg
    image_path: /assets/images/projects/Audio2BluetoothV1-Audio.jpg
    alt: "PCM1808 & supporting components schematic file"
    title: "Audio schematic file"
repairs_gallery:
  - url: /assets/images/projects/Audio2BluetoothV1.jpg
    image_path: /assets/images/projects/Audio2BluetoothV1.jpg
    alt: "Main schematic file"
    title: "Main schematic file"
---
I had a digital piano, but it couldn't connect to my pair of Bluetooth headphones that I carried with my everywhere. I looked at the options for AUX audio to Bluetooth, but every single one I found was battery powered. <em>This is the perfect opportunity to try PCB design!</em>

This project is a custom PCB based 3.5mm audio to Bluetooth (A2DP) converted. To achieve this I combined a PCM1808 audio to digital converted, which communicates with an <b>STM32F446</b> over <b>I2S</b>. The STM32, then communicates with a CC2564C through the Bluetooth Host Controller Interface (HCI), which uses <b>4-wire UART</b>.

## Schematics

{% include gallery id="schematic_gallery" caption="Hardware schematics created in KiCad." %}

## Layout

This PCB was a mixed signal PCB with audio, high speed digital and RF sections. As such, I decided to use a SIG/GND - GND - GND - SIG/GND stackup. The traces on the top and bottom will connect power and signals while the GND layers will provide simple return paths to avoid EMI interfering with the sensitive analog/RF components.

![The first of the 4 layer PCB]({{ '/assets/images/projects/audio-to-bluetooth-layout-front.png' }})
*Layer 1 of 4 (Top)*

![The last of the 4 layer PCB]({{ '/assets/images/projects/audio-to-bluetooth-layout-back.png' }})
*Layer 4 of 4 (Bottom)*

## Production
As part of this project, I decided to assemble the PCBA. I stencilled the solder paste onto the board, placed the components, and used my reflow-oven.

![The first of the 4 layer PCB]({{ '/assets/images/projects/audio-to-bluetooth-layout-front.png' }})

Unfortunately, the board did not come out perfectly, so I had to make some repairs using a hot air gun and soldering iron:

{% include gallery id="repairs_gallery" caption="Repairs done on board" %}

assembled by hand
fixed mistakes in solder mask by hand
rotated MCU
Crossed PCM1808
Changed direction voltage translators

## Software
I have programmed the STM32 firmware, using HAL to read data from the ADC into memory using DMA. Then it processes it to get a single channel, at 48KHz sampling rate and 16-bit resolution, to reduce the amount of data. Finally I exported the data through SWO. I then exported 
The project is not yet completed. I am currently debugging the transceiver circuitry and trying to implement the drivers. 

-Exported audio from PCM1808
-Implementing HCI drivers & debugging more hardware (CTS) from cc2564C not dropping 


