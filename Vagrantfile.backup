# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Define a common base box
  config.vm.box = "ubuntu/focal64"
  config.vm.box_check_update = false
  
  # Disable default shared folder (we'll use Ansible instead)
  config.vm.synced_folder ".", "/vagrant", disabled: true
  
  # Configure plugin for VirtualBox Guest Additions
  config.vbguest.auto_update = false
  
  # Web Server VM
  config.vm.define "web01" do |web|
    web.vm.hostname = "web01"
    web.vm.network "private_network", ip: "192.168.56.10"
    web.vm.provider "virtualbox" do |vb|
      vb.name = "web01"
      vb.memory = "1024"
      vb.cpus = 1
    end
    # Ensure Python is installed for Ansible
    web.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y python3 python3-apt
    SHELL
  end
  
  # Database Server VM
  config.vm.define "db01" do |db|
    db.vm.hostname = "db01"
    db.vm.network "private_network", ip: "192.168.56.11"
    db.vm.provider "virtualbox" do |vb|
      vb.name = "db01"
      vb.memory = "1024"
      vb.cpus = 1
    end
    # Ensure Python is installed for Ansible
    db.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y python3 python3-apt
    SHELL
  end
end
