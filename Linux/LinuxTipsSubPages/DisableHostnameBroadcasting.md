# Disable hostname broadcasting

To hide your hostname on a LAN in Linux, you have a few options:

1. Change the hostname to a generic name:
    
    Edit the `/etc/hostname` file and replace your current hostname with a generic one, then reboot your system[2](https://askubuntu.com/questions/58849/how-to-protect-a-computer-name-from-being-disclosed-to-network-peers).
    
2. Disable hostname broadcasting:
    
    Modify your network configuration to prevent broadcasting your hostname. This can be done by editing the `/etc/sysctl.conf` file and adding:
    
    `net.ipv4.conf.all.arp_ignore = 1
    net.ipv4.conf.all.arp_announce = 2`
    
    Then run `sudo sysctl -p` to apply the changes[5](https://security.stackexchange.com/questions/45689/how-to-prevent-other-hosts-on-the-same-lan-from-seeing-my-ip-and-host-name).
    
3. Use a firewall to block hostname queries:
    
    Configure your firewall (e.g., iptables or ufw) to block incoming requests for hostname information[5](https://security.stackexchange.com/questions/45689/how-to-prevent-other-hosts-on-the-same-lan-from-seeing-my-ip-and-host-name).
    
4. Disable mDNS (Multicast DNS):
    
    If you're using Avahi for mDNS, you can disable it by stopping the avahi-daemon service:
    
    `sudo systemctl stop avahi-daemon
    sudo systemctl disable avahi-daemon`
    
5. Modify DHCP client configuration:
    
    Edit your DHCP client configuration file (usually `/etc/dhcp/dhclient.conf`) to prevent sending the hostname to the DHCP server:
    
    `send host-name "";`
    

Keep in mind that completely hiding your hostname on a LAN can be challenging, as some network protocols rely on hostname information for proper functioning[1](https://stackoverflow.com/questions/23533407/how-to-hide-the-hostname-on-the-terminal-on-linux)[5](https://security.stackexchange.com/questions/45689/how-to-prevent-other-hosts-on-the-same-lan-from-seeing-my-ip-and-host-name). These methods will help reduce hostname visibility, but may not guarantee complete anonymity on the network.

### Citations:

1. [https://stackoverflow.com/questions/23533407/how-to-hide-the-hostname-on-the-terminal-on-linux](https://stackoverflow.com/questions/23533407/how-to-hide-the-hostname-on-the-terminal-on-linux)
2. [https://askubuntu.com/questions/58849/how-to-protect-a-computer-name-from-being-disclosed-to-network-peers](https://askubuntu.com/questions/58849/how-to-protect-a-computer-name-from-being-disclosed-to-network-peers)
3. [https://forums.virtualbox.org/viewtopic.php?t=66677](https://forums.virtualbox.org/viewtopic.php?t=66677)
4. [https://superuser.com/questions/328690/how-to-disable-disclosing-a-computer-name-to-a-network](https://superuser.com/questions/328690/how-to-disable-disclosing-a-computer-name-to-a-network)
5. [https://security.stackexchange.com/questions/45689/how-to-prevent-other-hosts-on-the-same-lan-from-seeing-my-ip-and-host-name](https://security.stackexchange.com/questions/45689/how-to-prevent-other-hosts-on-the-same-lan-from-seeing-my-ip-and-host-name)
6. [https://bbs.archlinux.org/viewtopic.php?id=292913](https://bbs.archlinux.org/viewtopic.php?id=292913)
7. [https://forums.linuxmint.com/viewtopic.php?t=282398](https://forums.linuxmint.com/viewtopic.php?t=282398)
8. [https://unix.stackexchange.com/questions/16890/how-to-make-a-machine-accessible-from-the-lan-using-its-hostname](https://unix.stackexchange.com/questions/16890/how-to-make-a-machine-accessible-from-the-lan-using-its-hostname)

---

Answer from Perplexity: [https://www.perplexity.ai/search/on-linux-how-to-hide-the-hostn-Exg8ak3VT4646T9pvFz6qA?utm_source=copy_output](https://www.perplexity.ai/search/on-linux-how-to-hide-the-hostn-Exg8ak3VT4646T9pvFz6qA?utm_source=copy_output)