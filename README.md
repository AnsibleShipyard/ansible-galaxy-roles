ansible-galaxy-roles
====================

This repo is the main repo I use to test and upload my
ansible roles.

## Test Driving the roles
1. Install Vagrant.
1. Add ubuntu 13.10 box:

    vagrant box add ubuntu-13.10 http://cloud-images.ubuntu.com/vagrant/precise/current/precise-server-cloudimg-amd64-vagrant-disk1.box

1. Run `vagrant up` given the supplied `Vagrantfile`.
1. If for whatever reason you need to re-provision run the ansible command below or run:

    vagrant provision

1. Restart from fresh again:

    vagrant destroy --force && vagrant up

## Ansible Command
If your interested in knowing what command would initiate an ansible provision:

    ansible-playbook -i inventory.yml --private-key=~/.vagrant.d/insecure_private_key -u vagrant test-playbooks.yml

## Having Problems?

1. Ansible cannot ssh, as it reports security key issues.
  - Remove the entry for `172.16.1.10` in `~/.ssh/known_hosts` file
1. Create an github issue

