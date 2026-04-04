# OpenNMS installation script for Debian and Ubuntu

https://github.com/opennms-forge/opennms-install

# Add an Ubuntu server

### Step 1: Install SNMP

In Ubuntu, install SNMP:

`sudo apt install snmp snmpd snmp-mibs-downloader`

There are two files that look nearly identical:

- `/etc/snmp/snmp.conf`: This is for the **client** (the `snmpwalk` tool). It doesn't understand "agentAddress" or "rocommunity".
- `/etc/snmp/snmpd.conf`: (Note the **'d'**) This is for the **daemon** (the background service). This is where your settings belong.

---

### Step 2: Fix the Configuration Files

1. **Edit the Daemon Config:** Open this file:
    
    `sudo vim /etc/snmp/snmpd.conf`
    
2. **Add your configuration there:**
    
    `agentAddress udp:161,udp6:[::1]:161` 
    
    `rocommunity public 192.168.1.0/24` (Adapt this range according to your network)
    
    *(When using a subnet like `192.168.1.0/24`, any device on that network, including OpenNMS, can read it.). You can also replace this range with the IP address of your OpenNMS server*
    

### Step 3: Restart the Service

After saving the file (Ctrl+O, Enter, Ctrl+X), restart the daemon:

`sudo systemctl restart snmpd`

### Step 3: Solve the "Timeout" Issue

If you still get "Timeout," it’s usually one of two things:

- **The Firewall:** Ubuntu’s `ufw` might be blocking port 161. `sudo ufw allow 161/udp`

*Optional: Add other services like HTTP(S), SSH, (S)FTP, depending of your needs.*

- **Binding Issue:** Run `netstat -tulpen | grep 161` to make sure the service is actually listening on `0.0.0.0:161` and not just `127.0.0.1`.

Restart UFW:

`sudo ufw reload`

*(Or start it with `sudo ufw enable` if used for the first time)*

---

### Quick Test

Run the walk again, but try it locally first to ensure the service is healthy:

`snmpwalk -v2c -c public localhost system`

If that works, try it from your OpenNMS machine using the Ubuntu IP.
