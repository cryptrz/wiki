# Linux Mint install

To install Sonic Pi on Linux Mint, follow these detailed steps to ensure a successful setup:

## Prerequisites

1. **Update your system**: Make sure your package list is up to date.
    
    ```bash
    sudo apt update && sudo apt upgrade
    
    ```
    
2. **Install required packages**: You may need to install additional dependencies. Use the following command:
    
    ```bash
    sudo apt install git qt6-base-dev libtool python3-pip
    
    ```
    

## Installation Steps

1. **Clone the Sonic Pi repository**:
    
    ```bash
    git clone <https://github.com/sonic-pi-net/sonic-pi.git> ~/Development/sonic-pi
    
    ```
    
2. **Navigate to the application folder**:
    
    ```bash
    cd ~/Development/sonic-pi/app
    
    ```
    
3. **Run the prebuild script**: This script checks for any issues before building.
    
    ```bash
    ./linux-prebuild.sh
    
    ```
    
4. **If the prebuild completes successfully, run the full build**:
    
    ```bash
    ./linux-build-all.sh
    
    ```
    
5. **Run Sonic Pi**: After the build completes, you can start Sonic Pi with:
    
    ```bash
    ~/Development/sonic-pi/bin/sonic-pi
    
    ```
    

## Audio Configuration

- **Audio Group Membership**: Ensure that your user is part of the `audio` group to access sound devices properly. You may need to log out and back in or reboot your system for changes to take effect.
- **PipeWire vs PulseAudio**: If you encounter sound issues, consider switching from PulseAudio to PipeWire, as some users have reported better compatibility with Sonic Pi when using PipeWire[1].

## Troubleshooting

- If Sonic Pi does not start or hangs on the splash screen, check for any missing dependencies or configuration issues related to audio servers like JACK or PulseAudio[3][4].
- Ensure that you have installed `qpwgraph` from Flatpak if needed, as some packages may not be available directly in Mint's repositories[1].

By following these steps, you should be able to successfully install and run Sonic Pi on Linux Mint.

Citations:
[1] [https://github.com/sonic-pi-net/sonic-pi/issues/3396](https://github.com/sonic-pi-net/sonic-pi/issues/3396)
[2] [https://www.youtube.com/watch?v=Tg2L5SdzB5Q](https://www.youtube.com/watch?v=Tg2L5SdzB5Q)
[3] [https://in-thread.sonic-pi.net/t/sonicpi-linux-mint-20-not-starting-up/5251](https://in-thread.sonic-pi.net/t/sonicpi-linux-mint-20-not-starting-up/5251)
[4] [https://linuxmusicians.com/viewtopic.php?t=20753](https://linuxmusicians.com/viewtopic.php?t=20753)
[5] [https://community.linuxmint.com/software/view/sonic-pi](https://community.linuxmint.com/software/view/sonic-pi)
[6] [https://forums.linuxmint.com/viewtopic.php?t=305546](https://forums.linuxmint.com/viewtopic.php?t=305546)
[7] [https://flathub.org/apps/net.sonic_pi.SonicPi](https://flathub.org/apps/net.sonic_pi.SonicPi)
[8] [https://github.com/sonic-pi-net/sonic-pi/issues/3259](https://github.com/sonic-pi-net/sonic-pi/issues/3259)