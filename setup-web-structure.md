```bash
sudo vim /usr/local/bin/laravel-permissions
```

Add:
```bash
#!/bin/bash
if [ $# -eq 0 ]; then
    echo "Usage: laravel-permissions /path/to/laravel/app"
    exit 1
fi

APP_PATH=$1

# Set ownership
sudo chown -R $USER:www-data $APP_PATH

# Set directory permissions
sudo find $APP_PATH -type d -exec chmod 755 {} \;

# Set file permissions
sudo find $APP_PATH -type f -exec chmod 644 {} \;

# Set specific Laravel permissions
sudo chmod -R 775 $APP_PATH/storage
sudo chmod -R 775 $APP_PATH/bootstrap/cache

# Set .env permissions
if [ -f "$APP_PATH/.env" ]; then
    sudo chmod 600 $APP_PATH/.env
fi
echo "Permissions set for $APP_PATH"
```

Make it executable:
```bash
sudo chmod +x /usr/local/bin/laravel-permissions
```
