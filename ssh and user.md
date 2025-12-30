# ==============================
# 1. CREATE A NEW USER
# ==============================
# Creates a new Linux user and home directory
adduser username


# ==============================
# 2. GIVE DOCKER ACCESS
# ==============================
# Allows user to run Docker without sudo
usermod -aG docker username


# ==============================
# 3. GIVE SUDO ACCESS
# ==============================
# Allows user to run administrative commands
usermod -aG sudo username


# ==============================
# 4. VERIFY USER GROUPS
# ==============================
# Confirms docker & sudo groups are added
groups username


# ==============================
# 5. CREATE SSH DIRECTORY
# ==============================
# Creates .ssh folder for SSH authentication
mkdir -p /home/username/.ssh


# ==============================
# 6. ADD SSH PUBLIC KEY
# ==============================
# Paste public SSH key here
nano /home/username/.ssh/authorized_keys


# ==============================
# 7. SET SSH PERMISSIONS
# ==============================
# Required secure permissions for SSH to work
chmod 700 /home/username/.ssh
chmod 600 /home/username/.ssh/authorized_keys
chown -R username:username /home/username/.ssh


# ==============================
# 8. GENERATE SSH KEY (LOCAL)
# ==============================
# Creates a secure SSH key pair
ssh-keygen -t ed25519 -C "email@example.com"


# ==============================
# 9. GENERATE SSH KEY (CUSTOM NAME)
# ==============================
# Useful for multiple servers or CI/CD
ssh-keygen -t ed25519 -f ~/.ssh/appu -C "name"


# ==============================
# 10. LIST SSH KEYS
# ==============================
# Shows all SSH keys on local system
ls ~/.ssh


# ==============================
# 11. COPY PUBLIC KEY
# ==============================
# Copy this and paste into authorized_keys
cat ~/.ssh/appu.pub


# ==============================
# 12. LOGIN TO SERVER USING SSH
# ==============================
# Secure login using SSH key
ssh username@server_ip


# ==============================
# 13. SWITCH USER
# ==============================
# Login as another user on server
su - username


# ==============================
# 14. TEST DOCKER ACCESS
# ==============================
# Confirms Docker works without sudo
docker ps


# ==============================
# 15. RESTART SSH SERVICE
# ==============================
# Apply SSH configuration changes
sudo systemctl restart ssh
sudo systemctl status ssh


# ==============================
# 16. DISABLE ROOT LOGIN (OPTIONAL)
# ==============================
# Improves server security
sudo nano /etc/ssh/sshd_config
# Change: PermitRootLogin no
sudo systemctl restart ssh

# 17. list all user on the system
cat /etc/passwd

# 18. list only user name 
cut -d:-f1/etcpasswd


![WhatsApp Image 2025-12-30 at 10 10 05 PM (2)](https://github.com/user-attachments/assets/d434c2c6-2dff-4b35-9707-52adee4c3da9)
