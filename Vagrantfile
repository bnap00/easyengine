# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.synced_folder ".", "/opt/easyengine"
    config.vm.provision "shell", inline: <<-SHELL
      apt-get install -qqy git
      pushd /opt/easyengine > /dev/null
      git checkout fix/phpmyadmin
      /bin/bash install fix/phpmyadmin
      source config/bash_completion.d/ee_auto.rc
      popd > /dev/null
    SHELL

    # Ubuntu 14.04 64 bit
    config.vm.define "trusty64" do |trusty64|
      trusty64.vm.provider "virtualbox" do |v|
          v.memory = 1024
      end
      trusty64.vm.box = "ubuntu/trusty64"
      trusty64.vm.network "forwarded_port", guest: 80, host: 8883
      trusty64.vm.network "forwarded_port", guest: 22222, host: 22222
      trusty64.vm.network "private_network", ip: "192.168.33.14"
      trusty64.ssh.forward_agent = true
    end

    # Ubuntu 14.04 32 bit
    config.vm.define "trusty32" do |trusty32|
      trusty32.vm.provider "virtualbox" do |v|
          v.memory = 1024
      end
      trusty32.vm.box = "ubuntu/trusty32"
      trusty32.vm.network "forwarded_port", guest: 80, host: 8884
      trusty32.vm.network "forwarded_port", guest: 22222, host: 22223
      trusty32.vm.network "private_network", ip: "192.168.33.15"
      trusty32.ssh.forward_agent = true
    end

    #Debian 8 64 bit
    config.vm.define "jessie64" do |jessie64|
      jessie64.vm.provider "virtualbox" do |v|
          v.memory = 1024
      end
      jessie64.vm.box = "debian/jessie64"
      jessie64.ssh.forward_agent = true
      jessie64.vm.network "forwarded_port", guest: 80, host: 8885
      jessie64.vm.network "forwarded_port", guest: 22222, host: 22224
      jessie64.vm.network "private_network", ip: "192.168.35.18"
    end
    #Debian 8 32 bit
    config.vm.define "jessie32" do |jessie32|
      jessie32.vm.provider "virtualbox" do |v|
          v.memory = 1024
      end
      jessie32.vm.box = "boxcutter/debian8-i386"
      jessie32.ssh.forward_agent = true
      jessie32.vm.network "forwarded_port", guest: 80, host: 8886
      jessie32.vm.network "forwarded_port", guest: 22222, host: 22225
      jessie32.vm.network "private_network", ip: "192.168.33.19"
    end

    #Ubuntu 16.04 64 bit
    config.vm.define "xenial64" do |xenial64|
      xenial64.vm.provider "virtualbox" do |v|
          v.memory = 1024
      end
      xenial64.vm.box = "ubuntu/xenial64"
      xenial64.ssh.forward_agent = true
      xenial64.vm.network "forwarded_port", guest: 80, host: 8887
      xenial64.vm.network "forwarded_port", guest: 22222, host: 22226
      xenial64.vm.network "private_network", ip: "192.168.33.20"
    end

    #Ubuntu 16.04 32 bit
    config.vm.define "xenial32" do |xenial32|
      xenial32.vm.provider "virtualbox" do |v|
          v.memory = 1024
      end
      xenial32.vm.box = "ubuntu/xenial32"
      xenial32.ssh.forward_agent = true
      xenial32.vm.network "forwarded_port", guest: 80, host: 8888
      xenial32.vm.network "forwarded_port", guest: 22222, host: 22227
      xenial32.vm.network "private_network", ip: "192.168.33.21"
    end
end