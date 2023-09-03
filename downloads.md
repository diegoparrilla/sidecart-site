---
layout: page
title: SidecarT Firmware & Software Downloads
permalink: /downloads
---

Welcome to the official download center for SidecarT firmware and software. Find the latest versions and necessary instructions below.

## SidecarT Firmware

The SidecarT firmware runs on the Raspberry Pi Pico, facilitating communication with the Atari ST.

### Raspberry Pi Pico W 
- **Latest Firmware Version:** [sidecart-pico_w.uf2 ({{ site.FIRMWARE_VERSION }})](https://github.com/diegoparrilla/atarist-sidecart-raspberry-pico/releases/download/{{ site.FIRMWARE_VERSION }}/sidecart-pico_w.uf2)

### Raspberry Pi Pico
*Coming soon*

[🔗 View All Firmware Versions on GitHub](https://github.com/diegoparrilla/atarist-sidecart-raspberry-pico/releases)

## SidecarT Test Software

The test software runs on the Atari ST, checking the SidecarT's communication capabilities.

### Installation Instructions:
1. Copy both `TESTSCRT.TOS` and `TESTROM.BIN` to a floppy disk or a hard disk partition on your Atari ST.
2. Transfer `TESTROM.BIN` to the `roms` folder (or your chosen name) on SidecarT's SD card.
3. Boot the Atari ST and SidecarT in configuration mode (press SELECT button), then select the `TESTROM.BIN` ROM file for emulation.
4. Now start the Atari ST and the SidecarT in normal mode and launch the `TESTSCRT.TOS` program.

### Latest Versions
- **Test Software:** [TESTSCRT.TOS ({{ site.TEST_FIRMARE_VERSION }})](https://github.com/diegoparrilla/atarist-sidecart-test-rom/releases/download/v0.0.3/TESTSCRT.TOS)
- **Test ROM:** [TESTROM.BIN ({{ site.TEST_FIRMARE_VERSION }})](https://github.com/diegoparrilla/atarist-sidecart-test-rom/releases/download/v0.0.3/TESTROM.BIN)

[🔗 View All Test Software Versions on GitHub](https://github.com/diegoparrilla/atarist-sidecart-test-rom/releases)
