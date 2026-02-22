```bash
# Disable apache2 if it is installed
sudo update-rc.d apache2 disable
sudo systemctl disable apache2

# Install nginx
sudo apt install nginx -y
sudo systemctl enable nginx
sudo systemctl start nginx
```
