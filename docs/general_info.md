# General Information Notes

### Transport Fever 2 Mods
Installation of Mods that are not available in the Steam Workshop:

* Local download Directory **/net/Dokumente/InstallFiles/TransportFever/**
* Directory for Mod installation under Steam **/data/SteamLibrary/steamapps/common/Transport Fever 2/mods**

### Mounting Android / iOS

* Android [MTP](https://wiki.archlinux.org/title/Media_Transfer_Protocol)

```aft-mtp-mount /media/android/```

* iOS [IOS (usbmuxd)](https://wiki.archlinux.org/title/IOS)

```ifuse /media/iphone/```

### Rebuild (g)mplayer
* mplayer-now wegsichern
* mplayer-now im mplayer-now Verzeichniss
* ```./configure --enable-gui```
* ```make clean```
* ```make```
* ```make install```

### MP3Gain Equalization

Created tga-mp3gain-norm to equalize all MP3s in a directory.

```bash
#!/bin/bash

find "$1" -type f -iname "*.mp3" -print0 | xargs -0 mp3gain -r -k
```






