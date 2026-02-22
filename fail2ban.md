```bash
sudo apt install fail2ban -y
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local

sudo systemctl enable fail2ban
sudo systemctl start fail2ban
sudo systemctl status fail2ban
```

### Optional, update fail2ban defaults
Change under `[DEFAULT]`

```bash
sudo vim /etc/fail2ban/jail.local
```

```
bantime = 3600
findtime = 600
maxretry = 3
```
