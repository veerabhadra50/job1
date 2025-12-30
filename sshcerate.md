# ===== CREATE SSH KEY (ED25519) =====
ssh-keygen -t ed25519 -C "name"

# ===== CREATE SSH KEY (RSA - OPTIONAL) =====
ssh-keygen -t rsa -b 4096 -C "name"

# ===== CREATE SSH KEY WITH CUSTOM NAME =====
ssh-keygen -t ed25519 -f ~/.ssh/appu -C "name"

# ===== LIST SSH KEYS =====
ls ~/.ssh

# ===== VIEW PUBLIC KEY =====
cat ~/.ssh/appu.pub

# ===== ON SERVER: CREATE SSH DIRECTORY =====
mkdir -p ~/.ssh

# ===== ADD PUBLIC KEY =====
nano ~/.ssh/authorized_keys

# ===== SET SSH PERMISSIONS =====
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys

# ===== LOGIN USING SSH =====
ssh username@server_ip

# ===== SWITCH USER =====
su - username
