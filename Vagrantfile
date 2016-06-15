# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.ssh.username = "vagrant"
  config.ssh.forward_agent = true

  config.vm.synced_folder ".", "/home/vagrant/geonames"

  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 12
    vb.memory = 8192
    vb.name = "geonames"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.groups = {
      "geonames" => ['default']
    }
    ansible.playbook = "playbook.yml"
    ansible.host_key_checking = false
    ansible.verbose = "vvvv"
  end
end
