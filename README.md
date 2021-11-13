# Ansible Playbooks

> Automated Mac setup and configuration with Ansible

These playbooks install and configure most of the Mac software I use for software development.

## Installation

1. Ensure Apple's command line tools are installed (`xcode-select --install` to launch the installer).
2. [Ensure `pipx` is available](https://pipx.pypa.io/stable/installation/)

   ```sh
   brew install pipx python-setuptools
   pipx ensurepath
   ```

3. [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-and-upgrading-ansible-with-pipx):

   ```sh
   pipx install ansible-core
   pipx install ansible-lint yamllint
   ```

4. Download this repository to your mac.
5. Run ansible-galaxy to install required Ansible roles.

   ```sh
   ansible-galaxy install -r requirements.yml
   ```

6. Run ansible-playbook to execute a playbook.

   ```sh
   ansible-playbook playbook.yml --ask-vault-pass --ask-become-pass
   ```

> Note: If some Homebrew commands fail, you might need to agree to Xcode's license or fix some other Brew issue. Run `brew doctor` to see if this is the case.

## Usage

### Execute full playbook

```sh
ansible-playbook playbook.yml --ask-vault-pass --ask-become-pass
```

### Update machine using playbook tags

```sh
ansible-playbook playbook.yml -t up
```

## System settings

### How to find the domain & key responsible for a setting

```sh
mkdir -p .diff
defaults read > .diff/before
defaults read > .diff/after
code --diff .diff/before .diff/after
```

[See pawelgrzybek blog post](https://pawelgrzybek.com/change-macos-user-preferences-via-command-line/)
