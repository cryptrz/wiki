# Brightness Controller installatation on Fedora

| Step | Command |
| --- | --- |
| Install dependencies | `sudo dnf install ddcutil xrandr python3-pip python3-qt5` |
| Install via pip | `pip3 install brightness-controller-linux` |
| Run the program | `brightness-controller-linux` |

**Notes and Troubleshooting:**

- Brightness Controller works by adjusting color profiles using `xrandr`, so it may not function under Wayland sessions or with some hardware configurations:
  - https://github.com/LordAmit/Brightness.

- For systems where Brightness Controller does not work, alternatives like `brightnessctl` or `light` are available in Fedora’s repositories and can be installed with `sudo dnf install brightnessctl` or `sudo dnf install light`:
  - https://discussion.fedoraproject.org/t/no-screen-brightness-problems-in-fedora/112737
  - https://discussion.fedoraproject.org/t/brightness-control-on-fedora-41/143730
  - https://forums.fedoraforum.org/showthread.php?332177-Fedora-Budgie-Brightness-control
  
- If you are using an external monitor, consider using `ddcutil` directly for hardware-level brightness control:
  - https://www.reddit.com/r/Fedora/comments/qx9dvj/complete_noob_here_uhhh_where_is_the_brightness/
  - https://github.com/LordAmit/Brightness

