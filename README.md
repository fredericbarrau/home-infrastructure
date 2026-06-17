# Home Infrastructure

Ansible project for managing my own stuffs (raspberry pi, NAS server, etc.).

This project is rather straighforward, and follows the pattern described in Ansible's documentation.

## Requirements

- Ansible
- Python 3

## How ?

```bash
# Get the required external collections
ansible-galaxy collection install -r requirements.yml
# Run 
ANSIBLE_CONFIG=./ansible.cfg ansible-playbook -i hosts site.yml
```
