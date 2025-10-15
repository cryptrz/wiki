# Install LUKS manually

Install cryptsetup-luks. (You can issue `apt install cryptsetup`, `yum install cryptsetup-luks` or `dnf install cryptsetup-luks` for Ubuntu/Debian, RHEL/Cent OS, and Fedora, respectively.)
Confirm the partition name using `fdisk -l`, `lsblk` or `blkid`. (Create a partition using fdisk if necessary.)
Set up the partition for LUKS encryption: `cryptsetup -y -v luksFormat /dev/sdb1`. (Replace /dev/sdb1 with the partition name you want to encrypt.)
Create a mapping to access the partition: `cryptsetup luksOpen /dev/sdb1 EDCdrive`.
Confirm mapping details: `ls -l /dev/mapper/EDCdrive and cryptsetup -v status EDCdrive`.
Overwrite existing data with zero: `dd if=/dev/zero of=/dev/mapper/EDCdrive`.
Format the partition: `mkfs.ext4 /dev/mapper/EDCdrive -L "Strategos USB"`.
Mount it and start using it like a usual partition: `mount /dev/mapper/EDCdrive /media/secure-USB`.
