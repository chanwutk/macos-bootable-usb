# A tutorial for creating a bootable usb in macOS

## 1. Prepare image file
We need to convert the iso file to dmg file (assuming the file is in the `~/Download`)
```
hdiutil convert -format UDRW -o ~/Download/path-to-output ~/Download/path-to-input.iso
```

## 2. Unmounting the USB Device
Then, we need to unmount the usb that will be used for creating bootable.

First, find the device number of the usb
```
diskutil list
```

Then, unmount the device (replace `N` with the device number)
```
diskutil unmountDisk /dev/diskN
```

## 3. Creating the bootable USB
run this command
```
sudo dd if=~/Download/path-to-output.dmg of=/dev/rdiskN bs=1m
```
