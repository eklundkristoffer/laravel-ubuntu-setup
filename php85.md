```bash
sudo LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php -y
sudo LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/nginx -y
sudo apt update

sudo apt install php8.5-cli -y

sudo apt install php8.5-common php8.5-{bcmath,bz2,curl,gd,gmp,intl,mbstring,readline,xml,zip} -y

# php-fpm
sudo apt install php8.5-fpm
sudo systemctl status php8.5-fpm
```

[Credits](https://php.watch/articles/php-8-5-installation-upgrade-guide-debian-ubuntu)
