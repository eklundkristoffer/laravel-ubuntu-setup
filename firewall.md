> [!NOTE]  
> This is for when you are not configuring firewall through your server provider like AWS / GCP.

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing

# Allow SSH
sudo ufw allow ssh

# Allow HTTP and HTTPS
sudo ufw allow 'Nginx Full'

# Enable firewall
sudo ufw enable

# Check status
sudo ufw status verbose
```
