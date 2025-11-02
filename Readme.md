# Ubuntu Server Basic Security & GitHub SSH Integration

This document describes the steps taken after the first login to a new Ubuntu server to set up secure SSH authentication, a basic web server configuration, and GitHub access via SSH.

---

## 1. Server access via SSH key (instead of password login)

### 1.1 Check or create the SSH key on the local system, i.e. your Windows host

```bash
ssh-keygen -t ed25519 -C "USER@LOCALHOST"
```

#### 1.1.1 The key is stored by default under, (i.e. under Windows C:\Users\USERNAME\.ssh\)
```bash
~/.ssh/vserver_id_ed25519        (private key)
~/.ssh/vserver_id_ed25519.pub    (public key)
```

### 1.2 Copy the public key to the server
```bash
ssh-copy-id -i ~/.ssh/your_key.pub USER@SERVER-IP-ADDRESS
```

#### 1.2.1 Example
```bash
ssh-copy-id -i ~/.ssh/vserver_ed25519.pub firstname-lastname@12.34.56.789
```

### 1.3 Test login
```bash
ssh -i ~/.ssh/vserver_ed25519 USER@SERVER-IP-ADDRESS
```

### 1.4 Deactivate password login on the server, to do this open the file containing the sshd configuration
```bash
sudo nano /etc/ssh/sshd_config
```

#### 1.4.1 Please make sure that following values are set
```bash
PasswordAuthentication no
PubkeyAuthentication yes
PermitRootLogin no
```

#### 1.4.2 Restart ssh service
```bash
sudo systemctl restart ssh
```

---

## 2. Nginx installation and basic configuration

### 2.1 Installation
```bash
sudo apt update
sudo apt install nginx -y
```



```bash

```
