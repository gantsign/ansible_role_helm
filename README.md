Ansible Role: Helm
==================

[![Tests](https://github.com/gantsign/ansible_role_helm/workflows/Tests/badge.svg)](https://github.com/gantsign/ansible_role_helm/actions?query=workflow%3ATests)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-gantsign.helm-blue.svg)](https://galaxy.ansible.com/gantsign/helm)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/gantsign/ansible_role_helm/master/LICENSE)

Role to download and install [Helm](https://helm.sh) the package manager for
Kubernetes.

Requirements
------------

* Ansible Core >= 2.12

* Linux Distribution

    * Debian Family

        * Debian

            * Buster (10)
            * Bullseye (11)

        * Ubuntu

            * Bionic (18.04)
            * Focal (20.04)

    * RedHat Family

        * Rocky Linux

            * 8

        * Fedora

            * 35

    * SUSE Family

        * openSUSE

            * 15.3

    * Note: other versions are likely to work but have not been tested.

Role Variables
--------------

The following variables will change the behavior of this role (default values
are shown below):

```yaml
# Helm version number
helm_version: '3.12.2'

# The CPU architecture of the Helm executable to install
helm_architecture: 'amd64'

# Mirror to download Helm from
helm_mirror: 'https://get.helm.sh'

# Dir where Helm should be installed
helm_install_dir: '/usr/local/share/helm'

# Directory to store files downloaded for Helm
helm_download_dir: "{{ x_ansible_download_dir | default(ansible_env.HOME + '/.ansible/tmp/downloads') }}"
```

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
    - role: gantsign.helm
```

Tab Completion for Zsh
----------------------

### Using Ansible

We recommend using the
[gantsign.antigen](https://galaxy.ansible.com/gantsign/antigen) role to enable
tab completion for Helm (this must be configured for each user).

```yaml
- hosts: servers
  roles:
    - role: gantsign.helm

    - role: gantsign.antigen
      users:
        - username: example
          antigen_libraries:
            - name: oh-my-zsh
          antigen_bundles:
            # Oh My Zsh Helm plugin
            - name: helm
```

### Using Antigen

If you prefer to use [Antigen](https://github.com/zsh-users/antigen) directly
add the following to your Antigen configuration:

```bash
antigen use oh-my-zsh
antigen bundle helm
```

### Manual configuration

To manually configure Zsh add the following to your `.zshrc`:

```bash
eval "$(helm completion zsh)"
```

More Roles From GantSign
------------------------

You can find more roles from GantSign on
[Ansible Galaxy](https://galaxy.ansible.com/gantsign).

Development & Testing
---------------------

This project uses the following tooling:
* [Molecule](http://molecule.readthedocs.io/) for orchestrating test scenarios
* [Testinfra](http://testinfra.readthedocs.io/) for testing the changes on the
  remote
* [pytest](http://docs.pytest.org/) the testing framework
* [Tox](https://tox.wiki/en/latest/) manages Python virtual
  environments for linting and testing
* [pip-tools](https://github.com/jazzband/pip-tools) for managing dependencies

A Visual Studio Code
[Dev Container](https://code.visualstudio.com/docs/devcontainers/containers) is
provided for developing and testing this role.

License
-------

MIT

Author Information
------------------

John Freeman

GantSign Ltd.
Company No. 06109112 (registered in England)
