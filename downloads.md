---
layout: page
title: Downloads
permalink: /downloads
---

This is the place to download the latest version of the SidecarT firmware and the SidecarT software. 

## Firmware

The SidecarT firmware is the software that runs in the Raspberry Pi Pico. It is responsible for the communication with the Atari ST and for the management of the SD card.

### Firmware for Raspberry Pi Pico W 

- Latest version ({{ site.FIRMWARE_VERSION }}): [sidecart-pico_w.uf2](https://github.com/diegoparrilla/atarist-sidecart-raspberry-pico/releases/download/{{ site.FIRMWARE_VERSION }}/sidecart-pico_w.uf2)

### Firmware for Raspberry Pi Pico

Coming soon.

### Previous versions

Please see the [releases](https://github.com/diegoparrilla/atarist-sidecart-raspberry-pico/releases) page in the GitHub repository.

## Firmware test software

### Instructions

The firmware test software is a program that runs in the Atari ST and tests the communication with the SidecarT. It is useful to check that the SidecarT is working properly.

To install the test software:

1. You must copy the `TESTSCRT.TOS` and the `TESTROM.BIN` to floppy disk or a hard disk partition in your Atari ST computer.
2. You must copy the `TESTROM.BIN` to the `roms` (or your chosen name) folder in the SD card of the SidecarT.
3. Start the Atari ST and the SidecarT in configuration mode (Click SELECT button), and select the `TESTROM.BIN` ROM file as the ROM to emulate.
4. Start the Atari ST and the SidecarT in normal mode now and run the `TESTSCRT.TOS` program.

### Latest versions

- Latest version ({{ site.TEST_FIRMARE_VERSION }}) of [TESTSCRT.TOS](https://github.com/diegoparrilla/atarist-sidecart-test-rom/releases/download/v0.0.3/TESTSCRT.TOS).
- Latest version ({{ site.TEST_FIRMARE_VERSION }}) of [TESTROM.BIN](https://github.com/diegoparrilla/atarist-sidecart-test-rom/releases/download/v0.0.3/TESTROM.BIN).

### Previous versions

Please see the [releases](https://github.com/diegoparrilla/atarist-sidecart-test-rom/releases) page in the GitHub repository.


