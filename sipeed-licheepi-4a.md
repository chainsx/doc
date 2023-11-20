### 1. Download u-boot files for Armbian

Download the u-boot file for the corresponding memory version of LicheePi 4A from the Action or Releases section of [chainsx/thead-u-boot](https://github.com/chainsx/thead-u-boot).

### 2. Flash u-boot to EMMC (required)

If there is a DIP switch, set it to EMMC mode. Press the BOOT button on the board and connect lpi4a to the computer using a data cable. Then perform the following operations:

```
sudo ./fastboot flash ram ./images/u-boot-with-spl.bin
sudo ./fastboot reboot
sleep 10
sudo ./fastboot flash uboot ./images/u-boot-with-spl.bin
```

For installation of drivers, refer to the [official Wiki](https://wiki.sipeed.com/hardware/zh/lichee/th1520/lpi4a/4_burn_image.html).

### 3. Flash the system

#### Option 1: Flash the system to an SD card

You can use Etcher or other software.

#### Option 2: Flash the system to EMMC

(1) Use the UMS (USB Mass Storage) feature of u-boot (experimental):

Interrupt the u-boot countdown by pressing `Ctrl^C` when counting down using the serial port to enter the u-boot command line, then enter the following command:
```
ums 0 mmc 0
```
The EMMC will be mapped as a USB Mass Storage device on the computer, and you can use Etcher or other software to flash it.

(2) After booting from the SD card, use the `dd` command to copy the Armbian image to the EMMC.
