# Provision Ubuntu on WSL2

Automating provisioning Ubuntu with Ansible on WSL 2

Uses ansible in a WSL 2 Ubuntu instance to provision locally.

Intended to be re-runnable (idempotent) to maintain and update when required.

## Getting Started

### Prerequisites

1. Windows 10 or 11.
1. WSL 2

### Update the package lists and install Ansible

1. `sudo apt update && sudo apt install -y ansible`

### Clone and Run
2. `git clone https://github.com/worldofgeese/provision-ubuntu-on-wsl2.git`
3. `cd provision-ubuntu-on-wsl2`
4. `ansible-galaxy install -r requirements.yml --force`
5. `ansible-playbook playbook.yml -i inventory --ask-become-pass -e '{"nix_flakes": true}'`
6. `exit` then open a new shell to make Nix available to your environment
7. Profit :smile:

## What is Installed?

- See the [playbook.yml](playbook.yml) task: `Install apt cmd line apps` for apt packages
- [aws vault](tasks/aws-vault.yml)

## Notes

|Description           | Command                                                                       |
|--------------------- | ----------------------------------------------------------------------------- |
|Find all local info   | `ansible localhost -m setup`                                                  |

See [vars.yml](vars.yml) to configure which tasks get run.

## References

- [Jeff Geerling's Ansible for Devops](https://leanpub.com/ansible-for-devops/c/J2V7E1SOETu3)
