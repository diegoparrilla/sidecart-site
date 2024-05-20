---
layout: post
title: "Hard disk emulation with SidecarT"
excerpt: "This week, I'm rolling out something that's going to make the SidecarT really cool: a new firmware update that slaps hard disk emulation right onto your beloved Atari ST..."
categories: [design, sidecart, software, firmware]
image: /assets/blog/images/sidecart-rev0-rev1-rev2.png
---

## A new feature for SidecarT: GEMDRIVE Hard Disk Emulator

This week, I'm rolling out something that's going to make the SidecarT really cool: a new firmware update that slaps hard disk emulation right onto your beloved Atari ST. That's right, we're going to turn that humble microSD card into a digital vault for all the bits and bytes you'd normally entrust to a clunky old hard disk. Sure, the Atari ST world isn't exactly short on hard disk solutions, but I wasn't content with just throwing another option into the mix. No, I aimed to deliver a feature that not only ticks all the boxes but also throws in a few extra goodies to keep things spicy for the SidecarT saga.

So, buckle up and let's dive into this digital delicacy, shall we?

[![SidecarT GEMDRIVE](/assets/blog/images/gemdrive-0.0.1.png)](/assets/blog/images/gemdrive-0.0.1.png){:.glightbox}

### Choosing Between Block Storage and File Storage

In developing the hard disk emulation for SidecarT, a pivotal choice presented itself: should the emulation function as a block storage device or a file storage system? Block storage devices operate by reading and writing data in predetermined block sizes, mirroring the functionality of traditional floppies and hard disks. This approach is widely recognized, with most people familiar with the concepts of partitions, sectors, and clusters associated with hard disks. To integrate block storage with SidecarT, it would necessitate crafting an interface for the RP2040 microcontroller and the cartridge interface to manage data blocks on the microSD card. Given the Atari ST's inherent support for block storage devices, this route seemed straightforward, requiring only the development of a driver and some additional code for integration.

However, I opted for a different path: file storage. Unlike block storage, file storage systems manage data through files, allowing the SidecarT firmware to interact with a file system on the microSD card. This is facilitated by the FatFS library, a renowned tool in embedded systems for navigating FAT file systems. The library simplifies file and directory operations, effectively abstracting the complexities of the FAT file system and its block storage underpinnings.

This decision was not without its challenges. The Atari ST is designed to support block storage natively, lacking direct hooks for file storage systems. This necessitated the creation of a file storage driver specifically for the Atari ST, requiring a hook into every GEM file access operation—a task significantly more complex than implementing a block storage driver. Despite these challenges, I believe this approach offers distinct advantages crucial for the SidecarT project's future, making it a worthwhile endeavor.

### The Case for File Storage

The pivotal decision to champion file storage over block storage within the SidecarT project stems from a compelling vision: to seamlessly integrate network drives with the Atari ST. Imagine the possibility of connecting the C: drive of an Atari ST directly to a remote NFS server, or even to cloud storage. This ambition to bridge local storage with networked resources is the driving force behind the preference for file storage. By mastering the intricacies of local file system access, we pave the way for implementing a network file system driver, enabling access to files on remote servers. This capability is not just an enhancement; it's a transformative feature that I envisioned for SidecarT from the outset. The logical first step towards this ambitious goal is to establish a robust local file system driver.

However, weaving every GEM file system function into the RP2040 firmware isn't exactly a walk in the park. It's a hefty task that goes way beyond just dealing with files. We're talking about managing directories, navigating drives and paths, and even getting executables to run smoothly. The Atari ST isn't making things easy either, with its rich set of functions throwing us curveballs left and right. So, where did I look for some much-needed wisdom? The realm of Atari ST emulators. These gems have been through the wringer, facing down similar challenges, and they're packed with insights and snippets of code that shine a light on the way forward. They've essentially laid out a map for us to follow, showing how to weave sophisticated file storage magic into the SidecarT.

### Leveraging Hatari's GEMDOS Drive Emulation Insights

Hatari, a renowned Atari ST emulator beloved by enthusiasts for running Atari ST software on contemporary hardware, features a sophisticated GEMDOS drive emulation layer. This layer facilitates direct access to the host's file system from Atari ST software, effectively bridging the gap between the emulator and native file system operations. The complexity of Hatari's approach, which seamlessly integrates every file system function of the Atari ST with the host file system, provided the perfect conceptual model for what I aimed to achieve with SidecarT.

However, the emulation advantages Hatari enjoys, such as direct hooks into the emulated 68000 CPU, underscored a significant challenge for implementing similar functionality in the SidecarT firmware. Unlike Hatari, which operates with complete control over the emulated Atari ST architecture, SidecarT interacts with actual Atari ST hardware, without the luxury of manipulating the hardware's inner workings to the same extent.

Fired up but not thrown off by Hatari's approach, I realized I had to chart my own course. Borrowing Hatari's code straight up just wasn't in the cards, which meant it was time to roll up my sleeves and build something tailor-made. This task had me diving deep into the RP2040 firmware, cooking up my own code to catch and redirect every file system call made by the Atari ST, all while making friends with the FatFS library to manage my microSD card dealings.

Kicking off this adventure was no picnic. It was a hefty, brain-twisting puzzle that stretched my skills and imagination in the best way possible. Tackling this challenge head-on not only tested my mettle but also turned out to be a heck of a fun ride, pushing the SidecarT into uncharted territories (Note: I learned that there is a GEMdriver implementation called ACS2STM for a hard disk driver).

[![Sidecart GEMDRIVE Configurator](/assets/blog/images/gemdrive-configurator.png)](/assets/blog/images/gemdrive-configurator.png){:.glightbox}


### Navigating GEMDOS Functions with SidecarT

The Atari ST's operating system offers a suite of GEMDOS functions accessible via the trap #1 interface, facilitating file system interactions. In my journey to integrate these capabilities into the SidecarT project, I delineated five distinct function groups:

1. **File Functions**: These include operations like open, close, read, write, seek, delete, rename, and adjusting file attributes and dates. They closely mirror the file access functions found in the C standard library, offering a familiar interface for file manipulation.
2. **Folder Functions**: Operations for creating, deleting, and renaming directories, essential for file system organization.
3. **Drive and Path Functions**: These functions manage the current working directory and drive, including getting and setting the current drive and path.
4. **Search Functions**: The find first and find next functions, crucial for navigating through files within a directory.
5. **Executable and Memory Functions**: Including loading and executing programs, and managing memory allocation and deallocation.

Implementing these functions within the RP2040 firmware to interface with the FatFS library was a complex yet fulfilling challenge. It allowed Atari ST software to interact with the microSD card for file operations, a significant achievement for the project.

For file functions, the primary challenge lay in managing file handles and converting date/time formats between the Atari ST and FatFS standards. Directory and path management (groups 2 and 3) proved more straightforward, thanks to similar interfaces between GEMDOS functions and the FatFS library.

The search functions (group 4) posed unique challenges, particularly in maintaining the state of directory searches due to FatFS's handling of search patterns, which required creative workarounds.

The crowning achievement of this whole saga was getting the executable functions, particularly the `Pexec` function, up and running. This little piece of programming magic, crucial for loading and running programs, comes with its own set of quirks. The usual `LOAD AND GO` routine, where you load a program into memory before kicking it into action, works pretty smoothly on TOS versions 1.04 and up. But making sure this played nice with the older TOS versions? That called for some real ingenuity to juggle memory ownership and keep the execution flow on track.

### The `Pexec` Function Variants

The `Pexec` function is pivotal for loading and executing programs on the Atari ST. It has several operational variants, with `LOAD AND GO` being the most common. This process involves loading the program with `Fopen` and `Fread` functions and executing it with a `JUST GO NEW FORM` variant of `Pexec`.

Getting things to work with TOS versions before 1.04 threw up its own set of hurdles. For TOS 1.00 and 1.02, I adapted the `LOAD AND GO` approach to ensure proper memory management and execution flow:

1. Load the program into memory using `Fopen` and `Fread`.
2. Initiate program execution with the `JUST GO` variant of `Pexec`, incorporating a crucial step that returns control to my code before the program launches.
3. Allocate the memory block for the loaded program.
4. Resume execution of the program.

This approach has been tested with multiple programs, showing promising results. However, the quest for perfection is ongoing, and I welcome insights from Atari ST aficionados to refine this process further.

### Making Friends with Classic Hard Disk Drivers

Navigating the waters of classic Atari ST computing means dealing with hard disk drivers that are all about block storage. This backdrop sets the stage for my GEMDOS file system hooks to mingle with the old guard without stepping on any toes. It's crucial that these different storage solutions can pass notes without causing a fuss, especially when it comes to moving data around. My hands-on time with the UltraSatan device and the PPutnik driver, playing nice with the GEMDRIVE, has been a win, showing off smooth file transfers back and forth. I even brought [KOBOLD](https://www.atarimania.com/pgesoft.awp?version=28184) into the mix for file shuffling, which worked like a charm.

[![UltraSatan Kobold GEMDRIVE](/assets/blog/images/kobold-copy.png)](/assets/blog/images/kobold-copy.png){:.glightbox}


### Game On with PPera Hard Disk Games

Diving into the world of PPera hard disk games supporting HAGA and HAGE drivers with the GEMDRIVE has been a blast. These games, which you can snag from the [Atari ST Adapted Games](https://atari.8bitchip.info/fromhd3.php) site, are a perfect match for the GEMDRIVE, playing nice across a spectrum of TOS versions from the vintage 1.00 to the more sprightly 2.06, as long as you've got at least 1MB RAM to play with. Most of these games run without issues for HAGA and HAGE, though there are a couple that seem to be playing hard to get, hinting at some deeper mysteries of compatibility yet to be unraveled.

### A Friendly Nod to Older TOS Versions

What's really turned heads is how well the GEMDRIVE gets along with the elder statesmen of the TOS world, versions 1.00 and 1.02. This harmony is more than just a technical triumph; it's a beacon of hope for Atari ST aficionados clinging to these classic systems. With the GEMDRIVE, they're not just dusting off old hardware; they're loading and executing programs straight from a microSD card, giving their vintage machines a new lease on life.

### Dodging the Bad-DMA Bullet

Then there's the cherry on top: SidecarT's built-in shield against the infamous Bad-DMA gremlin. This bugbear, born from the original DMA controller's less-than-perfect design, has been the bane of certain Atari ST models, corrupting data when you least expect it. But thanks to SidecarT's bypassing of the DMA controller, opting instead for a direct line through the cartridge slot and into the capable hands of an RP2040 microcontroller, this issue is left in the dust. This isn't just a workaround; it's a game-changer, ensuring data stays pristine and Atari STs affected by Bad-DMA can march into the future, unencumbered by the ghosts of their past.

### Wrapping Up

Navigating the complexities of hard disk emulation with the SidecarT has been nothing short of an adventure. Opting for file storage over block storage wasn't just a technical decision; it was a necessary evil, setting the stage for groundbreaking enhancements like linking the Atari ST with network and cloud storage solutions.

The SidecarT's knack for bypassing the notorious Bad-DMA issue, coupled with its compatibility across various TOS versions, particularly 1.00 and 1.02, doesn't just boost data integrity and reliability—it breathes new life into vintage machines. This makes SidecarT not just an upgrade but a transformational tool for Atari ST aficionados.

But this is merely the beginning. With the groundwork for network connectivity laid and our commitment to refining emulation techniques, the horizon for the SidecarT project looks dazzlingly bright. The journey ahead promises to be filled with challenges and triumphs, as we continue to push the boundaries of Atari ST innovation.

Got a spark of an idea or a suggestion? Hop into our [Discord server](https://discord.com/invite/u73QP9MEYC) and let's chat. It's in these collaborations that SidecarT will continue to evolve, adhering to our core values of simplicity, affordability, and a solderless, backward-compatible design. Let's keep the spirit of Atari ST innovation alive, together.