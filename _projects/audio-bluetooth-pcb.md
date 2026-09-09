---
layout: single
title: "Audio-to-Bluetooth PCB"
excerpt: "STM32-based hardware design featuring PCM1808 ADC and isolated power routing."
header:
  teaser: /assets/images/projects/Bluetooth-Top-Layout.png
sidebar:
  - title: "Tech Stack"
    text: "STM32F4, KiCad, C, FreeRTOS"
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

## Schematics
Detailed write-up of your hardware/firmware design, block diagrams, schematics, and challenges solved.
{% include gallery id="schematic_gallery" caption="Hardware schematics created in KiCad." %}




