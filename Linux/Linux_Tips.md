### Linux Directory Structure
https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/

# Tips

## Anbox (Android VM)

**Install Anbox on Fedora**: https://www.linuxadictos.com/en/instala-y-ejecutar-aplicaciones-de-android-con-anbox-en-fedora-30.html 

## apt

When it’s not possible to install a deb file directly with apt (`apt install ./file.deb`), create this:

```bash
 #!/bin/bash
 
# Save this script as "inst" and make it executable. 
# Then copy it into /usr/local/bin/

if [ "$#" -ne 1 ]; then
    echo "Usage: $0 <path-to-deb-file>"
    exit 1
fi

sudo apt install ./"$1"
```

## Arch Linux

- Arch Cheat Sheet: https://github.com/Stickano/ArchCheatSheet
- Automated install: https://www.debugpoint.com/archinstall-guide
- Blackarch on Arch: https://philosophos.github.io/articles/20170305~Installing-BlackArch-on-top-of-ArchLinux/
- Bluetooth install: https://www.jeremymorgan.com/tutorials/linux/how-to-bluetooth-arch-linux
- Dababase locked: https://wiki.archlinux.org/title/pacman#%22Failed_to_init_transaction_(unable_to_lock_database)%22_error
- Devel packages: `sudo pacman -S --needed base-devel`
- iwctl (command line wifi management): https://man.archlinux.org/man/community/iwd/iwctl.1.en
- key init: https://bbs.archlinux.org/viewtopic.php?id=143337
- Pamac install: https://www.fossmint.com/pamac-arch-linux-gui-package-manager
- KVM/Virt-Manager install: https://computingforgeeks.com/install-kvm-qemu-virt-manager-arch-manjar
- Yay install: https://www.makeuseof.com/install-and-use-yay-arch-linux
## Aureport:

https://linux.die.net/man/8/aureport)

- **Successful logins**: `ausearch --message USER_LOGIN --success yes --interpret`
- **Failed logins**: `ausearch --message USER_LOGIN --success no --interpret`
    - `-message` is followed by the message we are interested in searching for. Examples include `USER_LOGIN`, `DEL_USER`, `ADD_GROUP`, `USER_CHAUTHTOK`, `DEL_GROUP`, `CHGRP_ID`, `ROLE_ASSIGN`, and `ROLE_REMOVE`.
    - `-success` is followed by `yes` or `no` depending on whether you are searching for successful or unsuccessful attempts, respectively.
    - `-interpret` converts numeric entities, such as UID (User ID), into text.
    
    Successful logins: `ausearch --message USER_LOGIN --success yes --interpret | grep ct=root`
    
    Failed logins: `ausearch --message USER_LOGIN --success no --interpret | grep ct=root`
    

## Cache

- Clear cache:
    
    **1.** Clear PageCache only. `sync; echo 1 > /proc/sys/vm/drop_caches`
    
    **2.** Clear dentries and inodes. `sync; echo 2 > /proc/sys/vm/drop_caches`
    
    **3.** Clear pagecache, dentries, and inodes. `sync; echo 3 > /proc/sys/vm/drop_caches`

## ClamAV

[ClamAV installation and setup on Debian/Ubuntu](LinuxTipsSubPages/ClamAV-on-Debian-based.md)
    

## CRON

-  https://help.ubuntu.com/community/CronHowto


## Disk quota

[Configuration](LinuxTipsSubPages/DiskQuotaConfiguration.md)

## DNS

- Permanently change DNS on Ubuntu and Debian: https://www.tecmint.com/set-permanent-dns-nameservers-in-ubuntu-debian/

## Firewalld

- Add an open port

```bash
firewall-cmd --zone=public --add-port=2237/tcp
```

## Flameshot

- Command for shortcut: `/usr/bin/flameshot gui`

## Files

- https://www.networkworld.com/article/968831/5-ways-to-examine-the-content-of-files-on-linux.html
- https://opensource.com/article/20/4/linux-binary-analysis

## Find

[SUID vs SGID](LinuxTipsSubPages/SUIDvsSGID%201653fdfbfae88025bfc0ec15e9450e99.md)

## Gnome

- **Touchpad 3 fingers with Xorg/X11**: https://itsfoss.com/three-finger-swipe-gnome

## Hostname

[Disable hostname broadcasting](LinuxTipsSubPages/DisableHostnameBroadcasting.md)

## **i3**

- **Touchpad “Tap to click” + “Natural screen”:**
    - Copy/paste all of this in the terminal:
    
    ```bash
    sudo mkdir -p /etc/X11/xorg.conf.d && sudo tee <<'EOF' /etc/X11/xorg.conf.d/90-touchpad.conf 1> /dev/null
    Section "InputClass"
            Identifier "touchpad"
            MatchIsTouchpad "on"
            Driver "libinput"
            Option "Tapping" "on"
    EndSection
    
    EOF
    ```
    

## ip

- [ifconfig vs ip](https://www.tecmint.com/ifconfig-vs-ip-command-comparing-network-configuration/)

## iptables

 - [Template](LinuxTipsSubPages/iptables-template.md)

## **John Jumbo**

- **Manual install:**
    - Before following [this steps](https://github.com/openwall/john/blob/bleeding-jumbo/doc/INSTALL), install this:
    - `sudo apt install build-essential libssl-dev yasm libgmp-dev libpcap-dev libnss3-dev libkrb5-dev pkg-config libbz2-dev zlib1g-dev`
    - For NVIDIA support: `sudo apt install nvidia-cuda-toolkit nvidia-opencl-dev`
    - For AMD support: `sudo apt install fglrx-updates-dev`

[Jq (Command-line Json processor)](https://manpages.org/jq)

## Keyboard

- **CLI layout command ***(exemple for US International Dead Keys)***:**
    
    `setxkbmap -layout us -variant intl`
    

## Kali Linux

- **apt update and upgrade not working**: https://forums.kali.org/showthread.php?70575-Apt-update-and-upgrade-commands-not-working

    - `echo "deb [http://http.kali.org/kali](http://http.kali.org/kali)
     kali-last-snapshot main contrib non-free" | sudo tee /etc/apt/sources.list`

## KVM

- **Enable copy-paste on guest** *(already enabled automatically on host)***:**
    - `sudo apt install spice-guest-tools spice-vdagent`
    - Check if network is active: `sudo virsh net-start default`
    - If network is not active: `sudo virsh net-start default`
    - Enable network auto-start: `sudo virsh net-autostart default`
- **Import OVA:**
    - Extract the files: `tar xvf <image_name>.ova`
    - Coonvert System.vmdk to qcow2: `qemu-img convert -O qcow2 <image_name>.vmdk /path/to/folder/OL7U2.qcow2`
- **Enable Bridge Adapter:**
    - https://computingforgeeks.com/how-to-create-and-configure-bridge-networking-for-kvm-in-linux
    
- **Convert .ova to qcow2:**
    1. `tar xvf MyAppliance.ova`
    2. `qemu-img convert -O qcow2 extractedFile.vmdk newFile.qcow2`

## Loopback

[Definition](LinuxTipsSubPages/DefinitionLoopback.md) 

## Mail

[From localhost to external](LinuxTipsSubPages/MailFromLocalhostToExternal.md)   

## Memory

- To empty the memory buffer and cache, execute the following command,

```bash
free && sync && echo 3 > /proc/sys/vm/drop_caches && free
```

## Modprobe

- Error: could not insert ‘vboxdrv’: Operation not permitted: https://crazytechgo.com/modprobe-error-could-not-insert-vboxdrv-operation-not-permitted

## MSFVenom

[Cheat Sheet](LinuxTipsSubPages/MSFVenomCheatSheet.md)

## NVIDIA drivers on Debian

- [How to Install Nvidia Drivers on Debian 12 or 11](https://linuxcapable.com/install-nvidia-drivers-on-debian/) 

## NTP update

`sudo ntpdate [pool.ntp.org](http://pool.ntp.org/)`

## Ports

- Check open ports: `sudo netstat -tulpn | grep LISTEN`

## Python

- **Manual install:**
    - `sudo apt install build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev curl`
    - `tar -xf Python-3.?.?.tar.xz`
    - `cd Python-3.*`
    - `./configure`
    - `sudo make install`

- Externally Managed Environment error
    - `pip3 install XXXXX **--break-system-packages**`

## Raspberry Pi OS

- **Under voltage alert:**
    - `sudo vim /boot/config.txt` and add this: `avoid_warnings=1`

- **WiFi manual settings:**
    - Create the file ***wpa_supplicant.conf*** in the root of the /boot partition (adapt **ssid** and **psk**):

```bash
country=RO
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
ssid=**<NETWORK NAME>**
scan_ssid=1
psk=**<PASSWORD>**
key-mgmt=WPA-PSK
}
```

## RedShift

[config](Tips%20043ecd625f2a4c53ae9b35c04325ed7b/config%2019b3fdfbfae880afa621fb44a06b10ba.md)

## rpm command

- List installed packages: https://linoxide.com/list-installed-packages-fedora

## Rustdesk

[Install Rustdesk on Debian/Ubuntu](LinuxTipsSubPages/install-rustdesk-server.md)

## Sandboxing

- https://manpages.ubuntu.com/manpages/noble/man1/subuser.1.html
- https://www.man7.org/linux/man-pages/man1/Firejail.1.html

## SELinux

- Change default port (example for SSH from 22 to 2237)

```bash
semanage port -a -t ssh_port_t -p tcp 2237
semanage port -l | grep ssh
systemctl restart sshd.service
```

## SSH

- [SSH command usage, options, and configuration in Linux/Unix](https://www.ssh.com/academy/ssh/command)

[SSH permissions](LinuxTipsSubPages/SSHPermissions.md) 

## Sonic Pi

[Linux Mint install](LinuxTipsSubPages/SonicPiLinuxMintInstall.md) 

## sudo

- sudoers editor: [visudo](https://www.man7.org/linux/man-pages/man8/visudo.8.html)
- Sudo replacement: [pbrun](https://www.beyondtrust.com/docs/privilege-management/unix-linux/admin/administration-programs/pbrun.htm)

## Terminal

- Tilix error: https://gnunn1.github.io/tilix-web/manual/vteconfig

## Tor unofficial downloads (multiple architectures)

- https://sourceforge.net/projects/tor-browser-ports/files

## Tor Website

#### **TOR:**

`sudo apt install tor`

`sudo nano /etc/tor/torrc`

**Uncomment this 2 lines:**

`HiddenServiceDir /var/lib/tor/hidden_service/`

`HiddenServicePort 80 127.0.0.1:80`

#### **RPi OS:**

`sudo service tor stop`

`sudo service tor start`

`sudo service tor status`

#### **Fedora:**

`sudo systemctl start tor`

`sudo systemctl status tor`

**Check the website URL:**

`sudo cat /var/lib/tor/hidden_service/hostname` (RPi OS)

`sudo cat /var/lib/tor/other_hidden_service/hostname` (Fedora)

### **NGINX:**

**RPi OS:**

`sudo apt install nginx`

`sudo service nginx start`

`sudo service nginx status`

**Fedora:**

`sudo systemctl start nginx`

`sudo systemctl status nginx`

- ------------------------------------(RPi OS only)----------------------------
    
    `sudo nano /etc/nginx/nginx.conf`
    
    **Uncomment:**
    
    `server_tokens off;`
    
    `server_name_in_redirect off;`
    
    **Add this line:**
    
    `port_in_redirect off;`
    
    `sudo service nginx restart` (RPi OS)
    
    `sudo systemctl restart nginx`
    
- --------------------------------------------------------------------------------------------

`cd /var/www/html/` **(RPi)**

`cd /usr/share/nginx/html/` **(Fedora)**

`sudo rm index.nginx-debian.html` **(RPi)**

`sudo rm index.html` **(Fedora)**

`sudo nano index.php`

**Add some HTML code, a "hello world" or something: <html>(...)</html>**

`sudo service restart nginx`

**Copy/paste the onion URL in Tor  browser and check the website**

PHP install: [How to Install PHP on Raspberry Pi with NGINX (themoderncoder.com)](https://www.themoderncoder.com/install-php-on-raspberry-pi-with-nginx/) 

## TLP for Fedora

- https://linrunner.de/tlp/installation/fedora.html

## URL encode

- https://www.urlencoder.net/linux-urlencode

`sudo apt-get install gridsite-clients`

Example: `urlencode "http://example.com/?param=linux+url+encoder"`

Output: `http%3A%2F%2Fexample.com%2F%3Fparam%3Dlinux%2Burl%2Bencoder`

## Users

- https://www.man7.org/linux/man-pages/man5/nologin.5.html
- [Managing_Smart_Cards/Pluggable_Authentication_Modules](https://docs.redhat.com/en/documentation/Red_Hat_Enterprise_Linux/6/html/Managing_Smart_Cards/Pluggable_Authentication_Modules.html)

## VirtualBox

- [USB not recognized](https://askubuntu.com/questions/140081/virtualbox-doesnt-recognize-usb)

## VNC

[Kali and Ubuntu/Mint](Tips%20043ecd625f2a4c53ae9b35c04325ed7b/Kali%20and%20Ubuntu%20Mint%201a83fdfbfae880fc8201c55caa2305ba.md)

## **WiFi**

**Command-line connexion:**

- Find the networkds around: `nmcli dev wifi`
- Connect to a network: `nmcli dev wifi connect <SSID>`

**Driver install for AC1300 USB adapter (option 2, works for Kali/Debian-based and Fedora):**

- https://github.com/morrownr/88x2bu-20210702

**Driver install for AC1300 USB adapter (option 3):**

- https://www.tp-link.com/us/support/download/archer-t4u/#Driver

**Driver install for AWUS1900 on Kali:** 

- https://www.briansantacruz.me/2019/07/27/how-to-install-alfa-awus1900-on-kali-linux

**Driver install for AC600 USB adapter:**

- https://github.com/nlkguy/archer-t2u-plus-linux

- https://github.com/aircrack-ng/rtl8812au

## Wine

[Double-click .exe files ](LinuxTipsSubPages/Double-click-exe-files.md)

## WoeUSB

- https://linuxhaxor.net/code/install-woeusb-linux-mint.html
- https://www.linuxuprising.com/2020/10/how-to-make-bootable-windows-10-usb-on.html

## WSL

- Jekyll: https://medium.com/@hjgraca/using-wsl2-visual-studio-code-for-jekyll-blogging-on-windows-10-99489deb4650
