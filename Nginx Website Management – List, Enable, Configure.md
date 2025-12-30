# ==============================
# 1. LIST ALL ENABLED WEBSITES
# ==============================
# Shows active (enabled) Nginx site configs
ls /etc/nginx/sites-enabled/


# ==============================
# 2. LIST ALL AVAILABLE WEBSITES
# ==============================
# Shows all site configs (enabled + disabled)
ls /etc/nginx/sites-available/


# ==============================
# 3. CHECK NGINX CONFIG & SERVER NAMES
# ==============================
# Validates config and shows configured domains
sudo nginx -T | grep server_name


# ==============================
# 4. ENABLE A WEBSITE (CREATE SYMLINK)
# ==============================
# Links site config from available → enabled
sudo ln -s /etc/nginx/sites-available/website \
           /etc/nginx/sites-enabled/


# ==============================
# 5. DISABLE A WEBSITE
# ==============================
# Removes symlink (does not delete config)
sudo rm /etc/nginx/sites-enabled/website


# ==============================
# 6. EDIT WEBSITE CONFIG
# ==============================
# Modify domain, port, proxy, root, etc.
sudo nano /etc/nginx/sites-available/website


# ==============================
# 7. TEST NGINX CONFIG
# ==============================
# Must be successful before reload
sudo nginx -t


# ==============================
# 8. RELOAD NGINX
# ==============================
# Applies config without downtime
sudo systemctl reload nginx


# ==============================
# 9. RESTART NGINX (IF REQUIRED)
# ==============================
sudo systemctl restart nginx


# ==============================
# 10. CHECK NGINX STATUS
# ==============================
sudo systemctl status nginx


# ==============================
# 11. ENABLE HTTP (PORT 80)
# ==============================
# Default Nginx listens on port 80
# Ensure firewall allows it
sudo ufw allow 80


# ==============================
# 12. INSTALL CERTBOT (SSL)
# ==============================
sudo apt install certbot python3-certbot-nginx -y


# ==============================
# 13. ENABLE HTTPS (SSL)
# ==============================
# Automatically configures HTTPS
sudo certbot --nginx -d example.com -d www.example.com


# ==============================
# 14. AUTO-RENEW SSL
# ==============================
sudo certbot renew --dry-run
