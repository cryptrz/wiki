# From localhost to external

[https://www.youtube.com/watch?v=Tq7q_pttrDw](https://www.youtube.com/watch?v=Tq7q_pttrDw)

- `sudo apt install postfix bsd-mailx`
    - *internet site*
    - *<mail server name>*

- `sudo systemctl enable postfix`
- `sudo systemctl start postfix`

- `sudo cp /etc/postfix/main.cf /etc/postfix/main.cf.old`
- `sudo vim /etc/postfix/main.cf`
    
     → `inet_interfaces=loopback-only`
    

- `sudo ufw allow Postfix`
- `sudo ufw allow "Postfix SMTPS"`
- `sudo ufw allow "Postfix Submission"`

(Eventually test `telnet [localhost](http://localhost) 25` to confirm)

- `mailx email@address.com`