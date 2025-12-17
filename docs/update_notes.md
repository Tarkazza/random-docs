# Update Workarounds
Some stuff I stumbled over while updating lately.

### Grub Reinstall
In the current setup, where I still boot via traditional BIOS, not UEFI.
```bash
grub-install --target=i386-pc /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg
```

### 2025-04-16 OBS Virtual Camera Broken [SOLVED]

* OBS 31.0.3 virtual camera was still **broken** with v4l2loopback-dkms-0.14.
* OBS 32.0.1 virtual camera now **works** with v4l2loopback-dkms 0.15.2.

So the following is no longer relevant.

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

### 2025-11-08 LXPanel Tooltips

LXPanel Tooltips are broken because of GTK Bug.

Bug open on Gnome.org for months so far. 

[Github Bug Tracker](https://gitlab.gnome.org/GNOME/gtk/-/merge_requests/8216)

### 2025-12-01 Discord Crash and Green Stream

Discord Crashed during streaming, and Stream get's sent as green artifact-soup.
[Arch Forum Thread](https://bbs.archlinux.org/viewtopic.php?id=310039)

Crash itself was Fixed by Mesa project ~2025-12-10, Discord problem still there.

[Freedesktop Bug](https://gitlab.freedesktop.org/mesa/mesa/-/issues/14270)




