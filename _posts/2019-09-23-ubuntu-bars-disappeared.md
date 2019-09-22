---
title: "How to recover when all bars disappeared on ubuntu desktop"
data: 2019-09-23 16:28:00 -0400
categories: ubuntu desktop
---
Unity-related problems.
I found solutions but first one didn't work for me.
Second one is as follows:
CTRL+ALT+F1 to launch a tty terminal because CTRL+ALT+t might not work.
```bash
sudo rm -rf ~/.cache/compizconfig-1
sudo rm -rf ~/.compiz
sudo rm -rf ~/.Xauthority
sudo dconf reset -f /org/compiz/
setsid unity
sudo reboot
```

