# windows-boot
   brew install wimlib

    image_file=Win10_20H2_v2_English_x64.iso

    hdiutil mount ${image_file}

    # assuming USB is on /dev/disk2
    usb_disk=$(diskutil list | grep external | head -n 1 | awk '{print $1}')

    diskutil eraseDisk MS-DOS "WINDOWS10" MBR ${usb_disk}

    rsync -avh --progress --exclude=sources/install.wim /Volumes/DVD_ROM/ /Volumes/WINDOWS10

    wimlib-imagex split /Volumes/DVD_ROM/sources/install.wim /Volumes/WINDOWS10/sources/install.swm 3800

    hdiutil eject /Volumes/WINDOWS10

    hdiutil eject /Volumes/DVD_ROM

This requires the target Windows device to have UEFI boot options enabled (not legacy boot).
