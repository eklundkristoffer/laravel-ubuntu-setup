```bash
sudo chown -R $USER:www-data /var/www
sudo chmod -R 775 /var/www
sudo usermod -a -G www-data $USER

cd /var/www
git clone git@myapp:owner/repo.git myapp.com

cd /var/www/myapp.com
sudo find . -type f -exec chmod 644 {} \;    
sudo find . -type d -exec chmod 755 {} \;

sudo chgrp -R www-data storage bootstrap/cache
sudo chmod -R ug+rwx storage bootstrap/cache
```

### Add Nginx config

```bash
sudo vim /etc/nginx/sites-available/myapp
```

Add:
```
server {
    listen 80;
    server_name myapp.com www.myapp.com;
    root /var/www/myapp/public;

    add_header X-Frame-Options "SAMEORIGIN";
    add_header X-Content-Type-Options "nosniff";

    index index.php;
    charset utf-8;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }
    location = /favicon.ico { access_log off; log_not_found off; }
    location = /robots.txt  { access_log off; log_not_found off; }

    error_page 404 /index.php;
    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php8.5-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        include fastcgi_params;
        fastcgi_hide_header X-Powered-By;
    }

    location ~ /\.(?!well-known).* {
        deny all;
    }
}
```

Enable new site:
```
sudo ln -s /etc/nginx/sites-available/myapp /etc/nginx/sites-enabled/
sudo rm /etc/nginx/sites-enabled/default
sudo nginx -t
sudo systemctl restart nginx
```
