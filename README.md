# Raspberry Pi 4 Bitcoin Full Node tutorial

A noob-friendly step-by-step guide for selecting the hardware, configuring and running a Raspberry Pi, and configuring and running a Bitcoin full node with a focus on setting it up with enhanced privacy. This is meant for people who have limited or no experience with a Linux/UNIX-style operating system. I do my best to explain what each command is doing and why we're doing it.

Each step is outlined in a short YouTube video. This format allows me to easily insert changes when needed and avoid onerous video editing. The master playlist is [here](https://www.youtube.com/playlist?list=PLoF4_lt35vblmnoEnLnb54mzI_zpleU7E).

#### Comments, Questions, Suggestions
twitter: [@KeithMukai](https://twitter.com/KeithMukai)


## Introduction to the Hardware
* [Quick Intro](https://youtu.be/U0BmmDgqsv8)
* [Recommended hardware list](https://youtu.be/3L8BIlaAAqY)
    * [Vilros Raspberry Pi 4 w/4GB RAM kit](https://amazon.com/dp/B07TKFKKMP/?ref=idea_lv_dp_ov_d)
    * Case w/fan
    * USB-C power supply
    * [Eletung](https://amazon.com/dp/B0716JKJ68/?ref=idea_lv_dp_ov_d) or [StarTech SATA-to-USB 3.0 adapter](https://amazon.com/StarTech-com-SATA-USB-Cable-USB3S2SAT3CB/dp/B00HJZJI84)
    * [Samsung 860 EVO 500GB](https://amazon.com/dp/B0781Z7Y3S/?ref=idea_lv_dp_ov_d) (or bigger) SSD
    * Any microSD card and microSD card adapter
* [Wiring the case fan](https://youtu.be/VRZSCTIRA1Y)
* [Wired vs wifi connection](https://youtu.be/4b0ZkfbLgv0)
* [Game Plan: Boot from the SSD](https://youtu.be/XLvmtmloBio)
* [Note: Must use a compatible SATA-to-USB 3.0 adapter](https://youtu.be/HR329oF6BKQ)
* [SSD Selection](https://youtu.be/OWOn3xkVBUU)
* [SD Card (non)Selection](https://youtu.be/TDSaxzgfP-E)


## Installing Raspbian OS
main resource: [James A Chambers blog: Raspberry Pi 4 USB Boot Config Guide for SSD / Flash Drives](https://jamesachambers.com/raspberry-pi-4-usb-boot-config-guide-for-ssd-flash-drives/)

* [Getting Started](https://youtu.be/B67hf0MSKic)
* [Selecting Raspbian Package](https://youtu.be/feB3pw39K6I)
* [Using an older Raspbian release](https://youtu.be/jnJ85bQtiME)
* [Verifying your download with SHA256 checksum](https://youtu.be/dco3M-XSMkQ)
* [Writing Raspbian to the SD card](https://youtu.be/S0_epUIO3dA)
* [Writing Raspbian to the SSD](https://youtu.be/lNpGxCYBuks)
* [Create empty "ssh" file](https://youtu.be/1-k-03l1sZE)
    * Windows: from the terminal run `bash -c "touch ssh"`. And then copy the "ssh" file to the external drive called "boot".
* [Booting up the Pi](https://youtu.be/ARvkGilzRgk)
* [Following James A Chambers' procedure](https://youtu.be/VyEOR1YYFGU)
* [Connecting to the Pi: Intro to SSH](https://youtu.be/KCQPeMm2JT0)
    * Default `pi` user's password: "raspberry".
    * Windows users: You can use cmd.exe or PowerShell. You'll probably need to omit the ".local".
        * Mac: `ssh pi@raspberrypi.local`
        * Win: `ssh pi@raspberrypi`
    * If the ssh command can't find the raspi, you may have to log in to your router to get the list of connected devices. Find the device named "raspberrypi" and ssh using the listed IP address (e.g. `ssh pi@192.168.1.103`).
* [Find the PARTUUID for the SD card and SSD](https://youtu.be/HmPs5fvL1Tk)
* [Edit /boot/cmdline.txt](https://youtu.be/QwxMJw_-_rU)
* [Explanation + safe reboot](https://youtu.be/-2cbG2kFebo)
* [SSH warning](https://youtu.be/GRjrUyPqrl8)
    * Windows users should consult [this info](https://superuser.com/questions/311886/where-is-the-known-hosts-file-for-openssh-for-windows)
* [Updating fstab](https://youtu.be/SBB2FDkIbek)
* [Resizing the filesystem for the SSD](https://youtu.be/zaYkxPisiO0)
* [resize2fs on the SSD](https://youtu.be/XBZkDQBb5rQ)
* [Hardware setup wrapup](https://youtu.be/ch8gChu7zb4)


## Updating and Securing the Raspi
* [Change the default "pi" password](https://youtu.be/-psOHd3sy_w)
* [Create your own user](https://youtu.be/lmuroScbcKc)
* [Adding user to sudo group](https://youtu.be/5rNhLXbMJYU)
* [Update Raspbian](https://youtu.be/ePwC5cTZieQ)
* [Update Raspbian, pt2](https://youtu.be/_LUqyWzhEhs)
* [Update the Pi's firmware](https://youtu.be/zG5n6Phb6s8)
    * see James A Chamber's blog: [Raspberry Pi 4 Bootloader Firmware Updating / Recovery Guide](https://jamesachambers.com/raspberry-pi-4-bootloader-firmware-updating-recovery-guide/)


## Installing Bitcoin Core
main resource: [Raspnode](https://raspnode.com/diyBitcoin.html#swap)
* [Enlarge swap file](https://youtu.be/WILuf8HDQpg)
* [Install Bitcoin dependencies, pt1](https://youtu.be/ajqnHlZ1--c)
* [Install Bitcoin dependencies, pt1](https://youtu.be/Dqg-824Cf88)
* [Building the Berkeley DB, pt1](https://youtu.be/cgp8kIMBMvQ)
* [Building the Berkeley DB, pt2](https://youtu.be/FgkbdeMT_mU)
* [Cloning the Bitcoin source code, setting up the compile](https://youtu.be/A8q5CXKoubU)
* [Compiling Bitcoin!](https://youtu.be/qNgH1II2el0)
* [Install Bitcoin](https://youtu.be/NHSudREYlXA)
* [Run bitcoind for the first time](https://youtu.be/fZKdxuE3oyU)


## Configuring Bitcoin
* [Create the bitcoin.conf file](https://youtu.be/RpYXzL9zVaQ)
    * _note: The max dbcache might be 1024 so it's probably ignoring any value higher than that._
* [Install Supervisor](https://youtu.be/HLGVy8osd2M)
* [Configure Supervisor to manage bitcoind](https://youtu.be/2pgd9TcTnzo)
    * Configuration file (update `youruser` accordingly):
    ```
        [program:bitcoind]
        user=youruser
        command=bitcoind -datadir=/home/youruser/.bitcoin
        autostart=true
        autorestart=true
        stopwaitsecs=600
        stderr_logfile=/home/youruser/.bitcoin/err.log
        stdout_logfile=/home/youruser/.bitcoin/out.log
    ```

## Tor Integration
* [Install Tor](https://youtu.be/S6gvJTrg7OQ)
* [Configure Tor](https://youtu.be/VNl66lxUYPs)
* [Restart Tor service](https://youtu.be/zT_xxSQzLFw)
* [Adding user to Tor's debian-tor group](https://youtu.be/d9sOiqknCVg)
* [bitcoind and outgoing connections through Tor](https://youtu.be/cBNYWaWBYX8)
    * see: [Tor Support in Bitcoin](https://github.com/bitcoin/bitcoin/blob/master/doc/tor.md)
* [bitcoind and incoming connections from Tor](https://youtu.be/DJOovE24YOE)
* [Complete incoming/outgoing Tor settings](https://youtu.be/7bbiKuUSvfg)
* [Tor wrapup; update bitcoin.conf](https://youtu.be/1F3478RtntA)


## Misc
* [Recommended: set txindex=1](https://youtu.be/7kK5EppYkAE)
* [txindex=1 follow-up](https://youtu.be/DQotss8jX1I)
* [Configure logrotate](https://youtu.be/gU3HEnT7tfg)
* [Rename your Pi's hostname](https://youtu.be/i49VBuiM5kw)
* [Expect "unexpected version" warning](https://youtu.be/qiABTP8yk0c)


## And we're done!
* [Checking disk space; wrap up](https://youtu.be/u89T7aaucOk)
