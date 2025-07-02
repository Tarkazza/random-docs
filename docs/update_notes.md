# Update Workarounds
Some stuff I stumbled over while updating lately.

### Grub Reinstall
In the current setup, where I still boot via traditional BIOS, not UEFI.
```bash
grub-install --target=i386-pc /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg
```

### 2025-04-16 OBS Virtual Camera Broken
OBS 31.0.3 virtual camera still breaks with v4l2loopback-dkms-0.14.

Description of Problem in [OBS Forum](https://obsproject.com/forum/threads/obs-virtual-camera-failed-to-start-streaming-on-dev-video2-invalid-argument.184717/)

Open Bug in [Github Bug Tracker](https://github.com/ublue-os/akmods/issues/328)

Temporary solution, downgraded to the last available packages in the local pacman cache for now.

```bash
# select version 0.13.2-1 for both of these:
pacman -U /var/cache/pacman/pkg/v4l2loopback-dkms-0.13.2-1-any.pkg.tar.zst
pacman -U /var/cache/pacman/pkg/v4l-utils-1.28.1-2-x86_64.pkg.tar.zst

#refresh the module (or you could just reboot and skip these two commands)
rmmod -f v4l2loopback
modprobe v4l2loopback
```

### Transport Fever 2 Mods
Installation of Mods that are not available in the Steam Workshop:

* Local download Directory **/net/Dokumente/InstallFiles/TransportFever/**
* Directory for Mod installation under Steam **/data/SteamLibrary/steamapps/common/Transport Fever 2/mods**


