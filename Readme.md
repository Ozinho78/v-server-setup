# Ubuntu Server Basic Security & GitHub SSH Integration

This document describes the steps taken after the first login to a new Ubuntu server to set up secure SSH authentication, a basic web server configuration, and GitHub access via SSH.

---

## 1. Server access via SSH key (instead of password login)

### 1.1 Check or create the SSH key on the local system, i.e. your Windows host

```bash
ssh-keygen -t ed25519 -C "USER@LOCALHOST"
```

#### 1.1.1 The key is stored by default under, i.e. under Windows C:\Users\USERNAME\.ssh\
```bash
~/.ssh/id_ed25519        (private key)
~/.ssh/id_ed25519.pub    (public key)
```

### 1.2 Copy the public key to the server
```bash
ssh-copy-id -i ~/.ssh/your_key.pub USER@SERVER-IP-ADDRESS
```

#### 1.2.1 Example
```bash
ssh-copy-id -i ~/.ssh/vserver_ed25519.pub firstname-lastname@12.34.56.789
```


