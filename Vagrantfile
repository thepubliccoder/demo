# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.ssh.private_key_path= "../keys/vagrant"
  # Common to all VMs
  config.vm.box = "ubuntu-16.04.1-desktop-amd64"
  config.vm.boot_timeout = 60
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.synced_folder "data/", "/data"

  config.vm.provision :ansible do |ansible|
    ansible.verbose = "vv"
    ansible.playbook = "ansible/vagrant-vm-playbook.yml"
  end

  # First Ubuntu desktop
  config.vm.define "pc-192.168.200.100" do |node|
    node.vm.hostname = "pc-192-168-200-100"
    node.vm.network "private_network", ip: "192.168.200.100", virtualbox__intnet: "net1", auto_config: false
    node.vm.provider "virtualbox" do |vb|
      vb.name = "pc-192.168.200.100"
      vb.customize ["modifyvm", :id, "--vrde", "off"]
      vb.customize ["modifyvm", :id, "--vram", "128"]
      vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
    end
  end

  # Second Ubuntu desktop
  config.vm.define "pc-192.168.200.101" do |node|
    node.vm.hostname = "pc-192-168-200-101"
    node.vm.network "private_network", ip: "192.168.200.101", virtualbox__intnet: "net1", auto_config: false
    node.vm.provider "virtualbox" do |vb|
      vb.name = "pc-192.168.200.101"
      vb.customize ["modifyvm", :id, "--vrde", "off"]
      vb.customize ["modifyvm", :id, "--vram", "128"]
      vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
    end
  end

  # Kali2
  config.vm.define "Kali2" do |node|
    node.vm.hostname = "Kali2"
    node.vm.box = "Kali-Linux-2016.2-vbox-amd64"
    node.vm.network "private_network", ip: "192.168.200.200", virtualbox__intnet: "net1", auto_config: false
    node.vm.provider "virtualbox" do |vb|
      vb.name = "Kali2"
      vb.memory = 2048
      vb.cpus = 2
      vb.customize ["modifyvm", :id, "--vrde", "off"]
      vb.customize ["modifyvm", :id, "--vram", "128"]
      vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
    end
  end

  # SecurityOnion
  config.vm.define "SecurityOnion" do |node|
    node.vm.hostname = "SecurityOnion"
    node.vm.box = "ubuntu-14.04.5-desktop-amd64"
    node.vm.network "private_network", ip: "192.168.200.253", virtualbox__intnet: "net1", auto_config: false
    node.vm.provider "virtualbox" do |vb|
      vb.name = "SecurityOnion"
      vb.memory = 2048
      vb.cpus = 2
      vb.customize ["modifyvm", :id, "--vrde", "off"]
      vb.customize ["modifyvm", :id, "--vram", "128"]
      vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
      vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
    end
  end
end
