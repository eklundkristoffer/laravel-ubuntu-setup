```bash
sudo apt install certbot python3-certbot-nginx -y

sudo certbot --nginx -d myapp.com -d www.myapp.com

# Turn on automatic renewal
sudo certbot renew --dry-run
```
