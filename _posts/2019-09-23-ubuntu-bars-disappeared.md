---
title: "How to recover when all bars disappeared on ubuntu desktop"
data: 2019-09-23 16:28:00 -0400
categories: ubuntu desktop
---

Unity-related problems.
I found solutions but first one didn't work for me.
Second one is as follows.

At first, CTRL+ALT+F1 to launch a tty terminal because CTRL+ALT+t would not work.
And run the following set of commands.
```bash
sudo rm -rf ~/.cache/compizconfig-1
sudo rm -rf ~/.compiz
sudo rm -rf ~/.Xauthority
sudo dconf reset -f /org/compiz/
setsid unity
sudo reboot
```
I refered to [this post][reference]
[reference]: https://www.faqforge.com/linux/ubuntu-sidebar-top-bar-disappeared-heres-can-bring-back

