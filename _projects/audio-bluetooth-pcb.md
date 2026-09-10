---
layout: single
title: "Audio-to-Bluetooth PCB"
classes: wide
excerpt: "STM32-based hardware design featuring PCM1808 ADC and isolated power routing."
header:
  teaser: /assets/images/projects/Bluetooth-Top-Layout.png
sidebar:
  - title: "Domain"
    text: "Mixed-Signal PCB Design & Embedded Hardware"
  - title: "Core Architecture"
    text: "STM32F446 MCU, PCM1808 Audio ADC, CC2564C Bluetooth Transceiver"
  - title: "EDA & Layout"
    text: "KiCad (4-Layer Stackup, SIG-GND-GND-SIG Controlled Impedance & EMI Mitigation)"
  - title: "Protocols & Bus Interfaces"
    text: "I2S Audio Stream, 4-Wire UART (HCI), SPI, SWO Debug, DMA Data Pipelines"
  - title: "Assembly & Bring-Up"
    text: "Solder Stenciling, Reflow Oven SMT Assembly, BGA/QFN Rework, Hot Air & Iron Repair"
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
---
I had a digital piano, but it couldn't connect to my pair of Bluetooth headphones that I carried with my everywhere. I looked at the options for AUX audio to Bluetooth, but every single one I found was battery powered. <em>This is the perfect opportunity to try PCB design!</em>

This project is a custom PCB based 3.5mm audio to Bluetooth (A2DP) converted. To achieve this I combined a PCM1808 audio to digital converted, which communicates with an <b>STM32F446</b> over <b>I2S</b>. The STM32, then communicates with a CC2564C through the Bluetooth Host Controller Interface (HCI), which uses <b>4-wire UART</b>.

## Schematics

{% include gallery id="schematic_gallery" caption="Hardware schematics created in KiCad." %}

## Layout

This PCB was a <b>mixed signal PCB</b> with audio, high speed digital and RF sections. As such, I decided to use a SIG/GND - GND - GND - SIG/GND stack up. The traces on the top and bottom will connect power and signals while the GND layers will provide simple return paths to avoid EMI interfering with the sensitive analog/RF components.

![The first of the 4 layer PCB]({{ '/assets/images/projects/audio-to-bluetooth-layout-front.png' }})
*Layer 1 of 4 (Top)*

![The last of the 4 layer PCB]({{ '/assets/images/projects/audio-to-bluetooth-layout-back.png' }})
*Layer 4 of 4 (Bottom)*

## Production
As part of this project, I decided to assemble the PCBA. I stencilled the solder paste onto the board, placed the components, and used my reflow-oven. The remaining through-hole components where soldered on by hand.

![Current State PCB]({{ '/assets/images/projects/Current-PCB.jpg' }})

Unfortunately, the board did not come out perfectly, so I had to make some repairs using a hot <b>air gun</b> and <b>soldering iron</b>:

1) Rotated STM32 usign hot air gun (the small circle is the pin 1 marker, not the big circle)
2) Lifted and crossed 2 pins on the ADC
3) Fixed tombstoned 0402 capacitor
4) lifted and combined 2 pins to change direction on level-shifter

## Software
I have programmed the STM32 firmware, using <b>HAL</b> to read data from the ADC into memory using <b>DMA</b>. Then it processes it to get a single channel, at 48KHz sampling rate and 16-bit resolution, to reduce the amount of data. Finally I exported the data through <b>SWO</b>, before packing it into an uncompressed .WAV audio file.

The project is not yet completed. I am currently implementing the manufacturer's Bluetooth driver, while continuing to debug the hardware side of the Bluetooth transceiver.

### Key Highlights

* **Mixed-Signal Architecture:** Designed a custom 4-layer PCB integrating high-speed digital lines, 24-bit I2S audio routing, and a 2.4 GHz RF Bluetooth transceiver with dedicated continuous ground planes for EMI containment.
* **Protocol & Data Pipeline:** Interfaces a PCM1808 ADC over I2S directly to an STM32F446, leveraging circular DMA buffers for real-time audio sample processing without CPU overhead.
* **Full-Cycle Fabrication & Rework:** Handled complete PCBA assembly from solder paste stenciling and reflow heating down to fine-pitch QFP/QFN hot-air pin corrections and 0402 SMD rework.


