# Ubuntu Ansible Setup

Ansible playbooks for configuring Ubuntu workstations and GPU servers.

## Structure

```
.
├── ansible.cfg          # Ansible configuration
├── inventory.yml        # Host inventory
├── group_vars/
│   └── all.yml          # Shared variables
├── workstation.yml      # Workstation setup playbook
└── gpu-servers.yml      # GPU server setup playbook
```

## Workstation Packages

**APT:** fish, htop, btop, neovim, git, curl, jq, ripgrep, tree, just, podman, openssh-server

**Snap:** VS Code, Firefox

**External tools:** uv, kind, k9s, nvm, fisher, Claude CLI

## Usage

### Local workstation setup
```bash
ansible-playbook workstation.yml --ask-become-pass
```

### GPU servers setup
```bash
# First, add your servers to inventory.yml, then:
ansible-playbook gpu-servers.yml --ask-become-pass
```

### Run specific tasks with tags (if added)
```bash
ansible-playbook workstation.yml --tags "packages" --ask-become-pass
```

## Customization

Edit `group_vars/all.yml` to:
- Change username
- Add/remove apt packages
- Add/remove snap packages
- Toggle installation of external tools
# ubuntu-ansible
