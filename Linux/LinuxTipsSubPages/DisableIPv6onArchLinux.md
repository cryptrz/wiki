### To disable IPv6 on Arch Linux:

1. **Temporarily (until reboot):**
   ```bash
   sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1
   sudo sysctl -w net.ipv6.conf.default.disable_ipv6=1
   ```
2. **Persistently (across reboots):**
   Add the following lines to `/etc/sysctl.d/99-disable-ipv6.conf`:
   ```
   net.ipv6.conf.all.disable_ipv6 = 1
   net.ipv6.conf.default.disable_ipv6 = 1
   ```
   Then run:
   ```bash
   sudo sysctl --system
   ```

3. **GRUB method (alternative):**
   Add to your `/etc/default/grub`, line `GRUB_CMDLINE_LINUX_DEFAULT`, append:
   ```
   ipv6.disable=1
   ```
   Then:
   ```bash
   sudo grub-mkconfig -o /boot/grub/grub.cfg
   sudo reboot
   ```
