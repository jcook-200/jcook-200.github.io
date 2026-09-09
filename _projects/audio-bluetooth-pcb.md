---
layout: single
title: "Audio-to-Bluetooth PCB"
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
   
---
I had a digital piano, but it couldn't connect to my pair of Bluetooth headphones that I carried with my everywhere. I looked at the options for AUX audio to Bluetooth, but every single one I found was battery powered. <em>This is the perfect opportunity to try PCB design!</em>

This project is a custom PCB based 3.5mm audio to Bluetooth (A2DP) converted. To achieve this I combined a PCM1808 audio to digital converted, which communicates with an <b>STM32F446</b> over <b>I2S</b>. The STM32, then communicates with a CC2564C through the Bluetooth Host Controller Interface (HCI), which uses <b>4-wire UART</b>.

## Schematics
Detailed write-up of your hardware/firmware design, block diagrams, schematics, and challenges solved.
{% include gallery id="schematic_gallery" caption="Hardware schematics created in KiCad." %}

## Layout
test

## Production
test

## Software
test


