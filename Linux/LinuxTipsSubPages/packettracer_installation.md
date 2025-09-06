Download the deb file from https://www.netacad.com/resources/lab-downloads

# Arch Linux installation

```bash
cd ~
sudo pacman -S git base-devel
git clone https://aur.archlinux.org/packettracer.git
mv Downloads/Packet_Tracer822_amd64_signed.deb packettracer
cd packettracer
makepkg -si
```

# Ubuntu installation

```bash
cd ~/Downloads
sudo apt update
sudo apt install gdebi
wget https://archive.ubuntu.com/ubuntu/pool/universe/m/mesa/libgl1-mesa-glx_23.0.4-0ubuntu1~22.04.1_amd64.deb
sudo gdebi libgl1-mesa-glx_23.0.4-0ubuntu1~22.04.1_amd64.deb 
sudo gdebi Packet_Tracer822_amd64_signed.deb
```
