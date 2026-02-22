```bash
sudo fallocate -l 1G /swapfile

# Verify swapfile
ls -lh /swapfile

sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile

# Verify swapfile is active
sudo swapon --show
free -h

# Make swapfile permanent
sudo cp /etc/fstab /etc/fstab.bak
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```

[Credits](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04)
