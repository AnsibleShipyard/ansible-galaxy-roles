ansible-galaxy-roles
====================

__Deprecated__

We've worked hard to make each role well documented with functional tests
that run in travis and Docker. Please see each repository for information.

Here is a good [example](https://github.com/AnsibleShipyard/ansible-nginx).


# Old Info

This repo is the main repo I use to test and upload my
ansible roles.

## Just cloned?

    git submodule update --init

## Need to update submodules?

    git submodule foreach git pull

## Test Driving the roles
Install Vagrant.

Add ubuntu 13.10 box:

    vagrant box add ubuntu-13.10 http://cloud-images.ubuntu.com/vagrant/precise/current/precise-server-cloudimg-amd64-vagrant-disk1.box

Run `vagrant up` given the supplied `Vagrantfile`.

If for whatever reason you need to re-provision run the ansible command below or run:

    vagrant provision

Restart from fresh again:

    vagrant destroy --force && vagrant up

## Ansible Command
If you're interested in knowing what command would initiate an ansible provision:

    ansible-playbook playbook.yml

## Testing
Want to test the nodejs playbook?

    ansible-playbook playbook.yml --tags nodejs

## Having Problems?

1. Ansible cannot ssh, as it reports security key issues.
  - Remove the entry for `172.16.1.10` in `~/.ssh/known_hosts` file
1. Create an github issue
