#
# Vagrantfile
#

Vagrant.configure('2') do |config|

  config.vm.define 'test-node' do |instance|

    # Make sure to download as 'ubuntu-13.10'
    # vagrant box add
    # http://cloud-images.ubuntu.com/vagrant/saucy/current/saucy-server-cloudimg-amd64-vagrant-disk1.box

    instance.vm.provider "virtualbox" do |vb|
      vb.customize ['modifyvm', :id, '--memory', 1024]
    end

    instance.vm.box = 'ubuntu-13.10'
    instance.vm.host_name = 'test-playbooks-node'
    instance.vm.network 'private_network', ip: '172.16.1.10'

    instance.vm.provision 'ansible' do |prov|
      prov.inventory_path = 'inventory.yml'
      prov.playbook = 'test-playbooks.yml'
    end # prov
  end # instance

end # config
