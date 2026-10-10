# Self-Hosting

## Installation

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

Setup SSH Agent key auto add

```bash
echo "AddKeysToAgent yes" > ~/.ssh/config
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
- 5: Login with a web browser

```bash
gh auth login
```

Clone repository

```bash
git clone git@github.com:spencerdennison/services.git
```

Change into Ansible directory

```bash
cd services/ansible
```

Run Ansible playbooks

```bash
ansible-playbook local.yml --ask-become-pass --ask-vault-pass
```

Was using ansible-pull but --ask-vault-pass wouldn't prompt?
