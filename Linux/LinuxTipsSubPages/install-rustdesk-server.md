# RustDesk technical guide

1. Connect the server
2. ```sudo apt update && sudo apt install docker.io docker-compose -y && sudo systemctl start docker```
3. Copy the code in the first example for making the compose.yml file on this page: https://rustdesk.com/docs/en/self-host/rustdesk-server-oss/docker/
4.  ```sudo mkdir /opt/rustdesk && cd /opt/rustdesk && sudo vim compose.yml``` 
5.  Paste the code and save
6. ```sudo docker-compose up -d```
7. ```cd data && cat *.pub``` (Copy it for client's network settings)