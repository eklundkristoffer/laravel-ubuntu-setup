```bash
sudo apt install mysql-server -y
sudo systemctl start mysql.service

sudo myslq

# Set a strong password to root
> mysql ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
> mysql exit

# Secure mysql
sudo mysql_secure_installation
# Check password strength: no
# Change password: no
# Remove anonymous users: yes
# Disallow root login remotely: yes
# Remove test database and access to it: yes
# Reload privilege tables now: yes

# Create new mysql user
mysql -u root -p

# Create database
> mysql CREATE DATABASE IF NOT EXIST 'databasename';

# Set username & password
> mysql CREATE USER 'myuser'@'localhost' IDENTIFIED BY 'password';

# Grant user access to database
#
# This allows myuser full access to the database
# see in attached link below how to add specific permissions.
> mysql GRANT ALL PRIVILEGES ON databasename.* TO 'myuser'@'localhost';

> mysql FLUSH PRIVILEGES;
> mysql exit
```

[Credits](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-22-04)
