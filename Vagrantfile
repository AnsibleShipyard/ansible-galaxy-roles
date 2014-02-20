#
# Vagrantfile
# ===========
# - Make sure you have `vagrant` installed.
# - Run the following two commands:
#     - vagrant box add 'opscode-ubuntu-13.10' http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_ubuntu-13.10_chef-provisionerless.box
#     - vagrant box add 'opscode-centos-6.5' http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-6.5_chef-provisionerless.box
# - Run `vagrant up ubuntu1310`, `vagrant up centos65`
# - Or `vagrant up` which will spin all boxes defined here
#

test_name = 'ansible_roles'
# default_inventory = 'inventory.yml'
# default_playbook = 'playbook.yml'

nodes = [
  { :hostname => "ubuntu1310", :mem => 512, :cpus => 2,
    :ip => '172.16.1.10',
    :box => 'opscode-ubuntu-13.10',
    # :inv => default_inventory,
    # :playbook => default_playbook
  },

  { :hostname => "centos6510", :mem => 512, :cpus => 2,
    :ip => '172.16.1.11',
    :box => 'opscode-centos-6.5',
    # :inv => default_inventory,
    # :playbook => default_playbook
  },
]

Vagrant.configure('2') do |config|
  nodes.each do |node|
    config.vm.provider "virtualbox" do |vb|
      vb.customize ['modifyvm', :id, '--memory', node[:mem]]

      # Speedups!
      vb.customize ['modifyvm', :id, '--cpus', node[:cpus]]
      vb.customize ['modifyvm', :id, '--hwvirtex', 'on']
    end

    config.omnibus.chef_version = :latest
    config.vm.define node[:hostname] do |instance|
      instance.vm.box = node[:box]
      instance.vm.host_name = node[:hostname]# + '.' + domain
      instance.vm.network 'private_network', ip: node[:ip]

      # instance.vm.provision 'ansible' do |prov|
      #   prov.inventory_path = node[:inv]
      #   prov.playbook = node[:playbook]
      # end # prov

    end # end define
  end # end nodes
end # config

