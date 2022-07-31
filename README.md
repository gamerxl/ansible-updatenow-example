# ansible-updatenow-example
An ansible playbook example to update the packages of a bunch of servers with different distributions at once combined with a SSH ProxyJump to jump over a hypervisor.

## Requirements
- Ansible
- Recommended: A running SSH-Agent on the machine where you run the ansible playbook.

## Good to know
It provides an ansible playbook which features package update of a bunch of servers with different distributions at once (see [Supported distributions for package update](#supported-distributions-for-package-update)). It utilizes a SSH ProxyJump to jump over a hypervisor ssh server to connect to the servers listed in the `./inventory.yaml`.

It is recommended to run a SSH-Agent on the machine where you run the Ansible Playbook. Next you should create a secure SSH-Key for your Ansible Operations and add the private key to your SSH-Agent. The public key of the just created SSH-Key has to be added to the `~/.ssh/authorized_keys` of your servers listed in the `./inventory.yaml` of this repository.

It is recommended to have an ansible user named `ansible` on the machines where you run ansible. That includes the hypervisor and the servers listed in the `./inventory.yaml`. The public key of the created SSH-Key from above should be added to the recommended ansible user on the hypervisor and the servers listed in the `./inventory.yaml`. The private key of the SSH-Key should only be added to the machine where you will be run the ansible playbook and must not added to the hypervisor or servers listed in the `./inventory.yaml` etc..

### Supported distributions for package update
* Ubuntu
* Alpine Linux

## How to run the ansible playbook
```bash
ansible-playbook -i inventory.yaml --ask-become-pass playbook.yaml
```
