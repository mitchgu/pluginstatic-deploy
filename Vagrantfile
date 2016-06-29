# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # Online documentation at https://docs.vagrantup.com.can
  # Search for boxes at https://atlas.hashicorp.com/search.

  config.vm.box = "ubuntu/xenial64"

  config.vm.define "pluginstatic", primary: true do |instance|
    instance.vm.network "forwarded_port", guest: 80, host: 2016
    config.vm.provider "virtualbox" do |vb|
      vb.name = "pluginstatic"
    end
  end

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 512
    vb.cpus = 1
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    ansible.extra_vars = {
      vm: true,
      hostname: "pluginstatic"
    }
    ansible.tags = "nginx"
  end

end
