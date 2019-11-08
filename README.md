# Raspberry Pi 4 Bitcoin Full Node tutorial

![Raspi4](/raspi4.jpg)
A noob-friendly step-by-step guide for selecting the hardware, configuring and running a Raspberry Pi, and configuring and running a Bitcoin full node with a focus on setting it up with enhanced privacy. This is meant for people who have limited or no experience with a Linux/UNIX-style operating system. I do my best to explain what each command is doing and why we're doing it.

Each step is outlined in a short YouTube video. This format allows me to easily insert changes when needed and avoid onerous video editing. The master playlist is [here](https://www.youtube.com/playlist?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E).

This project can be completed in a couple of nights or over a weekend.

#### Comments, Questions, Suggestions
twitter: [@KeithMukai](https://twitter.com/KeithMukai)


## Introduction to the Hardware
* [Quick Intro](https://youtu.be/U0BmmDgqsv8?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Recommended hardware list](https://youtu.be/3L8BIlaAAqY?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
    * [Vilros Raspberry Pi 4 w/4GB RAM kit](https://amazon.com/dp/B07TKFKKMP/?ref=idea_lv_dp_ov_d)
    * Case w/fan
    * USB-C power supply
    * [Eletung](https://amazon.com/dp/B0716JKJ68/?ref=idea_lv_dp_ov_d) or [StarTech SATA-to-USB 3.0 adapter](https://amazon.com/StarTech-com-SATA-USB-Cable-USB3S2SAT3CB/dp/B00HJZJI84)
    * [Samsung 860 EVO 500GB](https://amazon.com/dp/B0781Z7Y3S/?ref=idea_lv_dp_ov_d) (or bigger) SSD
    * Any microSD card and microSD card adapter
* [Wiring the case fan](https://youtu.be/VRZSCTIRA1Y?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Wired vs wifi connection](https://youtu.be/4b0ZkfbLgv0?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Game Plan: Boot from the SSD](https://youtu.be/XLvmtmloBio?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Note: Must use a compatible SATA-to-USB 3.0 adapter](https://youtu.be/HR329oF6BKQ?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [SSD Selection](https://youtu.be/OWOn3xkVBUU?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [SD Card (non)Selection](https://youtu.be/TDSaxzgfP-E?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)


## Installing Raspbian OS
main resource: [James A Chambers blog: Raspberry Pi 4 USB Boot Config Guide for SSD / Flash Drives](https://jamesachambers.com/raspberry-pi-4-usb-boot-config-guide-for-ssd-flash-drives/)

* [Getting Started](https://youtu.be/B67hf0MSKic?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Selecting Raspbian Package](https://youtu.be/feB3pw39K6I?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Using an older Raspbian release](https://youtu.be/jnJ85bQtiME?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Verifying your download with SHA256 checksum](https://youtu.be/dco3M-XSMkQ?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Writing Raspbian to the SD card](https://youtu.be/S0_epUIO3dA?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Writing Raspbian to the SSD](https://youtu.be/lNpGxCYBuks?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Create empty "ssh" file](https://youtu.be/1-k-03l1sZE?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
    * Windows: from the terminal run `bash -c "touch ssh"`. And then copy the "ssh" file to the external drive called "boot".
* [Booting up the Pi](https://youtu.be/ARvkGilzRgk?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Following James A Chambers' procedure](https://youtu.be/VyEOR1YYFGU?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Connecting to the Pi: Intro to SSH](https://youtu.be/KCQPeMm2JT0?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
    * Default `pi` user's password: "raspberry".
    * Windows users: You can use cmd.exe or PowerShell. You'll probably need to omit the ".local".
        * Mac: `ssh pi@raspberrypi.local`
        * Win: `ssh pi@raspberrypi`
    * If the ssh command can't find the raspi, you may have to log in to your router to get the list of connected devices. Find the device named "raspberrypi" and ssh using the listed IP address (e.g. `ssh pi@192.168.1.103`).
* [Find the PARTUUID for the SD card and SSD](https://youtu.be/HmPs5fvL1Tk?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Edit /boot/cmdline.txt](https://youtu.be/QwxMJw_-_rU?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Explanation + safe reboot](https://youtu.be/-2cbG2kFebo?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [SSH warning](https://youtu.be/GRjrUyPqrl8?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
    * Windows users should consult [this info](https://superuser.com/questions/311886/where-is-the-known-hosts-file-for-openssh-for-windows)
* [Updating fstab](https://youtu.be/SBB2FDkIbek?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Resizing the filesystem for the SSD](https://youtu.be/zaYkxPisiO0?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [resize2fs on the SSD](https://youtu.be/XBZkDQBb5rQ?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Hardware setup wrapup](https://youtu.be/ch8gChu7zb4?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)


## Updating and Securing the Raspi
* [Change the default "pi" password](https://youtu.be/-psOHd3sy_w?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Create your own user](https://youtu.be/lmuroScbcKc?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Adding user to sudo group](https://youtu.be/5rNhLXbMJYU?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Update Raspbian, pt1](https://youtu.be/ePwC5cTZieQ?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Update Raspbian, pt2](https://youtu.be/_LUqyWzhEhs?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Update the Pi's firmware](https://youtu.be/zG5n6Phb6s8?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
    * see James A Chamber's blog: [Raspberry Pi 4 Bootloader Firmware Updating / Recovery Guide](https://jamesachambers.com/raspberry-pi-4-bootloader-firmware-updating-recovery-guide/)

## Installing Bitcoin Core
main resource: [Raspnode](https://raspnode.com/diyBitcoin.html#swap)
* [Enlarge swap file](https://youtu.be/WILuf8HDQpg?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Install Bitcoin dependencies, pt1](https://youtu.be/ajqnHlZ1--c?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Install Bitcoin dependencies, pt1](https://youtu.be/Dqg-824Cf88?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Building the Berkeley DB, pt1](https://youtu.be/cgp8kIMBMvQ?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Building the Berkeley DB, pt2](https://youtu.be/FgkbdeMT_mU?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Cloning the Bitcoin source code, setting up the compile](https://youtu.be/A8q5CXKoubU?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Compiling Bitcoin!](https://youtu.be/qNgH1II2el0?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Install Bitcoin](https://youtu.be/NHSudREYlXA?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Run bitcoind for the first time](https://youtu.be/fZKdxuE3oyU?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)


## Configuring Bitcoin
* [Create the bitcoin.conf file](https://youtu.be/RpYXzL9zVaQ?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
    * _note: The max dbcache might be 1024 so it's probably ignoring any value higher than that._
* [Install Supervisor](https://youtu.be/HLGVy8osd2M?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Configure Supervisor to manage bitcoind](https://youtu.be/2pgd9TcTnzo?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
    * UPDATE: no need to capture the stdout logs (what would normally get displayed in the terminal) as all that info is written to ~/.bitcoin/debug.log. So we just write stdout to "/null/dev" which purges it into the abyss.
    * UPDATE: the "-datadir=" is necessary. Without it bitcoind will look for the .bitcoin directory at "/.bitcoin" which would be at the disk root rather than within your user's "/home/youruser/" directory.
    * Configuration file (update `youruser` accordingly):
    ```
        [program:bitcoind]
        user=youruser
        command=bitcoind -datadir=/home/youruser/.bitcoin
        autostart=true
        autorestart=true
        stopwaitsecs=600
        stderr_logfile=/home/youruser/.bitcoin/err.log
        stdout_logfile=/dev/null
    ```

## Tor Integration
* [Install Tor](https://youtu.be/S6gvJTrg7OQ?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Configure Tor](https://youtu.be/VNl66lxUYPs?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Restart Tor service](https://youtu.be/zT_xxSQzLFw?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Adding user to Tor's debian-tor group](https://youtu.be/d9sOiqknCVg?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [bitcoind and outgoing connections through Tor](https://youtu.be/cBNYWaWBYX8?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
    * see: [Tor Support in Bitcoin](https://github.com/bitcoin/bitcoin/blob/master/doc/tor.md)
* [bitcoind and incoming connections from Tor](https://youtu.be/DJOovE24YOE?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Complete incoming/outgoing Tor settings](https://youtu.be/7bbiKuUSvfg?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Tor wrapup; update bitcoin.conf](https://youtu.be/1F3478RtntA?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)


## Misc
* [Recommended: set txindex=1](https://youtu.be/7kK5EppYkAE?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [txindex=1 follow-up](https://youtu.be/DQotss8jX1I?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Configure logrotate](https://youtu.be/gU3HEnT7tfg?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* [Rename your Pi's hostname](https://youtu.be/i49VBuiM5kw?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)
* Check the Pi's CPU and RAM load (no video yet)
    * Just run `htop`
* Check the Pi's temperature (no video yet)
    * Add the "video" group to your user (customize "youruser"): `sudo usermod -aG video youruser`
    * Get the current temperature: `vcgencmd measure_temp`
* [Expect "unexpected version" warning](https://youtu.be/qiABTP8yk0c?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)


## And we're done!
* [Checking disk space; wrap up](https://youtu.be/u89T7aaucOk?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E)



