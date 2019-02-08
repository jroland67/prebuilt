## AArch64 Laptop Prebuilt Images

These are the latest prebuilt images for your consumption.  There are currently 2 images available:

 * Complete prebuilt (configured) image
   * This image is **almost** (see below) ready for booting
 * Clean (not configured) Ubuntu Bionic image
   * This image is designed for the [Image Builder](https://github.com/aarch64-laptops/build) to consume

### Complete (configured) prebuilt image

This image is ready to be flashed onto an SD card to boot any one of the 3 devices currently supported by this project:

 * Asus NovaGo TP370QL
 * HP Envy x2
 * Lenovo Mixx 630

**IMPORTANT:** This image must be flashed using the [Flash Tool](https://github.com/aarch64-laptops/prebuilt/blob/master/flash-prebuilt.sh) provided by this repo.

If the [Flash Tool](https://github.com/aarch64-laptops/prebuilt/blob/master/flash-prebuilt.sh) is not used, the image will not boot.  If you find yourself in this situation you can do the following:

```
$ sudo mount /dev/<SD_CARD>2 <SDCARD_MOUNT_POINT>
$ ln -s /boot/<LAPTOP_DTB> <SDCARD_MOUNT_POINT>/boot/laptop.dtb
```

Where <LAPTOP_DTB> is either `laptop-asus-tp370ql.dtb` for the Asus NovaGo TP370QL or `laptop-hp-envy-x2.dtb` for HP Envy x2 and Lenovo Mixx 630

**Note:** Currently there are no known differences between the later 2 devices, so they use the same DTB.

Example:

```
$ sudo mount /dev/sda2 /mnt
$ ln -s /boot/laptop-asus-tp370ql.dtb /mnt/boot/laptop.dtb
```

**Note:** Obviously this will only work if your machine enumerated the SD card at `/dev/sda` and you wish to boot the Asus NovaGO TP370QL.

#### Flash Tool

To use the Flash Tool, do the following:

 1. Download the latest [Prebuilt Image](https://github.com/aarch64-laptops/prebuilt/raw/master/aarch64-laptops-bionic-prebuilt.img.xz) and make it executable
 2. Download the [Flash Tool](https://github.com/aarch64-laptops/prebuilt/blob/master/flash-prebuilt.sh)
 3. Use the [Flash Tool](https://github.com/aarch64-laptops/prebuilt/blob/master/flash-prebuilt.sh\
) to flash the latest [Prebuilt Image](https://github.com/aarch64-laptops/prebuilt/raw/master/aarch64-laptops-bionic-prebuilt.img.xz) onto the SD card

Example:

```
$ wget https://github.com/aarch64-laptops/prebuilt/raw/master/aarch64-laptops-bionic-prebuilt.img.xz
$ wget https://raw.githubusercontent.com/aarch64-laptops/prebuilt/master/flash-prebuilt.sh
$ chmod +x flash-prebuilt.sh
$ ./flash-prebuilt.sh asus-tp370ql /dev/sda
```

Once complete, place the SD card into your machine and boot.

If you need help with that see the [Booting into Ubuntu](https://github.com/aarch64-laptops/build#booting-into-ubuntu) section of the [Image Builder](https://github.com/aarch64-laptops/build) README.
 
### Clean (not configured) Ubuntu Bionic image

This image is consumed by the CI loop and by the [Image Builder](https://github.com/aarch64-laptops/build) when the [Quick Start Script](https://github.com/aarch64-laptops/build/blob/master/scripts/quick-start.sh) is used.

When used, it provides the following benefits:

1. The build can be completely unattended
2. Saves a great deal of time (2 hours) in the Ubuntu installer

**Note:** This image is not bootable on its own.
