# windows-boot
diskutil list 
fat32 and UEFI boot on PC 
sudo diskutil unmountDisk /dev/disk2 
Unmount of all volumes on disk2 was successful 
sudo dd if=Win11_23H2_English_x64v2.iso of=/dev/disk2 bs=1m 
