# ArchInstallation

## connect to wifi
```
iwctl --passphrase passphrase station device connect SSID

```
## partions

````
cfdisk

mkfs.ext4 /dev/root_partition

mkswap /dev/swap_partition

mount /dev/root_partition /mnt

swapon /dev/swap_partition

````
## pacstraping
```
pacstrap /mnt base linux linux-firmware linux-header gurb dunst rofi i3-gaps gnome base-devel bbswitch code nvidia sudo polykit-gnome cpupower networkmanager network-manager-applet acpi jdk11-openjdk jdk8-openjdk im_sensors ttf-font-awesome ttf-fira-code picom gparted lxappearance feh neofetch weechat firefox chromium thunar lightdm lightdm-webkit2-greeter git ntfs-3g linux-lts grub-customizer os-prober inte-ucode efibootmgr dosfstools
```

## chroot

```
n -sf /usr/share/zoneinfo/India/Kolkata /etc/localtime

hwclock --systohc

nano /etc/locale.gen

uncomment en_US.UTF-8
locale-gen

echo LANG=en_US.UTF-8 > /etc/locale.conf
export LANG=en_US.UTF-8

echo arch >> /etc/hostname
nano /etc/hosts
127.0.0.1   localhost.localdomain   localhost 
::1         localhost.localdomain   localhost
127.0.1.1   arch.localdomain        arch 
```
>nano /etc/pacman.conf
>#->uncomment 
>[multilib]
>include = /etc/pacman.d/mirrorlis

## time to add user and do grub-install
```
passwd #for root
useradd -m -G wheel -s /bin/bash (user name)
passwd (username you created)

mkdir /boot/efi
mount /dev/sda1 /boot/efi (sda1 is here your efi/mbr partion which stores your bootloder)

grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=grub --recheck
grub-mkconfig -o boot/grub/grub.cfg

```

## you have finished installing arch 
```
#Enable required services
exit      # If still on arch-chroot mode
umount -R /mnt
reboot

```
