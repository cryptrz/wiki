OpenVAS (Open Vulnerability Assessment System) is an open-source vulnerability scanner and management tool used to identify security weaknesses in networks, systems, and applications. It is part of the Greenbone Vulnerability Management suite and provides regular updates to its extensive database of vulnerability tests, helping organizations proactively detect and address security risks

# OpenVAS install

1. ```sudo apt update && sudo apt install docker.io && sudo systemctl start docker```
2. ```sudo docker run -d -p 9392:443 --name openvas mikesplain/openvas``` 
3. ```sudo vim /etc/hosts``` and add ```127.0.0.1 hostname-of-your-choice```
4. Web browser: https://hostname-of-your-choice:9392
5. Default credentials: admin:admin

### Troubleshooting
If port 9392 is not accessible: ```ufw allow 9392```

Another possibility: In step 2 replace ```-p 9392:443``` with ```-p 443:443``` and  remove ```:9392``` in the URL