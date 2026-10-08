# Self-Hosting

## Dependencies

- Cloudflare domain not publicly accessible wildcard record using server IP
- Do not specify root password during Debian install to ensure sudo installation
- SSH server + standard system utilities

Update and upgrade apt package repository

```bash
sudo apt update && sudo apt upgrade
```

Install Ansible and Git packages

```bash
sudo apt install ansible git
```
