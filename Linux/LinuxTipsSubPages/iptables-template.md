```
*filter

# Default policies: Drop all incoming, allow outgoing and forwarding
:INPUT DROP [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]

# Allow all traffic on the loopback interface
-A INPUT -i lo -j ACCEPT

# Allow established and related connections
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Drop invalid packets
-A INPUT -m state --state INVALID -j DROP

# Drop fragmented packets
-A INPUT -f -j DROP

# Drop XMAS, NULL, and other malformed packets
-A INPUT -p tcp --tcp-flags ALL ALL -j DROP
-A INPUT -p tcp --tcp-flags ALL NONE -j DROP

# Drop spoofed packets (private, reserved, multicast, etc.)
-A INPUT -s 10.0.0.0/8 -j DROP
-A INPUT -s 172.16.0.0/12 -j DROP
-A INPUT -s 192.168.0.0/16 -j DROP
-A INPUT -s 169.254.0.0/16 -j DROP
-A INPUT -s 127.0.0.0/8 ! -i lo -j DROP
-A INPUT -s 224.0.0.0/4 -j DROP
-A INPUT -d 224.0.0.0/4 -j DROP
-A INPUT -s 240.0.0.0/5 -j DROP
-A INPUT -d 240.0.0.0/5 -j DROP
-A INPUT -s 0.0.0.0/8 -j DROP
-A INPUT -d 0.0.0.0/8 -j DROP
-A INPUT -d 239.255.255.0/24 -j DROP
-A INPUT -d 255.255.255.255 -j DROP

# ICMP: Block certain types, rate-limit the rest
-A INPUT -p icmp --icmp-type address-mask-request -j DROP
-A INPUT -p icmp --icmp-type timestamp-request -j DROP
-A INPUT -p icmp --icmp-type router-solicitation -j DROP
-A INPUT -p icmp -m limit --limit 2/second -j ACCEPT

# Allow SSH (change port 22 if you use a custom port)
-A INPUT -p tcp --dport 22 -m state --state NEW -j ACCEPT

# Allow HTTP/HTTPS (optional, remove if not serving web traffic)
# -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT
# -A INPUT -p tcp --dport 443 -m state --state NEW -j ACCEPT

# Block dangerous ports (examples: Telnet, SMTP, RPC, NetBIOS, etc.)
-A INPUT -p tcp --dport 23 -j DROP    # Telnet
-A INPUT -p tcp --dport 25 -j DROP    # SMTP
-A INPUT -p tcp --dport 135 -j DROP   # MS RPC
-A INPUT -p tcp --dport 139 -j DROP   # NetBIOS
-A INPUT -p tcp --dport 445 -j DROP   # SMB
-A INPUT -p tcp --dport 1433 -j DROP  # MS SQL
-A INPUT -p tcp --dport 3306 -j DROP  # MySQL (unless needed)
-A INPUT -p tcp --dport 3389 -j DROP  # RDP

# SYN flood protection (rate-limit new TCP connections)
-A INPUT -p tcp --syn -m limit --limit 50/second --limit-burst 50 -j ACCEPT
-A INPUT -p tcp --syn -j DROP

COMMIT

```
