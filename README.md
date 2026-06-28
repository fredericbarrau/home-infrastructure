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


## Appendix

### Make WSL reachable from LAN

[See here](https://hy2k.dev/en/blog/2025/10-31-wsl2-mirrored-networking-dev-server/).

### CA stuffs

#### Manual host bootstrap for CA

- Install [step-cli](https://smallstep.com/docs/step-cli/installation/)
- Bootstrap your environment:

```bash
step ca bootstrap --ca-url https://pki.barrau.bzh --fingerprint b653f61258ffe0b3c646eb338272883ff5b8374ca09a8a49f55c4df6f02adfba
```

#### Generate a certificate using the CA

When orchestration is not feasible (or hardly) with ansible (chicken & egg problem).

Can be done from any bootstrapped node/user:


*Example*

```bash
sudo -i
# Using the self host method: step-cli will open a local 80 daemon during the validation challenge
step-cli ca certificate pi.hole tls.crt tls.pem --contact frederic.barrau@gmail.com --not-after 1h --provisioner ACME --san pihole.barrau.bzh
```