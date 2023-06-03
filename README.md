# A tutorial for creating a bootable usb in macOS

## 1. Prepare the image file
We need to convert the iso file to dmg file (assuming the file is in the `~/Download`)
```bash
hdiutil convert -format UDRW -o ~/Downloads/path-to-output ~/Downloads/path-to-input.iso
```
```bash
# if output == 'output-install-os.dmg'
hdiutil convert -format UDRW -o ~/Downloads/output-install-os ~/Downloads/os.iso
```

## 2. Unmounting the USB Device
Then, we need to unmount the usb that will be used for creating bootable.

First, find the device number of the usb
```bash
diskutil list
```

Then, unmount the device (replace `N` with the device number)
```bash
diskutil unmountDisk /dev/diskN
```
```bash
# if N == 2:
diskutil unmountDisk /dev/disk2
```

## 3. Creating the bootable USB
run this command
```bash
sudo dd bs=1m of=/dev/rdiskN if=~/Downloads/path-to-output.dmg
```
```bash
# if N == 2 and output == 'output-install-os.dmg':
sudo dd bs=1m of=/dev/rdisk2 if=~/Downloads/output-install-os.dmg
```
