# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = 'precise64'
  config.vm.box_url = 'http://files.vagrantup.com/precise64.box'

  if Vagrant.has_plugin?("vagrant-vbguest")
    config.vbguest.auto_update = false
    config.vbguest.no_remote = true
  end

  config.vm.define :ha1 do |node|
    node.vm.hostname = "ha1"
    node.vm.network :private_network, ip: "192.168.10.50"
    node.vm.provision "puppet" do |puppet|
      puppet.module_path = "modules"
      puppet.manifest_file = "ha_master.pp"
    end
  end

  config.vm.define :ha2 do |node|
    node.vm.hostname = "ha2"
    node.vm.network :private_network, ip: "192.168.10.51"
    node.vm.provision "puppet" do |puppet|
      puppet.module_path = "modules"
      puppet.manifest_file = "ha_slave.pp"
    end
  end

end
