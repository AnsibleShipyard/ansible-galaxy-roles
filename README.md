ansible-galaxy-roles
====================

This repo is the main repo I use to test and upload my
ansible roles.

## Manual Testing

1. Install Vagrant.
1. Run `vagrant up` given the supplied `Vagrantfile`.
1. Create an inventory file `inventory.yml` reflecting the vagrant vm.
1. run the following command:

    ansible-playbook -i inventory.yml --private-key=~/.vagrant.d/insecure_private_key -u vagrant test-playbooks.yml

## Automated

1. TBD - Run <task>
