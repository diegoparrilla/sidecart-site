---
layout: page
title: Quickstart
permalink: /quickstart
---

## (Obvious) Prerequisite.Grab an Atari ST/STE/Mega

While it may seem straightforward, the initial step involves obtaining a functional Atari ST, STE, or Mega computer. It's okay if certain components aren't in perfect shape—for instance, the floppy drive or the hard disk might not be operational—as long as the machine can power on. If you haven't secured one yet, consider checking second-hand sales websites or specialized forums such as [Atari Forum](https://www.atari-forum.com/) and [Atari Age](https://www.atariage.com/).

{:refdef: style="text-align: center;"}
[![Atari 520ST](/assets/image/quickstart/atari520st.jpeg)](/assets/mage/quickstart/atari520st.jpeg){:.glightbox}
{: refdef}

## Step 1. Acquire a SidecarT board

To get your hands on a SidecarT, you can either [purchase it from our store](/buy) or [build one yourself](/build).

{:refdef: style="text-align: center;"}
[![SidecarT without Raspberry Pi Pico](/assets/image/quickstart/board-single.png)](/assets/image/quickstart/board-single.png){:.glightbox}
{: refdef}


The SidecarT operates using a Raspberry Pi Pico W (Raspberry Pi Pico soon). You have the option to purchase the SidecarT with an included and pre-configured Raspberry Pi Pico W, or you can buy one separately. If you choose to purchase one on your own, you should look for a Raspberry Pi Pico WH, which already comes with the necessary 40-pin connectors to attach to the SidecarT's motherboard. Alternatively, you can buy a Raspberry Pi Pico W and procure two 20-pin connectors, then solder them to the board yourself. Here's a [link to a manufacturer](https://www.lcsc.com/product-detail/span-style-background-color-ff0-Pin-span-Headers_BOOMELE-Boom-Precision-Elec-C50981_C50981.html) for reference.

{:refdef: style="text-align: center;"}
[![Raspberry Pi Pico WH](/assets/image/quickstart/raspberry-pi-pico-rp2040-wh.png)](/assets/image/quickstart/raspberry-pi-pico-rp2040-wh.png){:.glightbox}
{: refdef}

To install and update the SidecarT firmware on the Raspberry Pi Pico W, you'll need a USB A to micro USB *data* cable. When purchasing from our store, a cable suited for this task is included. It's important to note the emphasis on a "data" cable - a simple charging cable won't suffice.

Here's the revised text:

---

With the latest improvements to the SidecarT project, using a microSD card is now optional, though it remains a good choice for extended storage and flexibility. Additionally, while having a WiFi Access Point for connecting the SidecarT enhances its capabilities, it's not mandatory. You can use the SidecarT with either of these options, both, or none at all, depending on your preferences.

---
{:refdef: style="text-align: center;"}
[![USB A to micro USB](/assets/image/quickstart/microusb.jpeg)](/assets/image/quickstart/microusb.jpeg){:.glightbox}
{: refdef}

## Step 2. Install the latest firmware version on the SidecarT

To install the latest SidecarT firmware on the Raspberry Pi Pico W, connect your PC, Mac, or Linux to the Raspberry Pi Pico W using the USB cable. Before powering on the Raspberry Pi Pico W, hold down the BOOTSEL button for a few seconds and then plug in the USB cable. A new drive named `RPI-RP2` should appear on your PC, Mac, or Linux. Open it.

PLACEHOLDER FOR A GIF SHOWING HOW TO PRESS THE BOOTSEL BUTTON

In this directory, you will need to copy the latest available Firmware version, which you can directly download from the links below:

### Raspberry Pi Pico W 
- **Latest Firmware Version:** [sidecart-pico_w.uf2 ({{ site.FIRMWARE_VERSION }})](https://github.com/diegoparrilla/atarist-sidecart-raspberry-pico/releases/download/{{ site.FIRMWARE_VERSION }}/sidecart-pico_w.uf2)

### Raspberry Pi Pico
*Coming soon*

Once you've copied the file corresponding to your Raspberry Pico version, disconnect the power cable. The new firmware has now been flashed.

## Step 3. (Optional) Format the microSD card to FAT16

To use the SidecarT effectively, your microSD card needs to be formatted in FAT16. Here's how you can format it in FAT16 on various platforms:

### Windows:

1. Insert your microSD card into your computer using an SD card reader.
2. Press `Windows + E` to open the File Explorer.
3. Right-click on your microSD card from the list of devices and choose `Format`.
4. In the Format window, from the `File system` dropdown, choose `FAT (Default)` (Note: FAT16 might be referred to as just FAT in some versions of Windows).
5. Click `Start` to format the card.
6. Once completed, safely eject the card from your computer.

### macOS:

1. Insert your microSD card into your computer.
2. Open `Disk Utility` (you can use Spotlight with `Command + Space` and then type "Disk Utility").
3. Select your microSD card from the list on the left and then click `Erase`.
4. For the format, choose `MS-DOS (FAT)` which is the macOS term for FAT16.
5. Click `Erase` to format the card.
6. Once the process is complete, safely eject the card from your Mac.

### Linux:

**Using the Terminal:**

1. Insert your microSD card into your computer.
2. Open a terminal.
3. Type `sudo fdisk -l` to list all the storage devices. Identify your microSD card's name (usually `/dev/sdb` or `/dev/mmcblk0` or similar).
4. Type `sudo umount /dev/sdX*` replacing `X` with your microSD card letter.
5. Type `sudo mkfs.vfat -F 16 /dev/sdX` again replacing `X` with your microSD card letter to format it to FAT16.
6. Once the process completes, you can safely eject the microSD card.

**Using GParted (GUI):**

1. Insert your microSD card into your computer.
2. Open GParted. If you don't have it installed, you can install it using `sudo apt install gparted` on Debian/Ubuntu based distributions.
3. Select your microSD card from the top right dropdown.
4. Right-click on the microSD card partition and select `Format to` -> `fat16`.
5. Click on the green checkmark to apply the changes.
6. Once the process completes, close GParted and safely eject your microSD card.

**Note:** Always ensure you've selected the correct device to format, especially when working with disk utilities, to avoid data loss.

## Step 4. (Optional) Copy the ROM images onto the microSD card

To get the ROM images for your SidecarT you can use your own images or you can have a look at this repo [here](https://romimages.sidecart.xyz) to download the available ROM images.

As a side not, SidecarT support STEEM ROM images format out of the box.


## Step 5. Connect the SidecarT with the Raspberry Pi Pico W and the microSD to the computer

Before turning on your computer, plug the SidecarT into the cartridge interface on the side of the computer. **It's crucial to ensure that the Raspberry Pi Pico faces upwards**.

PLACEHOLDER FOR A GIF SHOWING HOW TO PLUG IN

Make sure to handle the SidecarT carefully to avoid any damage. Once connected, you can turn on the computer and proceed with using the SidecarT.

## Step 6. Switch on the computer

When powering on the computer for the first time with SidecarT connected, it will start in CONFIGURATOR mode. In CONFIGURATOR mode, you can set up the specific function of the SidecarT. Currently, it only acts as a ROM emulator. 

> Note: You know you're in CONFIGURATOR mode when booting because the Raspberry Pi Pico W's LED will show two short blinks, one long blink and another short blink; a 'F' in Morse code. 

PLACEHOLDER WITH A GIF SHOWING THE BOOT SEQUENCE

Upon booting, the classic Atari GEM desktop should appear with an additional icon labeled "Cartridge". Open it, and inside you'll find a file named `SIDECART.TOS`. Run it.

PLACEHOLDER WITH A GIF SHOWING THE EXECUTION OF SIDECART.TOS

## Step 7a. Select the ROM to Emulate from the microSD card

Upon starting the program, you'll be presented with a list of options showcasing the various capabilities of the SidecarT.

PLACEHOLDER FOR SIDECART.TOS IN THE CURRENT VERSION

Press '1' and hit Enter to choose the *Emulate ROM image from microSD card* option. The system will then display a list of ROM images you've copied to the microSD card in step 4.

Enter the number corresponding to the ROM image you wish to emulate and press Enter. The SidecarT will load the selected image, preparing it for execution on the computer's next startup or reset.

> Note: You know you're in ROM EMULATION mode when booting because the Raspberry Pi Pico W's LED will show a short blink; a 'E' in Morse code.

## Step 7b: Wi-Fi Configuration & ROM Emulation via HTTP Server

For those utilizing a SidecarT with a Raspberry Pi Pico W, you have the capability to connect to a Wi-Fi network and fetch the ROM image directly from an HTTP server. 

1. Initiate this by pressing '3' to access the *Wi-Fi configuration* menu.

PLACEHOLDER FOR SIDECART.TOS SHOWING THE WIFI CONFIGURATION

2. Once inside, scroll through the list of available networks. Confirm your desired network by pressing 'Enter'. If your chosen network is secure, you'll be prompted to input the password. After a successful connection, you'll be redirected to the main menu.

The connection status will then be displayed at the screen's base. Upon acquiring an IP address from the DHCP server, the SidecarT's IP address will be showcased. With this, a new menu option emerges: *Emulate ROM image from Wi-Fi*.

3. Activate this option by pressing '2'. The system will then present a list of ROM images available on the HTTP server. These ROM lists are stored within a `roms.json` file on the HTTP server. Should you wish to alter the server URL, navigate to option '4' for *SidecarT configuration*.

PLACEHOLDER FOR SIDECART.TOS SHOWING THE ROMS AVAILABLE IN THE HTTP SERVER

4. Scroll to your desired ROM image and confirm with 'Enter'. The system will handle the download and ready the ROM for execution on your next system startup or reset.


## Step 8. Boot the ROM

Now you can reset or power cycle your computer. Every time you reset or power cycle your computer, it will load the image as a genuine cartridge ROM.


## Extra bonus. Load a different ROM / Enter CONFIGURATOR mode again

If you want to reconfigure the SidecarT for a different feature or simply load a different ROM, there is a special button in the SidecarT board for it: the SELECT button.

PLACEHOLDER FOR AN IMAGE OF THE SELECT BUTTON

To launch the SidecarT in CONFIGURATOR mode again, simply push the SELECT button for more than a second, wait for the Raspberry Pi Pico W to blink the 'F' in morse code and reset or power cycle your computer. It will boot again in CONFIGURATOR mode like in step 6.
