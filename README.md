# Self-Hosting

## Dependencies

- Cloudflare domain not publicly accessible wildcard record using server IP
- Do not specify root password during Debian install to ensure sudo installation
- SSH server + standard system utilities

Update and upgrade apt package repository

```bash
sudo apt update && sudo apt upgrade
```

Install Ansible, Git, and GitHub packages

```bash
sudo apt install ansible git gh
```

Generate Git SSH-Key

```bash
ssh-keygen -t ed25519 -f ~/.ssh/git
```

Add SSH-Key to SSH Agent

```bash
eval $(ssh-agent)
ssh-add ~/.ssh/git
```

Add Git SSH-Key to GitHub (Secondary device required)

- 1: GitHub.com
- 2: SSH
- 3: ~/.ssh/git.pub
- 4: services
- 5: Login with a web browser (Wait, it will prompt for secondary device login)

```bash
gh auth login
```

Run Ansible Pull

```bash
ansible-pull -U git@github.com:spencerdennison/self-hosting.git -f ansible/local.yml --ask-become-pass
```
