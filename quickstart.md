---
layout: page
title: Quickstart
permalink: /quickstart
excerpt: "Quickstart page for SidecarT setup! Merge Atari ST's nostalgia with modern tech. Grab an Atari, integrate SidecarT, and experience supercharged retrocomputing!"
image: /assets/images/board-hand.png
---

## (Obvious) Prerequisite.Grab an Atari ST/STE/Mega

While it may seem straightforward, the initial step involves obtaining a functional Atari ST, STE, or Mega computer. It's okay if certain components aren't in perfect shape—for instance, the floppy drive or the hard disk might not be operational—as long as the machine can power on. It's worth noting that the SidecarT board can emulate a physical floppy drive, so an Atari ST without a (or a broken) floppy drive can still be used with the SidecarT board. The SidecarT board is also compatible with TOS versions ranging from 1.00 to 2.06, almost every single ST and STE series compute sold. If you haven't secured one yet, consider checking second-hand sales websites or specialized forums such as [Atari Forum](https://www.atari-forum.com/) and [Atari Age](https://www.atariage.com/).

{:refdef: style="text-align: center;"}
[![Atari 520ST](/assets/images/quickstart/atari520st.jpeg)](/assets/mage/quickstart/atari520st.jpeg){:.glightbox}
{: refdef}

## Step 1. Acquire a SidecarT board

To get your hands on a SidecarT, you can either [purchase it from our store](https://store.sidecartridge.com/) or [build one yourself](https://docs.sidecartridge.com/architecture_and_design/).

{:refdef: style="text-align: center;"}
[![SidecarT without Raspberry Pi Pico](/assets/images/quickstart/board-single.png)](/assets/images/quickstart/board-single.png){:.glightbox}
{: refdef}


The SidecarT operates using a Raspberry Pi Pico W. You have the option to purchase the SidecarT with an included and pre-configured Raspberry Pi Pico W, or you can buy one separately. If you choose to purchase one on your own, you should look for a [Raspberry Pi Pico WH (Reference SC0919)](https://www.raspberrypi.com/documentation/microcontrollers/raspberry-pi-pico.html#raspberry-pi-pico-w-and-pico-wh), which already comes with the necessary 40-pin connectors to attach to the SidecarT's motherboard. Alternatively, you can buy a [Raspberry Pi Pico W (Reference SC0918)](https://www.raspberrypi.com/documentation/microcontrollers/raspberry-pi-pico.html#raspberry-pi-pico-w-and-pico-wh) and procure two 20-pin connectors, then solder them to the board yourself. Here's a [link to a manufacturer](https://www.lcsc.com/product-detail/span-style-background-color-ff0-Pin-span-Headers_BOOMELE-Boom-Precision-Elec-C50981_C50981.html) for reference.

{:refdef: style="text-align: center;"}
[![Raspberry Pi Pico WH](/assets/images/quickstart/raspberry-pi-pico-rp2040-wh.png)](/assets/images/quickstart/raspberry-pi-pico-rp2040-wh.png){:.glightbox}
{: refdef}

To install and update the SidecarT firmware on the Raspberry Pi Pico W, you'll need a USB A to micro USB *data* cable. When purchasing from our store, a cable suited for this task is included. It's important to note the emphasis on a "data" cable - a simple charging cable won't suffice.

With the latest improvements to the SidecarT project, using a microSD card is now optional, though it remains a good choice for extended storage and flexibility. Additionally, while having a WiFi Access Point for connecting the SidecarT enhances its capabilities, it's not mandatory. You can use the SidecarT with either of these options, both, or none at all, depending on your preferences.

{:refdef: style="text-align: center;"}
[![USB A to micro USB](/assets/images/quickstart/microusb.jpeg)](/assets/images/quickstart/microusb.jpeg){:.glightbox}
{: refdef}

## Step 2. Install the latest firmware version on the SidecarT

> :warning: If your purchased SidecarT includes the Raspberry Pi Pico W or WH, this step is unnecessary. The device arrives with the most recent firmware version already installed.


To install the latest SidecarT firmware on the Raspberry Pi Pico W, connect your PC, Mac, or Linux to the Raspberry Pi Pico W using the USB cable. Now hold down the BOOTSEL button for a few seconds and then hold down the RESET button. Now release the RESET button and gently release the BOOTSEL button afterwards. A new drive named `RPI-RP2` should appear on your PC, Mac, or Linux. Open it.

{:refdef: style="text-align: center;"}
[![How enter in BOOTSEL mode](/assets/images/quickstart/bootsel-mode.gif)](/assets/images/quickstart/bootsel-mode.gif){:.glightbox}
{: refdef}

In this directory, you will need to copy the latest available Firmware version, which you can directly download from the links below:

- **Latest STABLE Firmware ({{ site.FIRMWARE_VERSION }}):** [sidecart-pico_w.uf2 ({{ site.FIRMWARE_VERSION }})](https://github.com/diegoparrilla/atarist-sidecart-raspberry-pico/releases/download/{{ site.FIRMWARE_VERSION }}/sidecart-pico_w.uf2)

- **Latest BETA Firmware ({{ site.FIRMWARE_BETA_VERSION }}):** [sidecart-pico_w.uf2 ({{ site.FIRMWARE_BETA_VERSION }})](https://github.com/diegoparrilla/atarist-sidecart-raspberry-pico/releases/download/{{ site.FIRMWARE_BETA_VERSION }}/sidecart-pico_w-BETA.uf2)

Once you've copied the file corresponding to your Raspberry Pico version, disconnect the power cable. The new firmware has now been flashed.

## Step 3. (Optional) Format the microSD card to FAT16

> :warning: If you're aiming for a brief test of the SidecarT, you can bypass this step and move directly to step 5. Yet, for those intending to use the SidecarT with a microSD card, this step is indispensable.

To use the SidecarT effectively, your microSD card needs to be formatted in FAT16 or exFAT. Here's how you can format it in FAT16 or exFAT on various platforms:

### Windows:

1. Insert your microSD card into your computer using an SD card reader.
2. Press `Windows + E` to open the File Explorer.
3. Right-click on your microSD card from the list of devices and choose `Format`.
4. In the Format window, from the `File system` dropdown, choose `FAT (Default)` (Note: FAT16 might be referred to as just FAT in some versions of Windows) or `exFAT`.
5. Click `Start` to format the card.
6. Once completed, safely eject the card from your computer.

### macOS:

1. Insert your microSD card into your computer.
2. Open `Disk Utility` (you can use Spotlight with `Command + Space` and then type "Disk Utility").
3. Select your microSD card from the list on the left and then click `Erase`.
4. For the format, choose `MS-DOS (FAT)` which is the macOS term for FAT16, or `ExFAT`.
5. Click `Erase` to format the card.
6. Once the process is complete, safely eject the card from your Mac.

### Linux:

**Using the Terminal:**

1. Insert your microSD card into your computer.
2. Open a terminal.
3. Type `sudo fdisk -l` to list all the storage devices. Identify your microSD card's name (usually `/dev/sdb` or `/dev/mmcblk0` or similar).
4. Type `sudo umount /dev/sdX*` replacing `X` with your microSD card letter.
5. If you want to format it to FAT16, type `sudo mkfs.vfat -F 16 /dev/sdX` again replacing `X` with your microSD card letter to format it to FAT16.
6. If you want to format it to exFAT, type `sudo mkfs.exfat /dev/sdX` instead. Probably you will need to install some packages before, please check what your distribution needs.
6. Once the process completes, you can safely eject the microSD card.

**Using GParted (GUI):**

1. Insert your microSD card into your computer.
2. Open GParted. If you don't have it installed, you can install it using `sudo apt install gparted` on Debian/Ubuntu based distributions.
3. Select your microSD card from the top right dropdown.
4. Right-click on the microSD card partition and select `Format to` -> `fat16` or `exFAT`. Note: probably you will need to install some packages before, please check what your distribution needs
5. Click on the green checkmark to apply the changes.
6. Once the process completes, close GParted and safely eject your microSD card.

**Note:** Always ensure you've selected the correct device to format, especially when working with disk utilities, to avoid data loss.

## Step 4. (Optional) Copy the ROM images onto the microSD card

To get the ROM images for your SidecarT you can use your own images or you can have a look at this [collection](/roms) to download the available ROM images.

The default folder for the ROM images is `/roms` in the root of the microSD card. You can change the folder editing the configuration parameters from the configuration application.

As a side not, SidecarT support STEEM ROM images format out of the box.


## Step 5. Connect the SidecarT with the Raspberry Pi Pico W and the microSD to the computer

> :warning: **Important Cleaning Notice for SidecarT Users:** Ensuring the cleanliness of your Atari ST/STE/Mega's cartridge interface and the SidecarT's cartridge connector is crucial for optimal functionality. An unclean connection can lead to issues with device performance. We highly recommend using a soft brush and isopropyl alcohol for thorough cleaning. The headers of the SidecarT are soldered by hand, and while we strive to clean all the flux, we cannot guarantee that they are completely free of residues. Regular cleaning on your part is essential for maintaining the best connection and device performance.

Before turning on your computer, plug the SidecarT into the cartridge interface on the side of the computer. **It's crucial to ensure that the Raspberry Pi Pico faces upwards**.

{:refdef: style="text-align: center;"}
[![How to plug the SidecarT in the Atari ST cartridge](/assets/images/quickstart/plug-sidecart.gif)](/assets/images/quickstart/plug-sidecart.gif){:.glightbox}
{: refdef}

Make sure to handle the SidecarT carefully to avoid any damage. Once connected, you can turn on the computer and proceed with using the SidecarT.

## Step 6. Switch on the computer

When powering on the computer for the first time with SidecarT connected, it will start in CONFIGURATOR mode. In CONFIGURATOR mode, you can set up the specific function of the SidecarT. Currently, you can configure the SidecarT as a [ROM emulator](https://docs.sidecartridge.com/userguide/#rom-emulation), a [floppy emulator](https://docs.sidecartridge.com/userguide/#floppies-emulation), or a [real-time clock](https://docs.sidecartridge.com/userguide/#real-time-clock-rtc).

> Note: You know you're in CONFIGURATOR mode when booting because the Raspberry Pi Pico W's LED will show two short blinks, one long blink and another short blink; a 'C' in Morse code. 

{:refdef: style="text-align: center;"}
[![First boot with SidecarT in condigurator mode](/assets/images/quickstart/step-6-configurator.gif)](/assets/images/quickstart/step-6-configurator.gif){: style="max-width:640px; width: 100%;" .glightbox}
{: refdef}

Upon booting, the classic Atari GEM desktop should appear with an additional icon labeled "Cartridge". Open it, and inside you'll find a file named `SIDECART.TOS`. Run it.

## Step 7a. Select the ROM to Emulate from the microSD card

Upon starting the program, you'll be presented with a list of options showcasing the various capabilities of the SidecarT.

Press '1' and hit Enter to choose the *Emulate ROM image from microSD card* option. The system will then display a list of ROM images you've copied to the microSD card in step 4.

Enter the number corresponding to the ROM image you wish to emulate and press Enter. The SidecarT will load the selected image, preparing it for execution on the computer's next startup or reset.

> Note: You know you're in ROM EMULATION mode when booting because the Raspberry Pi Pico W's LED will show a short blink; a 'E' in Morse code.

{:refdef: style="text-align: center;"}
[![Load ROM from micrcoSD card of the SidecarT](/assets/images/quickstart/step-7a-load-rom.gif)](/assets/images/quickstart/step-7a-load-rom.gif){: style="max-width:640px; width: 100%;" .glightbox}
{: refdef}

## Step 7b: Wi-Fi Configuration & ROM Emulation via HTTP Server

For those utilizing a SidecarT with a Raspberry Pi Pico W, you have the capability to connect to a Wi-Fi network and fetch the ROM image directly from an HTTP server. 

Initiate this by pressing 'W' to access the *Wi-Fi configuration* menu.

{:refdef: style="text-align: center;"}
[![Wifi configuraton of SidecarT](/assets/images/quickstart/step-7b-1-configure-wifi.gif)](/assets/images/quickstart/step-7b-1-configure-wifi.gif){: style="max-width:640px; width: 100%;" .glightbox}
{: refdef}

Once inside, scroll through the list of available networks. Confirm your desired network by pressing 'Enter'. If your chosen network is secure, you'll be prompted to input the password. After a successful connection, you'll be redirected to the main menu.

The connection status will then be displayed at the screen's base. Upon acquiring an IP address from the DHCP server, the SidecarT's IP address will be showcased. With this, a new menu option emerges: *Emulate ROM image from Wi-Fi*.

Activate this option by pressing '2'. The system will then present a list of ROM images available on the HTTP server. 

{:refdef: style="text-align: center;"}
[![Show the ROMS available in the HTTP server](/assets/images/quickstart/step-7b-2-download-rom.gif)](/assets/images/quickstart/step-7b-2-download-rom.gif){: style="max-width:640px; width: 100%;" .glightbox}
{: refdef}

Scroll to your desired ROM image and confirm with 'Enter'. The system will handle the download and ready the ROM for execution on your next system startup or reset.

Now you can reset or power cycle your computer. Every time you reset or power cycle your computer, it will load the image as a genuine cartridge ROM.

## Step 8. Find an application in the Atari ST Floppy Database

The SidecarT board allows easy access to a database of floppy images without needing additional setup beyond the initial Floppies Emulation configuration.

- **Accessing the Database**: From the main menu, select *5. Download from the Floppy Images database*. Use the alphabetical and numerical bar to navigate and select an application by its starting letter.

- **Downloading an Application**: Press RETURN or ENTER to initiate the download of the chosen application's floppy image to the storage folder.

- **Finalizing the Setup**: Once downloaded, the SidecarT board's green LED will signal readiness by blinking an 'F' in Morse code. Reset or power cycle the Atari ST to start using the downloaded floppy image as a regular floppy disk.

{:refdef: style="text-align: center;"}
[![Download Floppy Image from Wi-Fi in SidecarT](/assets/images/quickstart/step-8-download-floppy-image.gif)](/assets/images/quickstart/step-8-download-floppy-image.gif){: style="max-width:640px; width: 100%;" .glightbox}
{: refdef}

## Extra bonus. Enter in the CONFIGURATOR mode again

If you want to reconfigure the SidecarT for a different feature, there is a special button in the SidecarT board for it: the SELECT button.

The SELECT button in the revision 0.0.1:
{:refdef: style="text-align: center;"}
[![Boot in SELECT mode in SidecarT rev 0.0.1](/assets/images/quickstart/select-button.gif)](/assets/images/quickstart/select-button.gif){:.glightbox}
{: refdef}


The SELECT button in the revision 1.0.0 and onwards:
{:refdef: style="text-align: center;"}
[![Boot in SELECT mode in SidecarT rev 2.0.0](/assets/images/quickstart/select-button-v2.gif)](/assets/images/quickstart/select-button-v2.gif){:.glightbox}
{: refdef}

To launch the SidecarT in CONFIGURATOR mode again, simply push the SELECT button for **more than a second** and power cycle your computer. The Raspberry Pi Pico W will blink the 'C' in morse code. It will boot again in CONFIGURATOR mode like in step 6.

## What's next?

You can now explore the different features available in the SidecarT.

1. [Download floppy images from the Atari ST database](https://docs.sidecartridge.com/userguide/#atari-st-database-of-floppy-images)
2. [Emulate a Floppy Drive](https://docs.sidecartridge.com/userguide/#floppies-emulation-configuration-preview)
3. [Real Time Clock](https://docs.sidecartridge.com/userguide/#real-time-clock-rtc)
4. [SidecarT in Ripper mode](https://docs.sidecartridge.com/userguide/#enable-rom-delay--ripper-mode)
5. [Setup your own ROMs hosting web server](https://docs.sidecartridge.com/how_to/#set-up-your-own-http-server-for-your-romsw)

You can find more information in the [Documentation](https://docs.sidecartridge.com) site.

## Need help?

Check out the [throubleshoot pages](https://docs.sidecartridge.com/troubleshooting/), or our [contact us](/contact) page if you have any questions or issues. We're happy to help!
